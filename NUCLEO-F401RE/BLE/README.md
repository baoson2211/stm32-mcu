# BLE

## X-NUCLEO-IDB05A1 Bluetooth Low Energy expansion board

==> **[STMicro's web site](https://www.st.com/en/ecosystems/x-nucleo-idb05a1.html)**


## Setup

```
   [Android smart phone]<--BLE-->[X-NUCLEO-IDB05A1][NUCLEO-F401RE]
```

## Template project for simple TX and RX

### Config on CubeMX

<img src="./doc/X-CUBE-BLE1.jpg" width=700>

<img src="./doc/X-CUBE-BLE1_2.jpg" width=700>

<img src="./doc/X-CUBE-BLE1_3.jpg" width=700>

### Code generated by X-CUBE-BLE1 with some modification

==> **[Code](./Template)**

This is a simpler version of [ApplicationSample](./ApplicationSample) project generated by "X-CUBE-BLE1/Application", but this one excludes dependencies on "X-CUBE-BLE1/Application".

Just use "X-CUBE-BLE1/Wireless" (w/o "X-CUBE-BLE1/Application") to generate a template, then do the following:

- Copy "inference_service.c" and "inference_service.h" from this project into the new project.
- Copy "app_x-cube-ble1.c" from this project into the new project (or cut & paste the code into the generated "app_x-cube-ble1.c").

Those codes include a minimal implementation of notifying (tx) an edge AI inference result to the central every second.

## Beacon (EddyStone)

### Note: let's study NFC tag instead of BLE-based beacon

BLE-based beacon will not come into wide use. Let's study NFC tag instead of beacon!

Reference: https://9to5google.com/2018/10/25/google-killing-location-notifications/

### Code generated by X-CUBE-BLE1

==> **[Code](./Beacon)**

### Changing the advertized URI

Modify the following part in :

eddystone_beacon.h
```
                       :
(Remove '//' to define EDDYSTONE_URL_BEACON_TYPE)
#define EDDYSTONE_BEACON_TYPE       (EDDYSTONE_URL_BEACON_TYPE) /* defined in configuration options */
                       :
#define PHYSICAL_WEB_URL            "goo.gl/viVrdi"
//#define PHYSICAL_WEB_URL            "www.st.com"

```

### Confirmation

Use [BLE Scanner](https://play.google.com/store/apps/details?id=com.macdom.ble.blescanner&hl=en) to read the URI.
