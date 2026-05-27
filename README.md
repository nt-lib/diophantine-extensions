# diophantine-extensions

Code verifying that Diophantus's original rational quadruple {1/16, 33/16, 17/4, 105/16} has only the two known extensions to a rational quintuple: 549120/10201 and -26880/177241

## Requirements

<!-- List software requirements here, e.g.:
- Magma v2.29-1 or higher
- SageMath X.Y
- Python 3.x
- GNU parallel
-->

## Project layout

| Directory | Contents |
|-----------|----------|
| `computations/` | Magma `.m` and SageMath `.sage` scripts run by `verify_all.sh` |
| `logs/` | Output from `verify_all.sh` (committed as a record of the computations) |
| `src/` | Library/source code shared across computations |
| `tests/` | Test scripts |

## Running computations

To run all scripts in `computations/` in parallel (requires GNU parallel):

```bash
make verify
# or directly:
bash verify_all.sh        # uses 10 parallel jobs by default
bash verify_all.sh 4      # use 4 parallel jobs
```

Output lands in `logs/<script-name>.txt`. SageMath scripts also produce `logs/<script-name>.timing.txt`.

## Running tests

```bash
make test
```

## Running on a remote machine

Syncs the repo to `/tmp/<repo-name>/` on the remote and runs `make test` there:

```bash
make test_remote ssh="user@hostname"
```
