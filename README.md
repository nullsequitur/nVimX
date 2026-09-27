# nViMx (Neovim Nix Verified Machine)

> **⚠️ WORK IN PROGRESS:** This project is currently under active development.
> See [roadmap.md](roadmap.md) for the project Epics, Tasks, and current implementation status.

nViMx is a skeleton key for software development. It is a single, declarative
Nix Flake that defines a highly tuned, modal, terminal-native workflow (Neovim,
Tmux, Zsh, Pi Agentic Harness) and compiles it into three distinct deployment
vectors.

With nViMx, your exact development environment travels with you and runs on any
machine, without requiring root access or host OS modifications.

## The Three Vectors

1. **The Physical Vector (Bare-Metal USB):** A raw NixOS disk image bootable via
   Ventoy. Bypasses the host OS entirely for full hardware access.
2. **The Virtual Vector (Portable Headless VM):** Runs directly on locked-down
   Windows, macOS, or Linux hosts via portable QEMU. Mounts the host filesystem
   seamlessly and exposes the environment over local SSH.
3. **The Network Vector (Single-File AppImage):** Bundles the entire
   `/nix/store` closure into a single executable `nViMx.AppImage`. `scp` it to
   any remote Linux server and drop into your workflow with zero installation.

## Tech Stack

- **Build System:** Nix Flakes
- **OS:** NixOS (for images) / Linux namespaces (for AppImage)
- **Virtualization:** QEMU (kvm/hvf/whpx) with `virtio-fs`
- **Workflow:** Neovim, Tmux, Zsh, Yazi, Ripgrep
- **AI Integration:** Pi Coding Agent

## License

MIT License. See `LICENSE` for details.
