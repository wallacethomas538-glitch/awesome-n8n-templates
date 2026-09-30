# VektorFlow EventBus integration

This folder contains original n8n workflow glue for VektorFlow. It does not replace the VektorFlow EventBus or copy VektorFlow agent logic into n8n.

## Workflow

Import `VektorFlow EventBus Ingress.json` into an n8n instance.

The workflow exposes:

`POST /webhook/vektorflow/eventbus`

It validates the VektorFlow event envelope:

- `event_id`
- `event_type`
- `source`
- `timestamp`
- `data`

It then acknowledges the event. The workflow is intentionally inactive on import so credentials and downstream actions can be configured before activation.

## VektorFlow side

The VektorFlow EventBus adapter is configured with:

- `N8N_EVENT_WEBHOOK_URL`
- `N8N_EVENT_TYPES` (optional)
- `N8N_SHARED_SECRET` (optional)
- `N8N_WEBHOOK_TIMEOUT` (optional)
- `N8N_MAX_RETRIES` (optional)
- `N8N_RETRY_BACKOFF` (optional)

The adapter sends a stable event ID and can sign requests with HMAC-SHA256 when `N8N_SHARED_SECRET` is configured.

## Important

This repository is a template collection. The workflow above is an integration artifact, not a replacement for VektorFlow. Template files elsewhere in this repository may have their own original licenses and attribution requirements; review those before redistributing or embedding them in production.

A live connection requires an actual n8n instance with the imported workflow activated and a reachable production webhook URL. No production URL or credential is hard-coded here.
