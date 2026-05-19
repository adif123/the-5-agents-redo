---
name: gpt-image-gen
description: Use when an agent needs to generate an image via the OpenAI Images API. Handles the curl call, base64 decode, and file save.
---

# gpt-image-gen

Wrapper for OpenAI's image generation API using model `gpt-image-2`.

## Requirements

- `OPENAI_API_KEY` must be set in `.env` (project root)
- Output directory must exist before calling

## API Call

Load the key first, then call:

```bash
# Load .env
export $(grep -v '^#' .env | xargs)

curl -s -X POST "https://api.openai.com/v1/images/generations" \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gpt-image-2",
    "prompt": "<the prompt>",
    "size": "1024x1024",
    "quality": "medium",
    "output_format": "png"
  }' > /tmp/img_response.json
```

## Decode and Save

**Option A — jq (preferred if available):**

```bash
jq -r '.data[0].b64_json' /tmp/img_response.json | base64 --decode > <output-path>.png
```

**Option B — Python fallback (always available):**

```bash
python3 -c "
import json, base64, sys
with open('/tmp/img_response.json') as f:
    data = json.load(f)
b64 = data['data'][0]['b64_json']
with open(sys.argv[1], 'wb') as out:
    out.write(base64.b64decode(b64))
" "<output-path>.png"
```

## Error Handling

If the response contains an `error` field instead of `data`, print the error and stop:

```bash
python3 -c "
import json
with open('/tmp/img_response.json') as f:
    r = json.load(f)
if 'error' in r:
    print('API error:', r['error'])
    exit(1)
"
```

## Model Note

The model is `gpt-image-2` — do not substitute with `dall-e-3`, `gpt-image-1`, or any other model. This model was released April 21, 2026. If a call fails, the issue is the API key or parameters, not the model name.

## Verify Output

Always verify after saving:

```bash
python3 -c "
import os, sys
path = sys.argv[1]
size = os.path.getsize(path) if os.path.exists(path) else 0
print(f'File: {path}  Size: {size} bytes')
if size == 0:
    print('ERROR: file empty or missing')
    exit(1)
" "<output-path>.png"
```
