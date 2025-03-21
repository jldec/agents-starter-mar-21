# agents-starter-mar-21

Another repro for https://github.com/cloudflare/workerd/issues/3761

I seem to be able to reproduce the issue quite reliably

#### Steps
- clone repo
- `pnpm install`
- `pnpm dev`
- type 'o' to open the browser
- reload browser - confirm new log `Connection xx-xx-xx-xx connected to Chat:default`
- wait a few seconds to see error

```txt
$ pnpm dev

> cloudflare-agent-starter@1.0.0 dev /Users/jldec/cloudflare/agents-starter-mar-21
> vite dev


  VITE v6.2.2  ready in 3391 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
  ➜  press h + enter to show help
1:33:53 PM [vite] (agents_starter_mar_21) ✨ new dependencies optimized: @cloudflare/unenv-preset/runtime/node/process/index, unenv/runtime/polyfill/performance, @cloudflare/unenv-preset/runtime/node/console/index, @cloudflare/unenv-preset/runtime/node/async_hooks/index
1:33:53 PM [vite] (agents_starter_mar_21) ✨ optimized dependencies changed. reloading
[vite] program reload

1:33:53 PM [vite] (agents_starter_mar_21) ✨ new dependencies optimized: unenv/runtime/node/tty/index
1:33:53 PM [vite] (agents_starter_mar_21) ✨ optimized dependencies changed. reloading
Connection f6b456b0-d6d5-4e05-b204-e7440b1c7da2 connected to Chat:default

Connection 8167f103-7ce7-49b2-b081-da4574e417bc connected to Chat:default

workerd/server/server.c++:3882: error: Uncaught exception: kj/compat/http.c++:4098: disconnected: worker_do_not_log; Request failed due to internal error
stack: 100f77840 101a06a28 101a06b17 10300ce2b 100f77840 101a1db9c 101a06a28 101a06b17 10300ce2b 100f77840 101a1db9c 101a06a28 101a06b17 10300ce2b 100f77840 101a1db9c 101a06a28 101a06b17 10300ce2b 100f77840 101a1db9c 1012af25f 1010eaa24 100f84478 100f84e6c 1009ea277 101a2b6e3 101a2c6f3 101a2d127 1019ffed8

```