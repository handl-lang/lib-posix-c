# lib-posix-c

C backend for the POSIX ports (path, env, time, fs). Renamed from
`lib-os-c`; the `fs` surface was absorbed from the now-superseded
`lib-fs` package.

## Surface

- path — `join`, `resolve`, `basename`, `dirname`, `extname`
- env — `get`, `has`
- time — `now_ms`, `instant_ns`, `elapsed_ns`, `epoch`, `now` (direct `clock_gettime` via `ffi.call`; folded from `lib-time-c`)
- fs — `read_file`, `write_file`, `exists`, `list_dir`, `stat`,
  `lstat`, `is_dir`, `is_file`, `remove`, `rmdir`, `rename`, `mkdir`
  (libc via `ffi.call`; see `src/fs.hnl`)

## Layout

```text
src/             the .hnl sources (index, path, env, time, fs, clock_gettime + tests)
pkg.hnl          package manifest — modules, deps, description, license
ci.sh            bupha entry → scripts/hnl-gate.sh
```

## Gate

```bash
HNL=../host-cli/target/debug/hnl scripts/hnl-gate.sh
```

## License

MIT.
