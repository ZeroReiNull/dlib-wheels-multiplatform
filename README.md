# dlib Wheels

Unofficial prebuilt [dlib](https://github.com/davisking/dlib) wheels for Python. Install without compiling dlib or setting up CMake.

## Install

Download a wheel for your Python version and platform from [Releases](https://github.com/ZeroReiNull/dlib-wheels-multiplatform/releases), then install it:

```bash
uv pip install ./dlib-*.whl
# or
python -m pip install ./dlib-*.whl
```

## Supported builds

- **Python:** CPython 3.10–3.15
- **Windows:** x86-64
- **macOS:** Apple Silicon, macOS 14+
- **Linux:** x86-64 / ARM64 (manylinux and musllinux)

Availability depends on the release assets.

## Builds

[GitHub Actions](https://github.com/ZeroReiNull/dlib-wheels-multiplatform/actions/workflows/build.yaml) builds and tests wheels from official dlib releases, then publishes them with SHA256 checksums. Run the workflow manually to check for new versions; completed releases are skipped unless `force` is enabled.

Older Windows wheels are kept in [archive/windows-amd64](archive/windows-amd64/).

## Credits

Not affiliated with the upstream dlib project. dlib's [upstream license](https://github.com/davisking/dlib/blob/master/dlib/LICENSE.txt) applies to dlib itself. Build workflow inspired in part by [alesanfra/dlib-wheels](https://github.com/alesanfra/dlib-wheels).
