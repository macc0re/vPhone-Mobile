# vPhone Mobile

<p align="center">
  <strong>An experimental mobile userspace runtime and virtual environment for iOS and iPadOS.</strong>
  <br>
  Built by <strong>Mac.Core</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-iOS%20%7C%20iPadOS-6478ff?style=for-the-badge" alt="Platform">
  <img src="https://img.shields.io/badge/Language-Swift-orange?style=for-the-badge" alt="Swift">
  <img src="https://img.shields.io/badge/Status-Experimental-yellow?style=for-the-badge" alt="Experimental status">
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="MIT License">
</p>

---

## About

**vPhone Mobile** is an experimental project exploring a self-contained userspace environment for iOS and iPadOS. Its direction is inspired primarily by the ideas behind projects such as Nyxian and by practical experiences with environments such as Switchzart.

The long-term goal is to build a mobile runtime with its own process and service management, virtual filesystem, application environment, and compatibility components. The project will also investigate how supported jailbreak environments could integrate through separate adapters.

A Mac-hosted virtualization engine may be explored as an optional companion for workloads that require a full virtual machine. That is a separate path from the on-device userspace runtime.

**This project is experimental. It is not currently a full iOS virtual machine, hypervisor, or compatibility layer for arbitrary iOS applications.** No claim is made that stock iOS apps can run simply by copying their files into the runtime.

## Project history

This repository was originally developed as **iVM**.

### iVM — original direction

iVM began as an iOS and iPadOS virtual machine manager inspired by tools such as UTM. The original concept focused on a SwiftUI dashboard for creating and organizing virtual machine profiles, configuring guest machines, selecting ISO images, and eventually connecting those profiles to a virtualization backend.

The early app included interface prototypes for the VM dashboard, machine configuration, machine details, ISO selection, and settings. A working guest execution engine was not implemented.

### vPhone Mobile — current direction

The project has since been rethought and renamed **vPhone Mobile**. Instead of focusing only on managing conventional virtual machines, development is now centered on an on-device userspace runtime and compatibility environment, with Nyxian's general approach as a primary research reference.

The earlier iVM work remains part of the project's history and provides the starting point for its mobile application structure.

## Planned architecture

The architecture is being explored in separate components:

- **vPhone Mobile** — native SwiftUI interface for configuring and managing environments.
- **vPhone Runtime** — the on-device userspace runtime.
- **Process Manager** — experimental process lifecycle and isolation abstractions.
- **Virtual Filesystem** — a managed filesystem for runtime data and applications.
- **Service Layer** — runtime services and communication interfaces.
- **Application Environment** — app installation and execution experiments.
- **Compatibility Layer** — app-facing APIs and service implementations, developed incrementally.
- **Jailbreak Adapters** — optional integration points for compatible environments; not a jailbreak or exploit by themselves.
- **Mac Host Engine** — optional future companion for full virtual-machine workloads.

These are architectural goals, not a statement that every component is already implemented.

## Project status

vPhone Mobile is in **early experimental development**.

| Component | Status |
|---|---|
| SwiftUI application foundation | Existing prototype |
| Original iVM interface | Historical prototype |
| Runtime architecture | Research and design |
| Process management | Not implemented |
| Virtual filesystem | Not implemented |
| Runtime service layer | Not implemented |
| Application compatibility layer | Not implemented |
| Stock app ports | Research only |
| Jailbreak adapters | Planned; environment-dependent |
| Mac-hosted VM engine | Optional future research |
| Full guest OS virtualization | Not implemented |

## Compatibility and limitations

- **Platforms:** iOS and iPadOS
- **Language:** Swift
- **UI framework:** SwiftUI
- **Original app deployment target:** iOS 17.0+
- **Build system:** Xcode and GitHub Actions

The host operating system's sandbox, entitlements, available APIs, code-signing rules, and device hardware impose important limits. A userspace runtime does not replace the iOS kernel and does not automatically gain access to private frameworks, privileged services, or system entitlements.

Stock applications may depend on private frameworks, system daemons, entitlements, extensions, and other platform services. Supporting an application therefore requires individual compatibility work; copying an extracted `.app` or `.ipa` is not sufficient.

Jailbreak integration, where technically and legally appropriate, will remain isolated from the core runtime and will depend on the target device and environment.

## Building

### Using Xcode

1. Clone or download this repository.
2. Open the Xcode project in a compatible version of Xcode on a Mac.
3. Select the app scheme.
4. Choose an iOS Simulator destination.
5. Build and run the project.

### Using GitHub Actions

1. Open the repository's **Actions** tab.
2. Select the iOS build workflow.
3. Run the workflow or push a commit.
4. Download the artifacts after a successful build.

Simulator builds are intended for simulator testing. An unsigned IPA requires compatible signing before installation on a physical device. A successful app build does not mean the runtime features described in the roadmap are implemented.

## Roadmap

- [ ] Finalize the runtime architecture and module boundaries
- [ ] Separate the SwiftUI app from runtime logic
- [ ] Prototype runtime initialization and lifecycle management
- [ ] Design the virtual filesystem
- [ ] Implement a basic service registry and message interface
- [ ] Create a small test application for the runtime
- [ ] Research application compatibility requirements
- [ ] Evaluate a first limited app-porting experiment
- [ ] Design optional jailbreak adapter interfaces
- [ ] Evaluate a separate Mac-hosted virtualization companion
- [ ] Document tested devices, OS versions, and limitations

The roadmap may change as research and implementation progress.

## Contributing

Suggestions, bug reports, and contributions are welcome.

Before submitting a pull request:

1. Explain the issue or proposed improvement.
2. Keep changes focused and document platform-specific assumptions.
3. Do not describe planned or experimental features as implemented.
4. Verify that the app and its build workflow still compile.

## License

vPhone Mobile is distributed under the **MIT License**. See [`LICENSE`](LICENSE) for details.

---

<p align="center">
  Built with Swift by <strong>Mac.Clover</strong>
</p>
