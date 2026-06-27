# Yuanjie AR Mini Program Maintenance Guide

## Project State

- Repository: `yuanjie-ai-group/yuanjie-ar-mp`
- Category: WeChat Mini Program for an AR ironwork museum experience
- Hosting/backend: CloudBase
- Public CloudBase host in inventory: `7463-tcb-advanced-a656fc-1257967285.tcb.qcloud.la`

## Before Editing

- Open the project with WeChat DevTools when changing WXML/WXSS/TypeScript or XR features.
- Do not commit `project.private.config.json`, local preview QR images, `miniprogram_npm/`, or real CloudBase credentials.
- Keep `project.config.json` appid/environment changes intentional and documented.

## Useful Commands

- Install mini program dependencies: `cd miniprogram && npm install`
- Check mini program package manifest: `cd miniprogram && npm run lint`
- Check cloud function syntax: `cd cloudfunctions/getOpenId && npm test`
- Build/upload: use WeChat DevTools or CloudBase pipeline; CLI build is not configured.

## Environment

- `.env.example` documents CloudBase and WeChat identifiers required by operators.
- Runtime configuration is primarily controlled by WeChat DevTools, CloudBase, and `project.config.json`.

## Deployment Notes

- See `DEPLOYMENT.md` before changing CloudBase environment, cloud functions, or public badge/host references.
