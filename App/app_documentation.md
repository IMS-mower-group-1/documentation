
## The Android mowing app

The app can
- Control the mower manually from the app with a touch joystick.
- Start and stop an automated mowing session.
- Fetch the current position of the mower.
- Fetch the route of an mowing session.
- Fetch the pictures of objects the mower have avoided during its mowing sessions.

## Bluetooth Connectivity
The application uses the BluetoothManager and BluetoothAdapter classes to manage Bluetooth connectivity. The BluetoothManager class is used to obtain a reference to the BluetoothAdapter, which is used to scan for and connect to the mower device. And within the mower-app bluetooth connection you can control the mower manually and start or stop the automated mowing session. 

## Architecture
The application follows a  MVC (Model-View-Controller) architecture with the MainActivity class as the controller.

This is an Android application that involves Bluetooth communication with a robot mower. The architecture of the application involves four classes: MainActivity, PairNewDeviceActivity, PairNewDeviceViewModel, and BluetoothClient.

MainActivity is the entry point of the application, and it initializes the Bluetooth adapter and requests necessary permissions from the user. It also starts the PairNewDeviceActivity when the user clicks on the "connect" button.

PairNewDeviceActivity is responsible for pairing and connecting to a new Bluetooth device. It uses a PairNewDeviceViewModel to manage the discovery of new devices and previously paired devices. It also starts the MainActivity when a device is selected for connection.

PairNewDeviceViewModel contains the logic for discovering new devices and retrieving previously paired devices. It also handles the broadcast receiver for Bluetooth discovery events and stores the discovered devices in a LiveData object.

BluetoothClient handles the Bluetooth connection to the robot mower. It sends and receives messages to and from the mower through a Bluetooth socket.

These classes work together to allow the user to pair and connect to a robot mower via Bluetooth and communicate with it.

## API

The API requests are defined in the RoboMowApi interface, which is used to create a Retrofit service. The interface includes methods that correspond to the REST endpoints of the API. For example, the getPosition method is used to retrieve the position of a device. Retrofit generates an implementation of the interface that can be used to make API requests.
The requests that are in use are

- Get all mow sessions for a mower
- Get active mow session for a mower
- Start mow session for a mower
- End mow session for a mower
- Update position
- Get position
- Upload image
- Get image

All available api requests and more information about each one is found in [API endpoints.md](https://github.com/IMS-mower-group-1/documentation/blob/main/Backend/API%20endpoints.md)


## Permissions
The application requests permission to use Bluetooth on the device. If the Android version is 12 (Build.VERSION_CODES.S) or higher, the requestMultiplePermissions activity result launcher is used to request the BLUETOOTH_SCAN and BLUETOOTH_CONNECT permissions. Otherwise, the requestBluetooth activity result launcher is used to request the user to enable Bluetooth.

## Activity Result Launchers
The application uses activity result launchers to handle the results of activities that are started by the application. The requestBluetooth activity result launcher is used to handle the result of the Bluetooth enable request, and the requestMultiplePermissions activity result launcher is used to handle the result of the permission request.

