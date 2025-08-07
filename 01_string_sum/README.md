# Built as standalone Pixi environment

Following along with [PyO3 tutorial](https://pyo3.rs/v0.25.1/).

All dependencies should are specified in `pyproject.toml`, so you should be able to simply do the following:
```
pixi install
```
To test it out, try running `maturin develop`:
```
maturin develop
# lots of progress output as maturin runs the compilation...
python
>>> import string_sum
>>> string_sum.sum_as_string(5, 20)
'25'
```
If you added the `extension-module` configuration to your `Cargo.toml` above, you should also be able to do `cargo test`.
```
cargo test
```

## VS Code settings

To get `rust-analyzer` working, I had to set the following workspace settings in `.vscode/settings.json`:
```
{
    "rust-analyzer.cargo.sysroot": "<find via the command `pixi run rustc --print sysroot`>",
    "rust-analyzer.cargo.extraEnv": {
        "PYO3_PYTHON": "<find via the command `pixi run which python`>"
    }
}
```
