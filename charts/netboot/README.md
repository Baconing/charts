# netboot

![Version: 1.0.0-alpha-2026.10](https://img.shields.io/badge/Version-1.0.0--alpha--2026.10-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

A custom, high availability (soon), declarative netbooting solution.

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Brenden (Baconing) Freier | <iam@baconi.ng> | <https://baconi.ng> |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| extraContainers | list | `[]` |  |
| extraFiles | object | `{"http":[{"checksumUrl":null,"content":null,"name":null,"url":null}],"tftp":[{"checksumUrl":null,"content":null,"name":null,"url":null}]}` | The extra files that will be exposed on the TFTP and HTTP servers. This is useful for serving kernels, initramfs, and ISOs on your LAN instead of having to download them from the internet every time you want to netboot a machine. Files here are saved to persistent storage (if enabled), even if the content variable is set. |
| extraFiles.http | list | `[{"checksumUrl":null,"content":null,"name":null,"url":null}]` | Files here will be exposed on the HTTP server. |
| extraFiles.http[0].checksumUrl | string | `nil` | The URL to the checksum file for the file. If this is set, the checksum will be verified before serving the file. If the file doesn't match the checksum, it will be re-downloaded from the url. Otherwise, it will not be served. If the file doesn't match the checksum right after a download, it will not be served or saved. |
| extraFiles.http[0].content | string | `nil` | The content of the file. If this is set, url will be ignored. |
| extraFiles.http[0].url | string | `nil` | The URL to fetch the file from. If this is set, content will be ignored. |
| extraFiles.tftp | list | `[{"checksumUrl":null,"content":null,"name":null,"url":null}]` | Files here will be exposed on the TFTP server. |
| extraFiles.tftp[0].checksumUrl | string | `nil` | The URL to the checksum file for the file. If this is set, the checksum will be verified before serving the file. If the file doesn't match the checksum, it will be re-downloaded from the url. Otherwise, it will not be served. If the file doesn't match the checksum right after a download, it will not be served or saved. |
| extraFiles.tftp[0].content | string | `nil` | The content of the file. If this is set, url will be ignored. |
| extraFiles.tftp[0].url | string | `nil` | The URL to fetch the file from. If this is set, content will be ignored. |
| extraHTTPVolumeMounts | list | `[]` |  |
| extraInitContainers | list | `[]` |  |
| extraInitVolumeMounts | list | `[]` |  |
| extraTFTPVolumeMounts | list | `[]` |  |
| extraVolumes | list | `[]` |  |
| fullnameOverride | string | `""` |  |
| ipxe | object | `{"arm32-efi":{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/arm32-efi/ipxe.efi"},"ipxe-legacy":{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/arm32-efi/ipxe-legacy.efi"},"prefix":"arm32-efi-","snponly":{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/arm32-efi/snponly.efi"}},"arm64-efi":{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/arm64-efi/ipxe.efi"},"ipxe-legacy":{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/arm64-efi/ipxe-legacy.efi"},"prefix":"arm64-efi-","snponly":{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/arm64-efi/snponly.efi"}},"i386-efi":{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/i386-efi/ipxe.efi"},"ipxe-legacy":{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/i386-efi/ipxe-legacy.efi"},"prefix":"i386-efi-","snponly":{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/i386-efi/snponly.efi"}},"loongarch32-efi":{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/loongarch32-efi/ipxe.efi"},"ipxe-legacy":{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/loongarch32-efi/ipxe-legacy.efi"},"prefix":"loongarch32-efi-","snponly":{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/loongarch32-efi/snponly.efi"}},"loongarch64-efi":{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/loongarch64-efi/ipxe.efi"},"ipxe-legacy":{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/loongarch64-efi/ipxe-legacy.efi"},"prefix":"loongarch64-efi-","snponly":{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/loongarch64-efi/snponly.efi"}},"riscv32-efi":{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/riscv32-efi/ipxe.efi"},"ipxe-legacy":{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/riscv32-efi/ipxe-legacy.efi"},"prefix":"riscv32-efi-","snponly":{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/riscv32-efi/snponly.efi"}},"riscv64-efi":{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/riscv64-efi/ipxe.efi"},"ipxe-legacy":{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/riscv64-efi/ipxe-legacy.efi"},"prefix":"riscv64-efi-","snponly":{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/riscv64-efi/snponly.efi"}},"x86":{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.pxe","url":"http://boot.ipxe.org/ipxe.pxe"},"prefix":"x86-","undionly":{"enabled":true,"name":"undionly.kpxe","url":"http://boot.ipxe.org/undionly.kpxe"}},"x86_64-bios":{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.pxe","url":"http://boot.ipxe.org/x86_64-pcbios/ipxe.pxe"},"prefix":"x86_64-bios-","undionly":{"enabled":true,"name":"undionly.kpxe","url":"http://boot.ipxe.org/x86_64-pcbios/undionly.kpxe"}},"x86_64-efi":{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/x86_64-efi/ipxe.efi"},"ipxe-legacy":{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/x86_64-efi/ipxe-legacy.efi"},"prefix":"x86_64-efi-","snponly":{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/x86_64-efi/snponly.efi"}}}` | The URLs to fetch the iPXE binaries from. Use extraFiles.tftp to serve additional iPXE binaries not listed here. Files here are saved to persistent storage (if enabled). |
| ipxe.arm32-efi | object | `{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/arm32-efi/ipxe.efi"},"ipxe-legacy":{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/arm32-efi/ipxe-legacy.efi"},"prefix":"arm32-efi-","snponly":{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/arm32-efi/snponly.efi"}}` | ARM32 EFI iPXE binaries. |
| ipxe.arm32-efi.enabled | bool | `true` | Download and serve ARM32 EFI iPXE binaries. |
| ipxe.arm32-efi.ipxe | object | `{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/arm32-efi/ipxe.efi"}` | ARM32 EFI iPXE binary (uses built-in iPXE NIC drivers). |
| ipxe.arm32-efi.ipxe-legacy | object | `{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/arm32-efi/ipxe-legacy.efi"}` | Legacy ARM32 EFI iPXE binary (no USB NIC drivers). |
| ipxe.arm32-efi.ipxe-legacy.name | string | `"ipxe-legacy.efi"` | The name of the binary served on the TFTP server. |
| ipxe.arm32-efi.ipxe-legacy.url | string | `"http://boot.ipxe.org/arm32-efi/ipxe-legacy.efi"` | The URL to fetch the ARM32 EFI ipxe-legacy.efi binary from. |
| ipxe.arm32-efi.ipxe.name | string | `"ipxe.efi"` | The name of the binary served on the TFTP server. |
| ipxe.arm32-efi.ipxe.url | string | `"http://boot.ipxe.org/arm32-efi/ipxe.efi"` | The URL to fetch the ARM32 EFI ipxe.efi binary from. |
| ipxe.arm32-efi.prefix | string | `"arm32-efi-"` | Prefixes for the TFTP filenames of ARM32 EFI iPXE binaries. Prevents clashing with other architectures. |
| ipxe.arm32-efi.snponly | object | `{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/arm32-efi/snponly.efi"}` | ARM32 EFI iPXE binary with Simple Network Protocol. |
| ipxe.arm32-efi.snponly.name | string | `"snponly.efi"` | The name of the binary served on the TFTP server. |
| ipxe.arm32-efi.snponly.url | string | `"http://boot.ipxe.org/arm32-efi/snponly.efi"` | The URL to fetch the ARM32 EFI snponly.efi binary from. |
| ipxe.arm64-efi | object | `{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/arm64-efi/ipxe.efi"},"ipxe-legacy":{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/arm64-efi/ipxe-legacy.efi"},"prefix":"arm64-efi-","snponly":{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/arm64-efi/snponly.efi"}}` | ARM64 EFI iPXE binaries. |
| ipxe.arm64-efi.enabled | bool | `true` | Download and serve ARM64 EFI iPXE binaries. |
| ipxe.arm64-efi.ipxe | object | `{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/arm64-efi/ipxe.efi"}` | ARM64 EFI iPXE binary (uses built-in iPXE NIC drivers). |
| ipxe.arm64-efi.ipxe-legacy | object | `{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/arm64-efi/ipxe-legacy.efi"}` | Legacy ARM64 EFI iPXE binary (no USB NIC drivers). |
| ipxe.arm64-efi.ipxe-legacy.name | string | `"ipxe-legacy.efi"` | The name of the binary served on the TFTP server. |
| ipxe.arm64-efi.ipxe-legacy.url | string | `"http://boot.ipxe.org/arm64-efi/ipxe-legacy.efi"` | The URL to fetch the ARM64 EFI ipxe-legacy.efi binary from. |
| ipxe.arm64-efi.ipxe.name | string | `"ipxe.efi"` | The name of the binary served on the TFTP server. |
| ipxe.arm64-efi.ipxe.url | string | `"http://boot.ipxe.org/arm64-efi/ipxe.efi"` | The URL to fetch the ARM64 EFI ipxe.efi binary from. |
| ipxe.arm64-efi.prefix | string | `"arm64-efi-"` | Prefixes for the TFTP filenames of ARM64 EFI iPXE binaries. Prevents clashing with other architectures. |
| ipxe.arm64-efi.snponly | object | `{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/arm64-efi/snponly.efi"}` | ARM64 EFI iPXE binary with Simple Network Protocol. |
| ipxe.arm64-efi.snponly.name | string | `"snponly.efi"` | The name of the binary served on the TFTP server. |
| ipxe.arm64-efi.snponly.url | string | `"http://boot.ipxe.org/arm64-efi/snponly.efi"` | The URL to fetch the ARM64 EFI snponly.efi binary from. |
| ipxe.i386-efi | object | `{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/i386-efi/ipxe.efi"},"ipxe-legacy":{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/i386-efi/ipxe-legacy.efi"},"prefix":"i386-efi-","snponly":{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/i386-efi/snponly.efi"}}` | i386 EFI iPXE binaries. |
| ipxe.i386-efi.enabled | bool | `true` | Download and serve i386 EFI iPXE binaries. |
| ipxe.i386-efi.ipxe | object | `{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/i386-efi/ipxe.efi"}` | i386 EFI iPXE binary (uses built-in iPXE NIC drivers). |
| ipxe.i386-efi.ipxe-legacy | object | `{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/i386-efi/ipxe-legacy.efi"}` | Legacy i386 EFI iPXE binary (no USB NIC drivers). |
| ipxe.i386-efi.ipxe-legacy.name | string | `"ipxe-legacy.efi"` | The name of the binary served on the TFTP server. |
| ipxe.i386-efi.ipxe-legacy.url | string | `"http://boot.ipxe.org/i386-efi/ipxe-legacy.efi"` | The URL to fetch the i386 EFI ipxe-legacy.efi binary from. |
| ipxe.i386-efi.ipxe.name | string | `"ipxe.efi"` | The name of the binary served on the TFTP server. |
| ipxe.i386-efi.ipxe.url | string | `"http://boot.ipxe.org/i386-efi/ipxe.efi"` | The URL to fetch the i386 EFI ipxe.efi binary from. |
| ipxe.i386-efi.prefix | string | `"i386-efi-"` | Prefixes for the TFTP filenames of i386 EFI iPXE binaries. Prevents clashing with other architectures. |
| ipxe.i386-efi.snponly | object | `{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/i386-efi/snponly.efi"}` | i386 EFI iPXE binary with Simple Network Protocol. |
| ipxe.i386-efi.snponly.name | string | `"snponly.efi"` | The name of the binary served on the TFTP server. |
| ipxe.i386-efi.snponly.url | string | `"http://boot.ipxe.org/i386-efi/snponly.efi"` | The URL to fetch the i386 EFI snponly.efi binary from. |
| ipxe.loongarch32-efi | object | `{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/loongarch32-efi/ipxe.efi"},"ipxe-legacy":{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/loongarch32-efi/ipxe-legacy.efi"},"prefix":"loongarch32-efi-","snponly":{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/loongarch32-efi/snponly.efi"}}` | LoongArch32 EFI iPXE binaries. |
| ipxe.loongarch32-efi.enabled | bool | `true` | Download and serve LoongArch32 EFI iPXE binaries. |
| ipxe.loongarch32-efi.ipxe | object | `{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/loongarch32-efi/ipxe.efi"}` | LoongArch32 EFI iPXE binary (uses built-in iPXE NIC drivers). |
| ipxe.loongarch32-efi.ipxe-legacy | object | `{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/loongarch32-efi/ipxe-legacy.efi"}` | Legacy LoongArch32 EFI iPXE binary (no USB NIC drivers). |
| ipxe.loongarch32-efi.ipxe-legacy.name | string | `"ipxe-legacy.efi"` | The name of the binary served on the TFTP server. |
| ipxe.loongarch32-efi.ipxe-legacy.url | string | `"http://boot.ipxe.org/loongarch32-efi/ipxe-legacy.efi"` | The URL to fetch the LoongArch32 EFI ipxe-legacy.efi |
| ipxe.loongarch32-efi.ipxe.name | string | `"ipxe.efi"` | The name of the binary served on the TFTP server. |
| ipxe.loongarch32-efi.ipxe.url | string | `"http://boot.ipxe.org/loongarch32-efi/ipxe.efi"` | The URL to fetch the LoongArch32 EFI ipxe.efi binary from. |
| ipxe.loongarch32-efi.prefix | string | `"loongarch32-efi-"` | Prefixes for the TFTP filenames of LoongArch32 EFI iPXE binaries. Prevents clashing with other architectures. |
| ipxe.loongarch32-efi.snponly | object | `{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/loongarch32-efi/snponly.efi"}` | LoongArch32 EFI iPXE binary with Simple Network Protocol. |
| ipxe.loongarch32-efi.snponly.name | string | `"snponly.efi"` | The name of the binary served on the TFTP server. |
| ipxe.loongarch32-efi.snponly.url | string | `"http://boot.ipxe.org/loongarch32-efi/snponly.efi"` | The URL to fetch the LoongArch32 EFI snponly.efi binary from. |
| ipxe.loongarch64-efi | object | `{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/loongarch64-efi/ipxe.efi"},"ipxe-legacy":{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/loongarch64-efi/ipxe-legacy.efi"},"prefix":"loongarch64-efi-","snponly":{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/loongarch64-efi/snponly.efi"}}` | LoongArch64 EFI iPXE binaries. |
| ipxe.loongarch64-efi.enabled | bool | `true` | Download and serve LoongArch64 EFI iPXE binaries. |
| ipxe.loongarch64-efi.ipxe | object | `{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/loongarch64-efi/ipxe.efi"}` | LoongArch64 EFI iPXE binary (uses built-in iPXE NIC drivers). |
| ipxe.loongarch64-efi.ipxe-legacy | object | `{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/loongarch64-efi/ipxe-legacy.efi"}` | Legacy LoongArch64 EFI iPXE binary (no USB NIC drivers). |
| ipxe.loongarch64-efi.ipxe-legacy.name | string | `"ipxe-legacy.efi"` | The name of the binary served on the TFTP server. |
| ipxe.loongarch64-efi.ipxe-legacy.url | string | `"http://boot.ipxe.org/loongarch64-efi/ipxe-legacy.efi"` | The URL to fetch the LoongArch64 EFI ipxe-legacy.efi binary from. |
| ipxe.loongarch64-efi.ipxe.name | string | `"ipxe.efi"` | The name of the binary served on the TFTP server. |
| ipxe.loongarch64-efi.ipxe.url | string | `"http://boot.ipxe.org/loongarch64-efi/ipxe.efi"` | The URL to fetch the LoongArch64 EFI ipxe.efi binary from. |
| ipxe.loongarch64-efi.prefix | string | `"loongarch64-efi-"` | Prefixes for the TFTP filenames of LoongArch64 EFI iPXE binaries. Prevents clashing with other architectures. |
| ipxe.loongarch64-efi.snponly | object | `{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/loongarch64-efi/snponly.efi"}` | LoongArch64 EFI iPXE binary with Simple Network Protocol. |
| ipxe.loongarch64-efi.snponly.name | string | `"snponly.efi"` | The name of the binary served on the TFTP server. |
| ipxe.loongarch64-efi.snponly.url | string | `"http://boot.ipxe.org/loongarch64-efi/snponly.efi"` | The URL to fetch the LoongArch64 EFI snponly.efi binary from. |
| ipxe.riscv32-efi | object | `{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/riscv32-efi/ipxe.efi"},"ipxe-legacy":{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/riscv32-efi/ipxe-legacy.efi"},"prefix":"riscv32-efi-","snponly":{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/riscv32-efi/snponly.efi"}}` | RISC-V 32-bit EFI iPXE binaries. |
| ipxe.riscv32-efi.enabled | bool | `true` | Download and serve RISC-V 32-bit EFI iPXE binaries. |
| ipxe.riscv32-efi.ipxe | object | `{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/riscv32-efi/ipxe.efi"}` | RISC-V 32-bit EFI iPXE binary (uses built-in iPXE NIC drivers). |
| ipxe.riscv32-efi.ipxe-legacy | object | `{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/riscv32-efi/ipxe-legacy.efi"}` | Legacy RISC-V 32-bit EFI iPXE binary (no USB NIC drivers). |
| ipxe.riscv32-efi.ipxe-legacy.name | string | `"ipxe-legacy.efi"` | The name of the binary served on the TFTP server. |
| ipxe.riscv32-efi.ipxe-legacy.url | string | `"http://boot.ipxe.org/riscv32-efi/ipxe-legacy.efi"` | The URL to fetch the RISC-V 32-bit EFI ipxe-legacy.efi binary from. |
| ipxe.riscv32-efi.ipxe.name | string | `"ipxe.efi"` | The name of the binary served on the TFTP server. |
| ipxe.riscv32-efi.ipxe.url | string | `"http://boot.ipxe.org/riscv32-efi/ipxe.efi"` | The URL to fetch the RISC-V 32-bit EFI ipxe.efi |
| ipxe.riscv32-efi.prefix | string | `"riscv32-efi-"` | Prefixes for the TFTP filenames of RISC-V 32-bit EFI iPXE binaries. Prevents clashing with other architectures. |
| ipxe.riscv32-efi.snponly | object | `{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/riscv32-efi/snponly.efi"}` | RISC-V 32-bit EFI iPXE binary with Simple Network Protocol. |
| ipxe.riscv32-efi.snponly.name | string | `"snponly.efi"` | The name of the binary served on the TFTP server. |
| ipxe.riscv32-efi.snponly.url | string | `"http://boot.ipxe.org/riscv32-efi/snponly.efi"` | The URL to fetch the RISC-V 32-bit EFI snponly.efi binary from. |
| ipxe.riscv64-efi | object | `{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/riscv64-efi/ipxe.efi"},"ipxe-legacy":{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/riscv64-efi/ipxe-legacy.efi"},"prefix":"riscv64-efi-","snponly":{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/riscv64-efi/snponly.efi"}}` | RISC-V 64-bit EFI iPXE binaries. |
| ipxe.riscv64-efi.enabled | bool | `true` | Download and serve RISC-V 64-bit EFI iPXE binaries. |
| ipxe.riscv64-efi.ipxe | object | `{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/riscv64-efi/ipxe.efi"}` | RISC-V 64-bit EFI iPXE binary (uses built-in iPXE NIC drivers). |
| ipxe.riscv64-efi.ipxe-legacy | object | `{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/riscv64-efi/ipxe-legacy.efi"}` | Legacy RISC-V 64-bit EFI iPXE binary (no USB NIC drivers). |
| ipxe.riscv64-efi.ipxe-legacy.name | string | `"ipxe-legacy.efi"` | The name of the binary served on the TFTP server. |
| ipxe.riscv64-efi.ipxe-legacy.url | string | `"http://boot.ipxe.org/riscv64-efi/ipxe-legacy.efi"` | The URL to fetch the RISC-V 64-bit EFI ipxe-legacy.efi binary from. |
| ipxe.riscv64-efi.ipxe.name | string | `"ipxe.efi"` | The name of the binary served on the TFTP server. |
| ipxe.riscv64-efi.ipxe.url | string | `"http://boot.ipxe.org/riscv64-efi/ipxe.efi"` | The URL to fetch the RISC-V 64-bit EFI ipxe.efi binary from. |
| ipxe.riscv64-efi.prefix | string | `"riscv64-efi-"` | Prefixes for the TFTP filenames of RISC-V 64-bit EFI iPXE binaries. Prevents clashing with other architectures. |
| ipxe.riscv64-efi.snponly | object | `{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/riscv64-efi/snponly.efi"}` | RISC-V 64-bit EFI iPXE binary with Simple Network Protocol. |
| ipxe.riscv64-efi.snponly.name | string | `"snponly.efi"` | The name of the binary served on the TFTP server. |
| ipxe.riscv64-efi.snponly.url | string | `"http://boot.ipxe.org/riscv64-efi/snponly.efi"` | The URL to fetch the RISC-V 64-bit EFI snponly.efi binary from. |
| ipxe.x86.enabled | bool | `true` | Download and serve x86 iPXE binaries. |
| ipxe.x86.ipxe | object | `{"enabled":true,"name":"ipxe.pxe","url":"http://boot.ipxe.org/ipxe.pxe"}` | x86 iPXE binary (unloads UNDI drivers and relies on iPXE's built-in NIC drivers). |
| ipxe.x86.ipxe.name | string | `"ipxe.pxe"` | The name of the binary served on the TFTP server. |
| ipxe.x86.ipxe.url | string | `"http://boot.ipxe.org/ipxe.pxe"` | The URL to fetch the x86 ipxe.pxe binary from. |
| ipxe.x86.prefix | string | `"x86-"` | Prefixes for the TFTP filenames of x86 iPXE binaries. Prevents clashing with other architectures. |
| ipxe.x86.undionly | object | `{"enabled":true,"name":"undionly.kpxe","url":"http://boot.ipxe.org/undionly.kpxe"}` | x86 iPXE binary (keeps the UNDI drivers loaded) |
| ipxe.x86.undionly.name | string | `"undionly.kpxe"` | The name of the binary served on the TFTP server. |
| ipxe.x86.undionly.url | string | `"http://boot.ipxe.org/undionly.kpxe"` | The URL to fetch the x86 undionly.kpxe binary from. |
| ipxe.x86_64-bios | object | `{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.pxe","url":"http://boot.ipxe.org/x86_64-pcbios/ipxe.pxe"},"prefix":"x86_64-bios-","undionly":{"enabled":true,"name":"undionly.kpxe","url":"http://boot.ipxe.org/x86_64-pcbios/undionly.kpxe"}}` | x86_64 Legacy/BIOS iPXE binaries. |
| ipxe.x86_64-bios.enabled | bool | `true` | Download and serve x86_64 Legacy/BIOS iPXE binaries. |
| ipxe.x86_64-bios.ipxe | object | `{"enabled":true,"name":"ipxe.pxe","url":"http://boot.ipxe.org/x86_64-pcbios/ipxe.pxe"}` | x86_64 Legacy/BIOS iPXE binary (unloads UNDI drivers and relies on iPXE's built-in NIC drivers). |
| ipxe.x86_64-bios.ipxe.name | string | `"ipxe.pxe"` | The name of the binary served on the TFTP server. |
| ipxe.x86_64-bios.ipxe.url | string | `"http://boot.ipxe.org/x86_64-pcbios/ipxe.pxe"` | The URL to fetch the x86_64 Legacy/BIOS ipxe.pxe binary from. |
| ipxe.x86_64-bios.prefix | string | `"x86_64-bios-"` | Prefixes for the TFTP filenames of x86_64 Legacy/BIOS binaries. Prevents clashing with other architectures. |
| ipxe.x86_64-bios.undionly | object | `{"enabled":true,"name":"undionly.kpxe","url":"http://boot.ipxe.org/x86_64-pcbios/undionly.kpxe"}` | Legacy x86_64 Legacy/BIOS iPXE binary (keeps the UNDI drivers loaded) |
| ipxe.x86_64-bios.undionly.name | string | `"undionly.kpxe"` | The name of the binary served on the TFTP server. |
| ipxe.x86_64-bios.undionly.url | string | `"http://boot.ipxe.org/x86_64-pcbios/undionly.kpxe"` | The URL to fetch the x86_64 Legacy/BIOS undionly.kpxe binary from. |
| ipxe.x86_64-efi | object | `{"enabled":true,"ipxe":{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/x86_64-efi/ipxe.efi"},"ipxe-legacy":{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/x86_64-efi/ipxe-legacy.efi"},"prefix":"x86_64-efi-","snponly":{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/x86_64-efi/snponly.efi"}}` | x86_64 EFI iPXE binaries. |
| ipxe.x86_64-efi.enabled | bool | `true` | Download and serve x86_64 EFI iPXE binaries. |
| ipxe.x86_64-efi.ipxe | object | `{"enabled":true,"name":"ipxe.efi","url":"http://boot.ipxe.org/x86_64-efi/ipxe.efi"}` | x86_64 EFI iPXE binary (uses built-in iPXE NIC drivers). |
| ipxe.x86_64-efi.ipxe-legacy | object | `{"enabled":true,"name":"ipxe-legacy.efi","url":"http://boot.ipxe.org/x86_64-efi/ipxe-legacy.efi"}` | Legacy x86_64 EFI iPXE binary (no USB NIC drivers). |
| ipxe.x86_64-efi.ipxe-legacy.name | string | `"ipxe-legacy.efi"` | The name of the binary served on the TFTP server. |
| ipxe.x86_64-efi.ipxe-legacy.url | string | `"http://boot.ipxe.org/x86_64-efi/ipxe-legacy.efi"` | The URL to fetch the x86_64 EFI ipxe-legacy.efi binary from. |
| ipxe.x86_64-efi.ipxe.name | string | `"ipxe.efi"` | The name of the binary served on the TFTP server. |
| ipxe.x86_64-efi.ipxe.url | string | `"http://boot.ipxe.org/x86_64-efi/ipxe.efi"` | The URL to fetch the x86_64 EFI ipxe.efi binary from. |
| ipxe.x86_64-efi.prefix | string | `"x86_64-efi-"` | Prefixes for the TFTP filenames of x86_64 EFI binaries. Prevents clashing with other architectures. |
| ipxe.x86_64-efi.snponly | object | `{"enabled":true,"name":"snponly.efi","url":"http://boot.ipxe.org/x86_64-efi/snponly.efi"}` | x86_64 EFI iPXE binary with Simple Network Protocol. |
| ipxe.x86_64-efi.snponly.name | string | `"snponly.efi"` | The name of the binary served on the TFTP server. |
| ipxe.x86_64-efi.snponly.url | string | `"http://boot.ipxe.org/x86_64-efi/snponly.efi"` | The URL to fetch the x86_64 EFI snponly.efi binary from. |
| ipxeScripts | object | `{"http":{"default.ipxe":null,"enabled":true,"existingConfigMap":null},"tftp":{"autoexec.ipxe":"echo Chainloading default iPXE script from HTTP server... dhcp set conn_type http chain --autofree http://${next-server}/scripts/default.ipxe || echo HTTP failed, localbooting...","enabled":true,"existingConfigMap":null}}` | The scripts that will be exposed on the TFTP and HTTP servers. It's recommended to use extraFiles to add additional files to the TFTP server and only use this for iPXE scripts. Files here are not saved to persistent storage (if enabled) and by default are read-only mounted. |
| ipxeScripts.http | object | `{"default.ipxe":null,"enabled":true,"existingConfigMap":null}` | Scripts/files here will be exposed on the HTTP server. |
| ipxeScripts.http."default.ipxe" | string | nil | This is the default iPXE script that will be chainloaded from autoexec.ipxe on the TFTP server. |
| ipxeScripts.http.existingConfigMap | string | nil | This deploys the ConfigMap that will be used for the HTTP server's files (unless existingConfigMap is set) and mounts it to the pod. |
| ipxeScripts.tftp | object | `{"autoexec.ipxe":"echo Chainloading default iPXE script from HTTP server... dhcp set conn_type http chain --autofree http://${next-server}/scripts/default.ipxe || echo HTTP failed, localbooting...","enabled":true,"existingConfigMap":null}` | Scripts/files here will be exposed on the TFTP server. |
| ipxeScripts.tftp."autoexec.ipxe" | string | `"echo Chainloading default iPXE script from HTTP server... dhcp set conn_type http chain --autofree http://${next-server}/scripts/default.ipxe || echo HTTP failed, localbooting..."` | This is the default iPXE script that will be served from the TFTP server. It's recommended to keep this script as simple as possible (aka the default) and chainload another script from the HTTP server. |
| ipxeScripts.tftp.enabled | bool | `true` | This deploys the ConfigMap that will be used for the TFTP server's iPXE scripts/files (unless existingConfigMap is set) and mounts it to the pod. |
| ipxeScripts.tftp.existingConfigMap | string | nil | Supply an existing ConfigMap to use for the TFTP server's iPXE scripts/files. |
| livenessProbe.httpGet.path | string | `"/"` |  |
| livenessProbe.httpGet.port | string | `"http"` |  |
| nameOverride | string | `""` | This is to override the chart name. |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podLabels | object | `{}` |  |
| podSecurityContext.fsGroup | int | `2000` |  |
| readinessProbe.httpGet.path | string | `"/"` |  |
| readinessProbe.httpGet.port | string | `"http"` |  |
| replicaCount | int | `1` | The number of replicas to set for the deployment. |
| resources | object | `{}` |  |
| securityContext.capabilities.drop[0] | string | `"ALL"` |  |
| securityContext.readOnlyRootFilesystem | bool | `true` |  |
| securityContext.runAsNonRoot | bool | `true` |  |
| securityContext.runAsUser | int | `1000` |  |
| service.annotations | object | `{}` |  |
| service.clusterIP | string | `nil` |  |
| service.enabled | bool | `true` |  |
| service.externalIPs | string | `nil` |  |
| service.externalTrafficPolicy | string | `nil` |  |
| service.ipFamilies | string | `nil` |  |
| service.ipFamilyPolicy | string | `nil` |  |
| service.labels | object | `{}` |  |
| service.loadBalancerClass | string | `nil` |  |
| service.loadBalancerIP | string | `nil` |  |
| service.loadBalancerSourceRanges | list | `[]` |  |
| service.nodePort | string | `nil` |  |
| service.ports.http.port | int | `80` |  |
| service.ports.http.targetPort | int | `8080` |  |
| service.ports.tftp.port | int | `69` |  |
| service.ports.tftp.targetPort | int | `6969` |  |
| service.type | string | `"ClusterIP"` |  |
| storage.dataVolume.accessModes[0] | string | `"ReadWriteMany"` |  |
| storage.dataVolume.annotations | object | `{}` |  |
| storage.dataVolume.enabled | bool | `false` |  |
| storage.dataVolume.labels | object | `{}` |  |
| storage.dataVolume.size | string | `"1Gi"` |  |
| storage.dataVolume.storageClass | string | `nil` |  |
| storage.dataVolume.type | string | `"pvc"` | The type of storage to use for the TFTP and HTTP servers. pvc is recommended to prevent redownloading files from the internet every time the pod is restarted. |
| storage.mounts.containers.http.dataVolume.enabled | bool | `true` |  |
| storage.mounts.containers.http.dataVolume.path | string | `"/data/assets/http"` |  |
| storage.mounts.containers.http.dataVolume.readOnly | bool | `true` |  |
| storage.mounts.containers.http.dataVolume.subPath | string | `"/assets/http"` |  |
| storage.mounts.containers.http.httpScriptsConfig.enabled | bool | `true` |  |
| storage.mounts.containers.http.httpScriptsConfig.path | string | `"/scripts"` |  |
| storage.mounts.containers.http.httpScriptsConfig.readOnly | bool | `true` |  |
| storage.mounts.containers.tftp.dataVolume.enabled | bool | `true` |  |
| storage.mounts.containers.tftp.dataVolume.path | string | `"/data/assets/tftp"` |  |
| storage.mounts.containers.tftp.dataVolume.readOnly | bool | `true` |  |
| storage.mounts.containers.tftp.dataVolume.subPath | string | `"/assets/tftp"` |  |
| storage.mounts.containers.tftp.tftpScriptsConfig.enabled | bool | `true` |  |
| storage.mounts.containers.tftp.tftpScriptsConfig.path | string | `"/scripts"` |  |
| storage.mounts.containers.tftp.tftpScriptsConfig.readOnly | bool | `true` |  |
| storage.mounts.initContainers.initExtraFiles.dataVolume.enabled | bool | `true` |  |
| storage.mounts.initContainers.initExtraFiles.dataVolume.path | string | `"/data/assets"` |  |
| storage.mounts.initContainers.initExtraFiles.dataVolume.readOnly | bool | `false` |  |
| storage.mounts.initContainers.initExtraFiles.dataVolume.subPath | string | `"/assets"` |  |
| storage.mounts.initContainers.initiPXE.dataVolume.enabled | bool | `true` |  |
| storage.mounts.initContainers.initiPXE.dataVolume.path | string | `"/data/ipxe"` |  |
| storage.mounts.initContainers.initiPXE.dataVolume.readOnly | bool | `false` |  |
| storage.mounts.initContainers.initiPXE.dataVolume.subPath | string | `"/ipxe"` |  |
| tolerations | list | `[]` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)
