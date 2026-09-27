# nViMx Project Roadmap

This document tracks the implementation of the nViMx architecture.

## Status Overview
- **Project State:** 🟡 In Development

---

## 🏗 Epic 1: The Unified Core (Source of Truth)
Establish the Nix Flake and the shared development environment module that will be injected into all deployment vectors.

### Tasks
- [ ] **Task 1.1:** Initialize `flake.nix` with inputs (`nixpkgs`, `home-manager`, `nixos-generators`, `nix-appimage`).
- [ ] **Task 1.2:** Create `modules/dev-env.nix` (Zsh, Tmux, system packages).
- [ ] **Task 1.3:** Integrate Neovim configuration and Vim-mode bindings across all tools.
- [ ] **Task 1.4:** Package the Pi agentic harness (`@vandeepunk/pi-coding-agent`).

## 💾 Epic 2: The Physical Vector (Bare-Metal)
Generate the hardware-agnostic bootable images.

### Tasks
- [ ] **Task 2.1:** Define `modules/os-common.nix` (users, SSH daemon, networking).
- [ ] **Task 2.2:** Add `hardware.enableRedistributableFirmware = true` for universal Wi-Fi/Bluetooth.
- [ ] **Task 2.3:** Configure `nixos-generators` output for `x86_64-linux` (`.raw` format).
- [ ] **Task 2.4:** Configure cross-compilation/output for `aarch64-linux` (Apple Silicon).

## 🪟 Epic 3: The Virtual Vector (Headless QEMU)
Build the portable runners and host-filesystem integration for locked machines.

### Tasks
- [ ] **Task 3.1:** Add `modules/qemu-guest.nix` (VirtIO drivers, auto-mounting `virtio-fs`).
- [ ] **Task 3.2:** Write `scripts/run-vm.sh` for Linux/macOS hosts (detects KVM/HVF, sets up port 2222).
- [ ] **Task 3.3:** Write `scripts/run-vm.bat` for Windows hosts.
- [ ] **Task 3.4:** Source and bundle portable QEMU binaries for Windows (`.exe`) on the exFAT partition.

## 🌐 Epic 4: The Network Vector (AppImage)
Enable zero-install SSH deployments to remote Linux servers.

### Tasks
- [ ] **Task 4.1:** Configure `nix-appimage` in `flake.nix` to bundle `myDevEnv`.
- [ ] **Task 4.2:** Verify `bwrap` user-namespace fallback works on heavily restricted hosts.
- [ ] **Task 4.3:** Write deployment script (`scripts/deploy-remote.sh`) to automate `scp` and execution.

## 🧪 Epic 5: CI/CD and Verification
Automate the build and testing process.

### Tasks
- [ ] **Task 5.1:** Write a NixOS VM test to verify Tmux and SSH load correctly on boot.
- [ ] **Task 5.2:** Create a `Justfile` (or Makefile) for one-click artifact generation (`just build-all`).
- [ ] **Task 5.3:** Set up GitHub Actions to build the Flake and publish artifacts on release.
