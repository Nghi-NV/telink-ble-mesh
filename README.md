# TelinkBleMeshLib

## Introduction

TelinkBleMeshLib is an Android library for communication and management of Bluetooth Mesh devices based on the Telink platform. This library provides a complete API set to interact with Bluetooth Mesh devices, perform device provisioning, configuration, and control devices in the mesh network.

## Requirements

- Android SDK 23 or above (Android 6.0+)
- Device with Bluetooth 4.0 or above support

## Features

- Scan and connect to Bluetooth Mesh devices
- Device provisioning
- Mesh network management
- Mesh device configuration
- Control devices through Mesh messages
- Support for Bluetooth SIG standard models
- End-to-end encryption and security according to Mesh standards

## Library Structure

The library is organized into the following main packages:

- `com.telink.ble.mesh.core`: Provides core Bluetooth Mesh functionality
- `com.telink.ble.mesh.entity`: Data objects and models
- `com.telink.ble.mesh.foundation`: Basic and foundation classes
- `com.telink.ble.mesh.util`: Utilities and support tools

## Installation

Add JitPack repository to your project-level build.gradle file:

```gradle
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```

Add the library to your module's build.gradle file:

```gradle
dependencies {
    implementation 'com.github.telink-semi:telink-ble-mesh:3.3.2'
}
```

## Usage

### Library Initialization

```java
// Initialize in Application or main Activity
MeshService.getInstance().init(context);
```

### Device Scanning

```java
// Set up scanning callback
MeshService.getInstance().registerMeshScannerCallback(new MeshScannerCallback() {
    @Override
    public void onDeviceFound(BluetoothDevice device, int rssi, byte[] scanRecord) {
        // Handle found device
    }
});

// Start scanning
MeshService.getInstance().startScan();
```

### Device Provisioning

```java
// Set up provisioning callback
MeshService.getInstance().registerProvisioningCallback(new ProvisioningCallback() {
    @Override
    public void onProvisioningComplete(ProvisioningEvent event) {
        // Handle provisioning completion
    }

    @Override
    public void onProvisioningFailed(ProvisioningEvent event) {
        // Handle provisioning failure
    }
});

// Start provisioning
ProvisioningParameters parameters = new ProvisioningParameters();
// Set parameters
MeshService.getInstance().startProvisioning(parameters);
```

### Sending Control Messages

```java
// Create message to control device
MeshMessage message = OnOffSetMessage.getSimple(address, appKeyIndex, isOn, true, 0);
MeshService.getInstance().sendMeshMessage(message);
```

## License

This library is distributed under the [Open] license. See the LICENSE file for more details.

