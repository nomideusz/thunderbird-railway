# Deploy and Host Thunderbird on Railway

[![Deploy on Railway](https://railway.com/button.svg)](https://railway.com/new/template/thunderbird?utm_medium=integration&utm_source=button&utm_campaign=thunderbird)

This template runs the full desktop [Thunderbird](https://www.thunderbird.net/) application in the cloud, streamed to any device through the [linuxserver.io](https://docs.linuxserver.io/images/docker-thunderbird/) Selkies web interface. Open your Railway domain, log in, and Thunderbird is running on the server with its files, settings and plugins persisted between visits.

## About Hosting Thunderbird

Thunderbird is the open-source mail, calendar and contacts client from Mozilla. The service streams a GPU-less desktop session over WebSockets with the linuxserver.io Selkies stack. Access is gated by HTTP basic auth (`CUSTOM_USER` / generated `PASSWORD`), and the application data persists on a volume at `/config`.

## Common Use Cases

- One always-on client for many IMAP accounts, reachable from any device
- Run mail filters and archiving rules 24/7 without a desktop that stays on
- Access mail from a device where you cannot install a client
- Disposable, isolated environment for opening files you do not fully trust

## Dependencies for Thunderbird Hosting

- None. Single service, no database.

### Deployment Dependencies

- [linuxserver.io Thunderbird image docs](https://docs.linuxserver.io/images/docker-thunderbird/)
- [Selkies project](https://github.com/selkies-project)

### Implementation Details

**First use:** open your Railway domain, log in with `CUSTOM_USER` and the generated `PASSWORD` (service Variables tab), and the Thunderbird window appears. On touch devices, use the sidebar for keyboard and gestures. Files you save under `/config` (the home directory) persist; use the built-in file manager or drag and drop into the browser window to upload, and the download tray to fetch files back.

Notes and limits:

- Keep the login strong: the password gate is the whole security model.
- Rendering is CPU-based (no GPU on Railway). Fine for the application UI and light media; not for GPU-accelerated work.
- Give the service 2 GB of RAM or more; desktop applications are memory-hungry.
- Only `/config` persists. Anything installed outside it is gone after a redeploy.
- Want a whole desktop instead of one app? The same author publishes a [Linux Desktop](https://railway.com/deploy/linux-desktop) template.

## Why Deploy Thunderbird on Railway?

Railway is a singular platform to deploy your infrastructure stack. Railway will host your infrastructure so you don't have to deal with configuration, while allowing you to vertically and horizontally scale it.

By deploying Thunderbird on Railway, you are one step closer to supporting a complete full-stack application with minimal burden. Host your servers, databases, AI agents, and more on Railway.
