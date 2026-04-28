# 🦍 Gorilla Kernel 6.19.13-7-ULTIMATE Replication Package

This package contains all the artifacts and scripts necessary to replicate the **6.19.13-7-ULTIMATE** kernel build, optimized for the Sony SVE14A3AJ.

## 📦 Contents

### 🛠️ Build Artifacts (.deb)
- `linux-image-6.19.13_6.19.13-7-ULTIMATE_amd64.deb`: The compiled kernel image.
- `linux-headers-6.19.13_6.19.13-7-ULTIMATE_amd64.deb`: Kernel headers for module compilation.
- `linux-image-6.19.13-dbg_6.19.13-7-ULTIMATE_amd64.deb`: Debugging symbols.
- `linux-libc-dev_6.19.13-7-ULTIMATE_amd64.deb`: Userspace development headers.

### ⚙️ Configuration & Replication
- `ULTIMATE_GORILLA_KERNEL.sh`: The master build script used to automate the entire process (patching, configuration, and compilation).
- `.config` / `performance_tuned.config`: The final kernel configuration used for this build.
- `stable_baked_kernel.config`: The baseline configuration.
- `config_diff.patch`: A patch file showing the changes made from the stable baseline to the performance-tuned configuration.
- `TUNE_AUTONOMOUS.sh`: Advanced system tuning script for low-latency desktop performance.

### 🔍 Metadata & Debugging
- `linux-upstream_6.19.13-7-ULTIMATE_amd64.changes`: Debian changes file listing build metadata.
- `linux-upstream_6.19.13-7-ULTIMATE_amd64.buildinfo`: Build environment information.
- `Module.symvers`: Symbol version information for the kernel.
- `System.map`: Kernel symbol table.
- `gorilla.tree.txt`: A snapshot of the build tree structure.

## 🚀 How to Replicate

1. **Environment Setup**: Ensure you are on a Debian-based system (Trixie/Sid recommended).
2. **Execute Master Script**: Run `./ULTIMATE_GORILLA_KERNEL.sh`.
   - The script will download the kernel 6.19.13 source.
   - It will apply the **ALC269 Sound Boost Patch** (+15dB Gain).
   - It will apply the performance tuning (BBR, FQ, CAKE, -march=native).
3. **Configuration**: The script uses `performance_tuned.config`. If you wish to inspect changes, refer to `config_diff.patch`.
4. **Build**: The script uses `make bindeb-pkg` to generate the `.deb` files.

## 🔧 Installation

To install the pre-compiled packages:
```bash
sudo dpkg -i *.deb
```

## 📝 Hardware Target
- **Model**: Sony SVE14A3AJ
- **CPU**: Intel Core i7-3632QM
- **GPU**: Radeon HD 7670M / Intel HD 4000
- **Audio**: Realtek ALC269
