# Built using globally installed tools

Following along with [PyO3 tutorial](https://pyo3.rs/v0.25.1/).

Steps (using Python/Maturin/etc. installed with Pixi global):
```
mkdir 00_string_sum
cd 00_string_sum
python -m venv .venv
source .venv/bin/activate
pip install maturin
```
Then:
```
maturin init --name string_sum
```
Then edit the resulting `Cargo.toml` to set the PyO3 `features` to `extension-module`:
```
[dependencies]
pyo3 = { version = "0.25.0", features = ["extension-module"] }

# # Original:
# [dependencies]
# pyo3 = "0.25.0"
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
