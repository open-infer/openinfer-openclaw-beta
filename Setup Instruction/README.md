# Welcome to the OpenInfer Claw Backend

There are two ways to set up the OpenInfer backend for Claw.

## Option 1: Replace your OpenClaw config

If you are new to OpenClaw, the easiest way is to download the config file below and replace your existing config:

[Download the config file](https://drive.google.com/file/d/12_kVKs_SVnZ-saE36RNLA9QTjwy1Ge6E/view?usp=drive_link)

Place the downloaded config in `~/.openclaw`.

> [!WARNING]
> This will replace your existing OpenClaw config.
> Be sure to back up your current config files before replacing them.

## Option 2: Add OpenInfer to your existing OpenClaw config

If you are already using OpenClaw and do not want to reset your config, follow these steps.

### 1. Add a new provider

Add a new provider under `models.providers`, for example `models.providers.openinfer`, with the following configuration:

```json
{
  "baseUrl": "http://api.openinfer.io/openai/v1",
  "apiKey": "9b8f3d7c1a6e4f20b5c9a1d8e7f34c62",
  "api": "openai-responses",
  "models": [
    {
      "id": "@url/https://openinfer-memento-demo.s3.us-west-1.amazonaws.com/models/openinfer.gguf",
      "name": "@url/https://openinfer-memento-demo.s3.us-west-1.amazonaws.com/models/openinfer.gguf",
      "reasoning": false,
      "input": [
        "text"
      ],
      "cost": {
        "input": 0,
        "output": 0,
        "cacheRead": 0,
        "cacheWrite": 0
      },
      "contextWindow": 128000,
      "maxTokens": 16384
    }
  ]
}
```

### 2. Set the default model

Set `agents.defaults.model.primary` to:

```text
providername/@url/https://openinfer-memento-demo.s3.us-west-1.amazonaws.com/models/openinfer.gguf
```

Example:

```text
openinfer/@url/https://openinfer-memento-demo.s3.us-west-1.amazonaws.com/models/openinfer.gguf
```

## You're all set

After saving these changes, OpenClaw should be ready to use with the OpenInfer backend.
