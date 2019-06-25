# Philips TV Ambilight+Yeelight (Switch) Component 
#### ``` Work in Progress```

![Ambilight+Yeelight](https://github.com/jomwells/images/blob/master/ambilight+yeelight.jpg?raw=true)

This new (and pretty unrefined) component mimics surprisingly well the funtionality of Amilight+Hue with all Yeelight bulbs/lights using the Music Mode function from their API. The colour of the bulb is read constantly from the TV (jointspace), processed on the Home Assistant machine, and updates are pushed to the bulb in a loop until turned off. I'm sure it could be improved, so the code is commented, I encourage you to have a play with the values and check the links for more custom changes, if something else works better, or adds more features ill be happy to add them in for everyone. The values I've chosen are simply through trial and error. 

>### Potential Epilepsy Warning:
>At times when testing this component (usually when the TV is displaying an ambient light / no colour), the bulb is still updated rapidly and can cause a noticeable flicker - if you have Epilepsy this may not be for you. (Yet) If anyone can find more optimal values to solve this, I would be very grateful (see Lines 83, 314, 316 etc).

## Configuration

If you have not setup any other Philips TV components, use the tool linked in the [Ambilight (Light) component](https://github.com/jomwells/ambilights) docs to obtain your username and password.
```
switch:
  - platform: philips_ambilight+yeelight
    name: Lounge Lamp (Top Right) # (Name in Front-End)
    host: 192.168.1.XXX # (the TV)
    username: !secret philips_username
    password: !secret philips_password
    address: 192.168.1.XXX # (The Bulb)
    display_options: right-top
```

The per-bulb positions I have added (defined by ```display_options```) are as follows:

![Ambilight+Yeelight Positions](https://github.com/jomwells/images/blob/master/ambilight+yeelight_positions.jpg?raw=true)

> Note: 
> - I have not tested each and every one of these positions manually, if one of them doesn't seem right, assume it's my fault and let me know, they are quick fixes
> - As I do not have a TV with bottom ambilight LED's, I have not been able to test this part at all, although it should work in theory, please let me know if you have any success.

For a more custom position, different value calculations, or perhaps something different entirely, see the links in the code's comments. Understanding the 'topology' section [(JointSpace API)](http://jointspace.sourceforge.net/projectdata/documentation/jasonApi/1/doc/API.html) will go a long way to explaining how this part works.