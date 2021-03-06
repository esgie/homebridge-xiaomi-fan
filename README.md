# homebridge-xiaomi-fan

`homebridge-xiaomi-fan` is a plugin for Homebridge which allows you to control your Xiaomi Smartmi Fan! It should work with most smart fans from xiaomi.
The goal is to make the fan fully controllable from the native Homekit iOS app and Siri.

### Features
* Integrates into homekit as a fan device
* Control power, speed, swing mode and switch beetwen standard and natural wind
* Rotate fan to the left or right by 5°
* Turn on/off the buzzer
* Turn on/off the LEDs

## Installation

If you are new to Homebridge, please first read the Homebridge [documentation](https://www.npmjs.com/package/homebridge).
If you are running on a Raspberry, you will find a tutorial in the [homebridge-punt Wiki](https://github.com/cflurin/homebridge-punt/wiki/Running-Homebridge-on-a-Raspberry-Pi).

Install homebridge:
```sh
sudo npm install -g homebridge
```

Install homebridge-xiaomi-fan:
```sh
sudo npm install -g homebridge-xiaomi-fan
```

## Configuration

Add the accessory in `config.json` in your home directory inside `.homebridge`.

Example configuration:

```js
{
  "accessories": [
    {
      "accessory": "xiaomifan",
      "name": "Xiaomi Fan 2s",
      "ip": "192.168.0.40",
      "token": "8305d8fba83f94bb5ad8f963b6c84c84",
      "pollingInterval": 10,
      "moveControl": true,
      "buzzerControl": true,
      "ledControl": false
    }
  ]  
}
```

## Token

For the plugin to work the device token is required. For methods on how to find the token refer to this guide [obtaining mi device token](https://github.com/jghaanstra/com.xiaomi-miio/blob/master/docs/obtain_token.md).

### Configuration fields
- `accessory` [required]
Should always be "xiaomifan".
- `name` [required]
Name of your accessory.
- `ip` [required]
ip address of your Fan.
- `token` [required]
The device token of your Fan.
- `prefsDir` [optional]
The directory where the fan device info will be stored. **Default: "~/.xiaomiFan"**
- `pollingInterval` [optional]
The fan state background polling interval in seconds. **Default: 5**
- `moveControl` [optional]
Whether the move service is enabled. This allows to move the fan in 5° to the left or right. **Default: true**
- `buzzerControl` [optional]
Whether the buzzer service is enabled. This allows to turn on/off the fan buzzer. **Default: true**
- `ledControl` [optional]
Whether the led service is enabled. This allows to turn on/off the fan LED. **Default: true**
  
## Troubleshooting
If you have any issues with the plugin or fan services then you can run homebridge in debug mode, which will provide some additional information. This might be useful for debugging issues. 

Homebridge debug mode:
```sh
homebridge -D
```

## Special thanks
[miio](https://github.com/aholstenson/miio) - the Node.js remote control module for Xiaomi Mi devices.

[HAP-NodeJS](https://github.com/KhaosT/HAP-NodeJS) & [homebridge](https://github.com/nfarina/homebridge) - for making this possible.


