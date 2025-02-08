# References

## CAN Boat Protocol Documentation

For more information about the CAN Boat protocol, visit the following link:

[CAN Boat Protocol Documentation](https://canboat.github.io/canboat/canboat.html)

## Project Overview

This project is designed to emulate marine devices using the CAN Boat protocol. It includes various device-specific initialization files and scripts to simulate the behavior of these devices.

## Project Files

### emulate.js

### System Overview

- **Hardware**: Raspberry Pi 5 with MacArthur HAT
- **Software**: OpenPlotter, SignalK
- **Purpose**: Emulate a Simrad AC12 autopilot system that can interact with Raymarine autopilot commands

### Project Structure

```plaintext
/home/allan/RaymarineAPtoFakeNavicoAutoPilot/

```

The `emulate.js` file is responsible for initializing and emulating the device. It loads device-specific initialization information and sets up the default PGNs to transmit.

#### Key Sections

- **Loading Device-Specific Initialization**: The device-specific initialization file is loaded based on the command-line argument or defaults to 'AC12'.
- **Default Transmit PGNs**: The default PGNs to transmit are obtained from the device-specific initialization file.
- **Device Address**: The device address is obtained from the command-line argument.

```javascript
// filepath: /workspaces/RaymarineAPtoFakeNavicoAutoPilot/emulate.js
const debug = require('debug')('emulate')

var myArgs = process.argv.slice(2);
const emulate = myArgs[0] || 'AC12'
const emulate_init = './device/' + emulate + '.js'

// Load device specific init info
debug('Loading %s', emulate_init)
require(emulate_init)
const defaultTransmitPGNs = require(emulate_init).defaultTransmitPGNs
module.exports.defaultTransmitPGNs = defaultTransmitPGNs

const deviceAddress = myArgs[1];
//  const deviceAddress = require(emulate_init).deviceAddress;
module.exports.deviceAddress = deviceAddress;

debug('deviceAddress: %j', deviceAddress)
