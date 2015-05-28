#### Envisalink_TPI ####
This project is to create a module for use with nodeJS applications that accept responses from the Envisalink server and provide a useful object for your custom client application.

This project uses the [Ademco TPI provided by Eyez-On](http://forum.eyez-on.com/FORUM/viewtopic.php?f=6&t=301).  It processes events from the Envisalink server and provides an easy object for node applications clients.

Credit goes to  [AlarmServer project for DSC panels](https://github.com/juggie/AlarmServer) and [MattTW/HoneyAlarmServer](https://github.com/MattTW/HoneyAlarmServer).

### How to ###

create a test.js file that contains:
```
var sys_res = require('ademco');
console.log(sys_res(process.argv[2]));
```
Then run it like this:
```
node test '%00,01,1C08,08,04, MCKAYCR SYSTEM Ready to Arm $'
```
The object returned will look like this:
```
{ type: 
   { name: 'Virtual Keypad Update',
     description: 'The panel wants to update the state of the keypad',
     handler: 'keypad_update' },
  partition: 'Partition: 01',
  icons: 'READY,AC PRESENT',
  numeric: '08',
  beeps: 'Coninuous Fast Beep (trouble/urgency)',
  msg: 'MCKAYS SYSTEM Ready to Arm',
  raw: '%00,01,1C08,08,04, MCKAYS SYSTEM Ready to Arm $' }
  ```
### WHATS NEXT ###

Register this as an NPM package

If anyone wants to help contribute a similar object for DSC systems that would be great.  I'd do it but I don't have the panel to play with.  The goal is to provide a module that anyone can pick up and use to build a more dynamic client application for the Envisalink like what I'm doing with my [EnvisaClient](https://github.com/mckaycr/envisaclient)

Also if you are building a client application, and you think my object could be structured better, I'm always open to suggestions.  I want this to use "industry wide" best practices, meaning I want this to easily be adapted for use in any home automation client applications.  If that even makes sense.
