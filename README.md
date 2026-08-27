# Dialer & Messenger Analysis Workspace

This project contains the source code and architectural analysis for the Android Automotive OS (AAOS) Dialer and Messenger applications.

## Project Purpose
The goal of this workspace is to evaluate the integration between the Phone (Dialer) and Messaging modules to decide whether to maintain them as standalone applications or merge them into a single monolithic Phone app.

### Dialer Module
*   **Purpose**: Handles HFP (Hands-Free Profile) calling, contact management, and call history.
*   **Core Tech**: `InCallService`, `TelecomManager`, `car-telephony-common`.

### Messenger Module
*   **Purpose**: Handles SMS/MMS synchronization via Bluetooth MAP and provides a voice-optimized messaging interface.
*   **Core Tech**: `TelephonyProvider`, `car-messenger-common`.

---

## Directory Structure

```text
Dialer-Message-Analysis/
├── Dialer/                 # Main Phone/Dialer application source
│   ├── src/                # Java source code (com.android.car.dialer)
│   ├── res/                # Automotive-optimized resources
│   └── framework/          # Emulator and telephony framework stubs
├── Messenger/              # Main Messaging application source
│   ├── src/                # Java source code (com.android.car.messenger)
│   └── res/                # Messaging UI resources
└── libs/                   # Shared libraries and dependencies
    ├── car-ui-lib/         # Shared AAOS UI components
    ├── car-telephony-common/ # Shared contact/call-log data layer
    ├── car-messenger-common/ # Shared messaging POJOs and utils
    ├── car-apps-common/    # Shared automotive app utilities
    ├── car-uxr-client-lib/ # User Experience Restriction (UXR) management
    └── car-assist-lib/     # Assistant and Voice Interaction integration
```

## Developer Setup
1.  **Build System**: The project uses Gradle for local builds and supports `Android.bp` for AOSP integration.
2.  **Dependencies**: Most shared logic resides in the `libs/` directory. Ensure these are included in the build path.
3.  **Permissions**: Both apps require system-level permissions for Bluetooth and Telephony access.
