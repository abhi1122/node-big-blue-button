# nodejs-bigbluebutton

## Install

```
$ npm install nodejs-bigbluebutton --save 
```
### Get BigBlueButton config details
Display the current security salt for the BigBlueButton API.

```
$ bbb-conf --secret
```


### Usage
```js
var bbb = require('nodejs-bigbluebutton');

bbb.salt = '';//Add Your salt key
bbb.url = ''; //Add Your Url
```

### Check 

```js
bbb.create(data, function (response) {
console.log(response);
});
```

### Create meeting on BBB

- `meetingId :- REQUIRED`
- `meetingName :- REQUIRED`
- `attendeePw :- Match this value in getJoinMeetingURL() to join as attendee.`
- `moderatorPw :- Match this value in getJoinMeetingURL() to join as moderator.`
- `welcomeMsg :- ''= use default. Change to customize.`
- `dialNumber :- The main number to call into. Optional.`
- `voiceBridge :- PIN to join voice. Optional.`
- `webVoice :- Alphanumeric to join voice. Optional.`
- `logoutUrl :- Default in bigbluebutton.properties. Optional.`
- `maxParticipants :- Optional. -1 = unlimitted. Not supported in BBB. [number]`
- `record :- New.true will tell BBB to record the meeting.`
- `duration :- Default = 0 which means no set duration in minutes. [number]`
- `meta_category :-Use to pass additional info to BBB server. See API docs.`

```js
data = {
        meetingID: 'a1',
        name: 'demo',
        attendeePW: '123',
        moderatorPW: '123',
        welcome: '123',
        dialNumber: '',
        voiceBridge: '',
        webVoice: '',
        logoutURL: '',
        maxParticipants: '-1',
        record: 'false',
        duration: '0',
        meta_category: ''
    };

bbb.create(data, function (response) {
        console.log(response);
});
```


### Join meeting 

- `meetingId  REQUIRED - We have to know which meeting to join.`
- `username REQUIRED - The user display name that will show in the BBB meeting.`
- `password REQUIRED - Must match either attendee or moderator pass for meeting.`
- `userId OPTIONAL - string`
- `webVoiceConf OPTIONAL - string`

```js
data = {
        meetingID: 'a1',
        fullName: 'demo',
        password: '123',
        userID: '',
        webVoiceConf: '',
    }


bbb.join(data, function (response) {
console.log(response);
}); 
```
if you want to join as moderator use moderator password else use attendee password

### Check meeting is running or not 

- `meetingId  REQUIRED - We have to know which meeting is running.`

```js
data = {
        meetingID: 'a1',
    }

bbb.running(data, function (response) {
console.log(response);
}); 
```
        

### Get meeting info 

- `meetingId  REQUIRED`

```js
data = {
        meetingID: 'a1'
    }

bbb.getMeetingInfo(data, function (response) {
console.log(response);
}); 
```


### Get recordings 

- `meetingId  REQUIRED`

```js
data = {
        meetingID: 'a1'
    }

bbb.getRecordings(data, function (response) {
console.log(response);
});
```


### Publish recordings 

- `meetingId  REQUIRED`
- `publish  REQUIRED true for publish false unpublish`

```js
data = {
        meetingID: 'a1',
        publish: true
    }

bbb.publishRecordings(data, function (response) {
console.log(response);
});
```


### Delete recordings

- `recordID  REQUIRED`

```js
data = {
        recordID: 'a1'
    }


bbb.deleteRecordings(data, function (response) {
        console.log(response);
});
```



### Update recordings

- `recordID  REQUIRED`
- `meta_Presenter `
- `meta_Presenter  `
- `meta_TERM `

```js
data = {
        recordID: 'a1',
        meta_Presenter: '',
        meta_Presenter:'',
        meta_TERM: ''

    };


    bbb.updateRecordings(data, function (response) {
        console.log(response);
    });
```



### End meeting

- `meetingID  REQUIRED`
- `password REQUIRED`

```js
    data = {
        meetingID: 'a1',
        password: '123'

    };


    bbb.end(data, function (response) {
        console.log(response);
    });
```
###BigBlueButton APIs
<http://docs.bigbluebutton.org/dev/api.html>



###Thanks