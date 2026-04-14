# Welcome to the OpenInfer Beta Powering Claw Backend
Agentic AI has an infrastructure problem. 90% of agent workloads are background tasks — latency-tolerant, routine, and always-on — yet they're being served on premium compute stacks built for real-time sessions. That mismatch is expensive and unnecessary.

OpenInfer fixes this.

Powered by Weave, our inference orchestration engine, OpenInfer routes each workload based on its SLA and workload characteristics to the right compute topology automatically. The result: major compute dependency unlock and real cost control at scale.

**OpenClaw** is the first application built on OpenInfer Beta. Run it free across our partner cloud ecosystem, starting with AWS.

## Get Started

Free production trial available at [openinfer.io/beta](https://openinfer.io/beta)
> OpenInfer Beta is under active development. APIs and interfaces are subject to change.




There are two ways to set up the OpenInfer backend for Claw.

## Option 1: Replace your OpenClaw config

If you are new to OpenClaw, the easiest way is to download the config file below and replace your existing config:

[Download the config file](https://drive.google.com/file/d/12_kVKs_SVnZ-saE36RNLA9QTjwy1Ge6E/view?usp=drive_link)

Place the downloaded config in `~/.openclaw`.

> [!WARNING]
> This will replace your existing OpenClaw config.
> Be sure to back up your current config files before replacing them.

## Option 2: Add OpenInfer to your existing OpenClaw config

If you are already using OpenClaw and do not want to reset your config, open the config in ~/.openclaw/openclaw.json and follow these steps.

### 1. Add a new provider

Add a new provider under `models.providers`, for example `models.providers.openinfer`, with the following configuration:

```json
{
  "baseUrl": "http://api.openinfer.io:9080/openai/v1",
  "apiKey": "9b8f3d7c1a6e4f20b5c9a1d8e7f34c62",
  "api": "openai-responses",
  "models": [
    {
      "id": "@oi/beta",
      "name": "@oi/beta",
      "reasoning": false,
      "input": [
        "text"
      ]
    }
  ],
  "headers": {
    "X-Session-ID": "openclaw-responses-2"
  }
}
```

### 2. Set the default model

Set `agents.defaults.model.primary` to:

```text
providername/@oi/beta
```

Example:

```text
openinfer/@oi/beta
```

## You're all set

After saving these changes, OpenClaw should be ready to use with the OpenInfer backend.
