# lib-posix-c

C backend for the POSIX ports (path, env, time, fs) — renamed from
`lib-os-c`; the `fs` surface was absorbed from the now-superseded
`lib-fs` package. Pure `.hnl` over `ffi.call`.

## Layout

| path | role |
| --- | --- |
| `src/index.hnl` | module index |
| `src/path.hnl` + `path.test.hnl` | path ops (`join`/`resolve`/`basename`/`dirname`/`extname`) |
| `src/env.hnl` + `env.test.hnl` | env ops (`get`/`has`) |
| `src/time.hnl` + `time.test.hnl` | time ops (`now_ms`/`instant_ns`/`elapsed_ns`/`epoch`/`now`, direct `clock_gettime` via `ffi.call`; folded from `lib-time-c`) |
| `src/clock_gettime.hnl` | the `clock_gettime` ffi binding |
| `src/fs.hnl` | fs ops over libc via `ffi.call` (`read_file`/`write_file`/`exists`/`list_dir`/`stat`/`lstat`/`is_dir`/`is_file`/`remove`/`rmdir`/`rename`/`mkdir`) |
| `pkg.hnl`, `scripts/hnl-gate.sh`, `workflows/gate.yaml` | manifest (dep `posix`) / gate / bupha entry |

## Contract

- Implements the `posix` contract (`lib-posix`); `posix-stub` is the
  test backend.

## Verification

```bash
HNL=../host-cli/target/debug/hnl scripts/hnl-gate.sh
```

## License

MIT.

<!-- myco:agent-awareness -->

## Agent awareness

- Session start / any work discussion: run `myco status --prompt`
  before proposing next steps — know the board first.
- User describes new work → offer to capture it (`myco todo add`,
  `issue new`, `proposal new`). Don't wait to be asked.
- Picking up a task: `myco resume <ID>` is the briefing.
- Wrapping up: `myco handoff <ID>` anything resumable; keep statuses
  honest (claimed → in-progress → blocked/done).

<!-- /myco:agent-awareness -->
