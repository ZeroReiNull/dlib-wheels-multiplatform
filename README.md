# dlib Wheels

Unofficial precompiled Python wheels built from the [official dlib source](https://github.com/davisking/dlib). This repository provides ready-to-install wheels without requiring users to compile dlib or install CMake locally.

> **Unofficial distribution.** This project is not affiliated with or maintained by the dlib developers. For the original project, documentation, and source code, visit [davisking/dlib](https://github.com/davisking/dlib).

## Download and install

Get wheels from [**GitHub Releases**](https://github.com/ZeroReiNull/dlib-wheels-multiplatform/releases). Choose a file matching your **Python version**, **operating system**, and **CPU architecture**.

For example, with [uv](https://docs.astral.sh/uv/):

```bash
uv add ./dlib-<version>-<python-tag>-<abi-tag>-<platform>.whl
```

Or with pip:

```bash
python -m pip install ./dlib-<version>-<python-tag>-<abi-tag>-<platform>.whl
```

Replace the example filename with the exact downloaded filename. The release's `SHA256SUMS.txt` contains checksums for verifying downloaded files.

Verify the installation:

```bash
python -c "import dlib; print(dlib.__version__)"
```

A wheel installs the compiled Python extension; **CMake is needed by the GitHub Actions build, not on the machine installing a compatible wheel**.

## Build targets

The [workflow](.github/workflows/build.yaml) currently targets CPython **3.10–3.15**, on these platforms:

| Operating system | Architecture | Wheel platform |
| --- | --- | --- |
| Windows | x86-64 | `win_amd64` |
| macOS 14+ | Apple Silicon (ARM64) | `macosx_arm64` |
| Linux (glibc / manylinux) | x86-64 | `manylinux_x86_64` |
| Linux (glibc / manylinux) | ARM64 | `manylinux_aarch64` |
| Linux (musl / musllinux) | x86-64 | `musllinux_x86_64` |
| Linux (musl / musllinux) | ARM64 | `musllinux_aarch64` |

These are **build targets**, not a guarantee that every wheel has been published or tested on every end-user system. Check the assets and status of a specific release. Windows ARM64 and Intel macOS are not currently built.

## Build and release process

1. Open [**Actions → Build dlib Wheels**](https://github.com/ZeroReiNull/dlib-wheels-multiplatform/actions/workflows/build.yaml) and select **Run workflow**.
2. The workflow discovers the latest official dlib GitHub Release and checks whether a complete corresponding wheel release already exists here.
3. If needed, it checks out that official dlib version and builds/tests the six platform targets with `cibuildwheel`.
4. After all targeted wheels pass validation, it uploads them with SHA256 checksums to a GitHub Release.

An existing complete release is skipped by default. Enable **force** only when you intentionally want a fresh build; the workflow makes a separate revision-tagged release instead of overwriting an earlier one.

The repository itself does not vendor dlib source code. Builds use an official tagged source revision. Native build dependencies are installed in GitHub-hosted build environments.

## Legacy Windows wheels

Previously published Windows x86-64 wheels are preserved under [`archive/windows-amd64/`](archive/windows-amd64/), including older dlib and Python versions. They are kept for historical compatibility, **not** part of the current automated release matrix. These files are provided as-is, without a claim of current security, compatibility, or regression testing.

Use [GitHub Releases](https://github.com/ZeroReiNull/dlib-wheels-multiplatform/releases) for newly built wheels instead of the archived binaries.

## Notes

- The package distribution name remains **`dlib`** (not `dlib-bin`), so compatible tools can resolve the expected Python package name.
- Test the wheel on your actual target device and workload before relying on it.
- The upstream dlib project and its [license](https://github.com/davisking/dlib/blob/master/dlib/LICENSE.txt) remain authoritative. These binaries are independently built and distributed.
- To report a packaging/build issue, open a [repository issue](https://github.com/ZeroReiNull/dlib-wheels-multiplatform/issues). For problems in dlib itself, refer to the upstream project.

## Acknowledgements

Build workflow inspired in part by [alesanfra/dlib-wheels](https://github.com/alesanfra/dlib-wheels).
