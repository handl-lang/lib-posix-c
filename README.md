# lib-posix-c

C backend for the POSIX ports (path, env, time, fs). Renamed from
`lib-os-c`; the `fs` surface was absorbed from the now-superseded
`lib-fs` package.

## Surface

- path — `join`, `resolve`, `basename`, `dirname`, `extname`
- env — `get`, `has`
- time — `now`, `epoch` (delegates to `time-c`)
- fs — `read_file`, `write_file`, `exists`, `list_dir`, `stat`,
  `lstat`, `is_dir`, `is_file`, `remove`, `rmdir`, `rename`, `mkdir`
  (libc via `ffi.call`; see `src/fs.hnl`)

## Layout

```text
src/             the .hnl sources (index/path/env/time/fs.hnl + tests)
pkg.hnl          package manifest — modules, deps, description, license
ci.sh            bupha entry → scripts/hnl-gate.sh
```

## Gate

```bash
HNL=../host-cli/target/debug/hnl scripts/hnl-gate.sh
```

## License

MIT.
