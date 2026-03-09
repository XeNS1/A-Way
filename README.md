# A-Way (Termux:Wayland)

A-Way is a high-performance, research-backed Wayland companion for Android, designed to provide a seamless Wayland session for Termux environments without requiring root privileges.

## 🏗 Architecture

Unlike traditional monolithic solutions, **A-Way** uses a decoupled process model inspired by the core lessons of `termux-x11`:

1.  **The Shell-Side (Backend):** A Rust-based core launched via `app_process` within the Termux context. It owns the `wayland-0` Unix socket, ensuring native performance and proper permissions for Termux clients.
2.  **The Android App (Frontend):** A modern Material You (M3) interface that handles the rendering surface (`SurfaceView`), system input events, and lifecycle management.

These processes communicate over a high-speed Binder/AIDL handshake and a dedicated control channel.

## ✨ Features (In Progress)

- **Native Rust Core:** Leverages Rust's safety and speed for the compositor logic.
- **Material You UI:** Fully adaptive Android 12+ interface for configuration.
- **Decoupled Input:** Low-latency pointer and keyboard event forwarding.
- **DataStore Config:** Reactive settings management that feeds directly into the runtime.
- **Zero-Root:** Works entirely within the user-space.

## 🛠 Tech Stack

- **Backend:** Rust, Smithay (planned), Unix Domain Sockets.
- **Frontend:** Kotlin, Jetpack Compose / Material 3, DataStore.
- **Glue:** JNI, Binder (AIDL), `app_process`.

## 🚧 Status: MVP Skeleton

This project is currently in the **active research & MVP stage**. The core IPC mechanism, process loading, and basic session management are implemented. Real-time buffer swap and full protocol dispatching are next on the roadmap.

## 📄 License

This project is licensed under the [MIT License](LICENSE).
