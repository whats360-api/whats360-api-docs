# Code examples per endpoint

Generated from the documented parameters in [api-reference.md](api-reference.md). Placeholders only. **Not executed against the live API.** PHP samples were not run at all. Use a test device. `disconnect` and `delete` change device state.

`instance_id` is omitted from `instances` (list) and `instances/create`, as documented.

## Send text
`GET /send-text`  Parameters: token, instance_id, jid, msg

```bash
curl "https://whats360.live/api/v1/send-text?token=YOUR_TOKEN&instance_id=DEVICE_ID&jid=201234567890@s.whatsapp.net&msg=Hello"
```

```php
<?php
$q = http_build_query([
  'token' => 'YOUR_TOKEN',
  'instance_id' => 'DEVICE_ID',
  'jid' => '201234567890@s.whatsapp.net',
  'msg' => 'Hello'
]);
$ch = curl_init('https://whats360.live/api/v1/send-text?' . $q);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
echo curl_exec($ch);
```

```javascript
const q = new URLSearchParams({
  token: 'YOUR_TOKEN',
  instance_id: 'DEVICE_ID',
  jid: '201234567890@s.whatsapp.net',
  msg: 'Hello',
});
const res = await fetch(`https://whats360.live/api/v1/send-text?${q}`, { method: 'GET' });
console.log(res.status, await res.text());
```

```python
import urllib.parse, urllib.request
q = urllib.parse.urlencode({
    "token": "YOUR_TOKEN",
    "instance_id": "DEVICE_ID",
    "jid": "201234567890@s.whatsapp.net",
    "msg": "Hello",
})
req = urllib.request.Request(f"https://whats360.live/api/v1/send-text?{q}", method="GET")
print(urllib.request.urlopen(req).read().decode())
```

## Send image
`GET /send-image`  Parameters: token, instance_id, jid, imageurl, caption?

```bash
curl "https://whats360.live/api/v1/send-image?token=YOUR_TOKEN&instance_id=DEVICE_ID&jid=201234567890@s.whatsapp.net&imageurl=https://example.com/image.jpg"
```

```php
<?php
$q = http_build_query([
  'token' => 'YOUR_TOKEN',
  'instance_id' => 'DEVICE_ID',
  'jid' => '201234567890@s.whatsapp.net',
  'imageurl' => 'https://example.com/image.jpg'
]);
$ch = curl_init('https://whats360.live/api/v1/send-image?' . $q);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
echo curl_exec($ch);
```

```javascript
const q = new URLSearchParams({
  token: 'YOUR_TOKEN',
  instance_id: 'DEVICE_ID',
  jid: '201234567890@s.whatsapp.net',
  imageurl: 'https://example.com/image.jpg',
});
const res = await fetch(`https://whats360.live/api/v1/send-image?${q}`, { method: 'GET' });
console.log(res.status, await res.text());
```

```python
import urllib.parse, urllib.request
q = urllib.parse.urlencode({
    "token": "YOUR_TOKEN",
    "instance_id": "DEVICE_ID",
    "jid": "201234567890@s.whatsapp.net",
    "imageurl": "https://example.com/image.jpg",
})
req = urllib.request.Request(f"https://whats360.live/api/v1/send-image?{q}", method="GET")
print(urllib.request.urlopen(req).read().decode())
```

## Send video
`GET /send-video`  Parameters: token, instance_id, jid, videourl, caption?

```bash
curl "https://whats360.live/api/v1/send-video?token=YOUR_TOKEN&instance_id=DEVICE_ID&jid=201234567890@s.whatsapp.net&videourl=https://example.com/video.mp4"
```

```php
<?php
$q = http_build_query([
  'token' => 'YOUR_TOKEN',
  'instance_id' => 'DEVICE_ID',
  'jid' => '201234567890@s.whatsapp.net',
  'videourl' => 'https://example.com/video.mp4'
]);
$ch = curl_init('https://whats360.live/api/v1/send-video?' . $q);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
echo curl_exec($ch);
```

```javascript
const q = new URLSearchParams({
  token: 'YOUR_TOKEN',
  instance_id: 'DEVICE_ID',
  jid: '201234567890@s.whatsapp.net',
  videourl: 'https://example.com/video.mp4',
});
const res = await fetch(`https://whats360.live/api/v1/send-video?${q}`, { method: 'GET' });
console.log(res.status, await res.text());
```

```python
import urllib.parse, urllib.request
q = urllib.parse.urlencode({
    "token": "YOUR_TOKEN",
    "instance_id": "DEVICE_ID",
    "jid": "201234567890@s.whatsapp.net",
    "videourl": "https://example.com/video.mp4",
})
req = urllib.request.Request(f"https://whats360.live/api/v1/send-video?{q}", method="GET")
print(urllib.request.urlopen(req).read().decode())
```

## Send audio
`GET /send-audio`  Parameters: token, instance_id, jid, audiourl

```bash
curl "https://whats360.live/api/v1/send-audio?token=YOUR_TOKEN&instance_id=DEVICE_ID&jid=201234567890@s.whatsapp.net&audiourl=https://example.com/audio.mp3"
```

```php
<?php
$q = http_build_query([
  'token' => 'YOUR_TOKEN',
  'instance_id' => 'DEVICE_ID',
  'jid' => '201234567890@s.whatsapp.net',
  'audiourl' => 'https://example.com/audio.mp3'
]);
$ch = curl_init('https://whats360.live/api/v1/send-audio?' . $q);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
echo curl_exec($ch);
```

```javascript
const q = new URLSearchParams({
  token: 'YOUR_TOKEN',
  instance_id: 'DEVICE_ID',
  jid: '201234567890@s.whatsapp.net',
  audiourl: 'https://example.com/audio.mp3',
});
const res = await fetch(`https://whats360.live/api/v1/send-audio?${q}`, { method: 'GET' });
console.log(res.status, await res.text());
```

```python
import urllib.parse, urllib.request
q = urllib.parse.urlencode({
    "token": "YOUR_TOKEN",
    "instance_id": "DEVICE_ID",
    "jid": "201234567890@s.whatsapp.net",
    "audiourl": "https://example.com/audio.mp3",
})
req = urllib.request.Request(f"https://whats360.live/api/v1/send-audio?{q}", method="GET")
print(urllib.request.urlopen(req).read().decode())
```

## Send document
`GET /send-doc`  Parameters: token, instance_id, jid, docurl, caption?

```bash
curl "https://whats360.live/api/v1/send-doc?token=YOUR_TOKEN&instance_id=DEVICE_ID&jid=201234567890@s.whatsapp.net&docurl=https://example.com/file.pdf"
```

```php
<?php
$q = http_build_query([
  'token' => 'YOUR_TOKEN',
  'instance_id' => 'DEVICE_ID',
  'jid' => '201234567890@s.whatsapp.net',
  'docurl' => 'https://example.com/file.pdf'
]);
$ch = curl_init('https://whats360.live/api/v1/send-doc?' . $q);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
echo curl_exec($ch);
```

```javascript
const q = new URLSearchParams({
  token: 'YOUR_TOKEN',
  instance_id: 'DEVICE_ID',
  jid: '201234567890@s.whatsapp.net',
  docurl: 'https://example.com/file.pdf',
});
const res = await fetch(`https://whats360.live/api/v1/send-doc?${q}`, { method: 'GET' });
console.log(res.status, await res.text());
```

```python
import urllib.parse, urllib.request
q = urllib.parse.urlencode({
    "token": "YOUR_TOKEN",
    "instance_id": "DEVICE_ID",
    "jid": "201234567890@s.whatsapp.net",
    "docurl": "https://example.com/file.pdf",
})
req = urllib.request.Request(f"https://whats360.live/api/v1/send-doc?{q}", method="GET")
print(urllib.request.urlopen(req).read().decode())
```

## List devices
`GET /instances`  Parameters: token

```bash
curl "https://whats360.live/api/v1/instances?token=YOUR_TOKEN"
```

```php
<?php
$q = http_build_query([
  'token' => 'YOUR_TOKEN'
]);
$ch = curl_init('https://whats360.live/api/v1/instances?' . $q);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
echo curl_exec($ch);
```

```javascript
const q = new URLSearchParams({
  token: 'YOUR_TOKEN',
});
const res = await fetch(`https://whats360.live/api/v1/instances?${q}`, { method: 'GET' });
console.log(res.status, await res.text());
```

```python
import urllib.parse, urllib.request
q = urllib.parse.urlencode({
    "token": "YOUR_TOKEN",
})
req = urllib.request.Request(f"https://whats360.live/api/v1/instances?{q}", method="GET")
print(urllib.request.urlopen(req).read().decode())
```

## Create device
`GET /instances/create`  Parameters: token, id, name?

```bash
curl "https://whats360.live/api/v1/instances/create?token=YOUR_TOKEN&id=new-device"
```

```php
<?php
$q = http_build_query([
  'token' => 'YOUR_TOKEN',
  'id' => 'new-device'
]);
$ch = curl_init('https://whats360.live/api/v1/instances/create?' . $q);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
echo curl_exec($ch);
```

```javascript
const q = new URLSearchParams({
  token: 'YOUR_TOKEN',
  id: 'new-device',
});
const res = await fetch(`https://whats360.live/api/v1/instances/create?${q}`, { method: 'GET' });
console.log(res.status, await res.text());
```

```python
import urllib.parse, urllib.request
q = urllib.parse.urlencode({
    "token": "YOUR_TOKEN",
    "id": "new-device",
})
req = urllib.request.Request(f"https://whats360.live/api/v1/instances/create?{q}", method="GET")
print(urllib.request.urlopen(req).read().decode())
```

## Connect device
`GET /instances/connect`  Parameters: token, instance_id

```bash
curl "https://whats360.live/api/v1/instances/connect?token=YOUR_TOKEN&instance_id=DEVICE_ID"
```

```php
<?php
$q = http_build_query([
  'token' => 'YOUR_TOKEN',
  'instance_id' => 'DEVICE_ID'
]);
$ch = curl_init('https://whats360.live/api/v1/instances/connect?' . $q);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
echo curl_exec($ch);
```

```javascript
const q = new URLSearchParams({
  token: 'YOUR_TOKEN',
  instance_id: 'DEVICE_ID',
});
const res = await fetch(`https://whats360.live/api/v1/instances/connect?${q}`, { method: 'GET' });
console.log(res.status, await res.text());
```

```python
import urllib.parse, urllib.request
q = urllib.parse.urlencode({
    "token": "YOUR_TOKEN",
    "instance_id": "DEVICE_ID",
})
req = urllib.request.Request(f"https://whats360.live/api/v1/instances/connect?{q}", method="GET")
print(urllib.request.urlopen(req).read().decode())
```

## Disconnect device
`GET /instances/disconnect`  Parameters: token, instance_id

```bash
curl "https://whats360.live/api/v1/instances/disconnect?token=YOUR_TOKEN&instance_id=DEVICE_ID"
```

```php
<?php
$q = http_build_query([
  'token' => 'YOUR_TOKEN',
  'instance_id' => 'DEVICE_ID'
]);
$ch = curl_init('https://whats360.live/api/v1/instances/disconnect?' . $q);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
echo curl_exec($ch);
```

```javascript
const q = new URLSearchParams({
  token: 'YOUR_TOKEN',
  instance_id: 'DEVICE_ID',
});
const res = await fetch(`https://whats360.live/api/v1/instances/disconnect?${q}`, { method: 'GET' });
console.log(res.status, await res.text());
```

```python
import urllib.parse, urllib.request
q = urllib.parse.urlencode({
    "token": "YOUR_TOKEN",
    "instance_id": "DEVICE_ID",
})
req = urllib.request.Request(f"https://whats360.live/api/v1/instances/disconnect?{q}", method="GET")
print(urllib.request.urlopen(req).read().decode())
```

## Device status
`GET /instances/status`  Parameters: token, instance_id

```bash
curl "https://whats360.live/api/v1/instances/status?token=YOUR_TOKEN&instance_id=DEVICE_ID"
```

```php
<?php
$q = http_build_query([
  'token' => 'YOUR_TOKEN',
  'instance_id' => 'DEVICE_ID'
]);
$ch = curl_init('https://whats360.live/api/v1/instances/status?' . $q);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
echo curl_exec($ch);
```

```javascript
const q = new URLSearchParams({
  token: 'YOUR_TOKEN',
  instance_id: 'DEVICE_ID',
});
const res = await fetch(`https://whats360.live/api/v1/instances/status?${q}`, { method: 'GET' });
console.log(res.status, await res.text());
```

```python
import urllib.parse, urllib.request
q = urllib.parse.urlencode({
    "token": "YOUR_TOKEN",
    "instance_id": "DEVICE_ID",
})
req = urllib.request.Request(f"https://whats360.live/api/v1/instances/status?{q}", method="GET")
print(urllib.request.urlopen(req).read().decode())
```

## QR code (JSON)
`GET /instances/qr`  Parameters: token, instance_id

```bash
curl "https://whats360.live/api/v1/instances/qr?token=YOUR_TOKEN&instance_id=DEVICE_ID"
```

```php
<?php
$q = http_build_query([
  'token' => 'YOUR_TOKEN',
  'instance_id' => 'DEVICE_ID'
]);
$ch = curl_init('https://whats360.live/api/v1/instances/qr?' . $q);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
echo curl_exec($ch);
```

```javascript
const q = new URLSearchParams({
  token: 'YOUR_TOKEN',
  instance_id: 'DEVICE_ID',
});
const res = await fetch(`https://whats360.live/api/v1/instances/qr?${q}`, { method: 'GET' });
console.log(res.status, await res.text());
```

```python
import urllib.parse, urllib.request
q = urllib.parse.urlencode({
    "token": "YOUR_TOKEN",
    "instance_id": "DEVICE_ID",
})
req = urllib.request.Request(f"https://whats360.live/api/v1/instances/qr?{q}", method="GET")
print(urllib.request.urlopen(req).read().decode())
```

## Delete device
`GET /instances/delete`  Parameters: token, instance_id

```bash
curl "https://whats360.live/api/v1/instances/delete?token=YOUR_TOKEN&instance_id=DEVICE_ID"
```

```php
<?php
$q = http_build_query([
  'token' => 'YOUR_TOKEN',
  'instance_id' => 'DEVICE_ID'
]);
$ch = curl_init('https://whats360.live/api/v1/instances/delete?' . $q);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
echo curl_exec($ch);
```

```javascript
const q = new URLSearchParams({
  token: 'YOUR_TOKEN',
  instance_id: 'DEVICE_ID',
});
const res = await fetch(`https://whats360.live/api/v1/instances/delete?${q}`, { method: 'GET' });
console.log(res.status, await res.text());
```

```python
import urllib.parse, urllib.request
q = urllib.parse.urlencode({
    "token": "YOUR_TOKEN",
    "instance_id": "DEVICE_ID",
})
req = urllib.request.Request(f"https://whats360.live/api/v1/instances/delete?{q}", method="GET")
print(urllib.request.urlopen(req).read().decode())
```

## List campaigns
`GET /campaigns`  Parameters: token, instance_id

```bash
curl "https://whats360.live/api/v1/campaigns?token=YOUR_TOKEN&instance_id=DEVICE_ID"
```

```php
<?php
$q = http_build_query([
  'token' => 'YOUR_TOKEN',
  'instance_id' => 'DEVICE_ID'
]);
$ch = curl_init('https://whats360.live/api/v1/campaigns?' . $q);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
echo curl_exec($ch);
```

```javascript
const q = new URLSearchParams({
  token: 'YOUR_TOKEN',
  instance_id: 'DEVICE_ID',
});
const res = await fetch(`https://whats360.live/api/v1/campaigns?${q}`, { method: 'GET' });
console.log(res.status, await res.text());
```

```python
import urllib.parse, urllib.request
q = urllib.parse.urlencode({
    "token": "YOUR_TOKEN",
    "instance_id": "DEVICE_ID",
})
req = urllib.request.Request(f"https://whats360.live/api/v1/campaigns?{q}", method="GET")
print(urllib.request.urlopen(req).read().decode())
```

## Start campaign
`POST /campaigns/start`  Parameters: token, instance_id, campaign_id

```bash
curl -X POST "https://whats360.live/api/v1/campaigns/start?token=YOUR_TOKEN&instance_id=DEVICE_ID&campaign_id=CAMPAIGN_ID"
```

```php
<?php
$q = http_build_query([
  'token' => 'YOUR_TOKEN',
  'instance_id' => 'DEVICE_ID',
  'campaign_id' => 'CAMPAIGN_ID'
]);
$ch = curl_init('https://whats360.live/api/v1/campaigns/start?' . $q);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_POST, true);
echo curl_exec($ch);
```

```javascript
const q = new URLSearchParams({
  token: 'YOUR_TOKEN',
  instance_id: 'DEVICE_ID',
  campaign_id: 'CAMPAIGN_ID',
});
const res = await fetch(`https://whats360.live/api/v1/campaigns/start?${q}`, { method: 'POST' });
console.log(res.status, await res.text());
```

```python
import urllib.parse, urllib.request
q = urllib.parse.urlencode({
    "token": "YOUR_TOKEN",
    "instance_id": "DEVICE_ID",
    "campaign_id": "CAMPAIGN_ID",
})
req = urllib.request.Request(f"https://whats360.live/api/v1/campaigns/start?{q}", method="POST")
print(urllib.request.urlopen(req).read().decode())
```

## Campaign status
`GET /campaigns/status`  Parameters: token, instance_id, campaign_id

```bash
curl "https://whats360.live/api/v1/campaigns/status?token=YOUR_TOKEN&instance_id=DEVICE_ID&campaign_id=CAMPAIGN_ID"
```

```php
<?php
$q = http_build_query([
  'token' => 'YOUR_TOKEN',
  'instance_id' => 'DEVICE_ID',
  'campaign_id' => 'CAMPAIGN_ID'
]);
$ch = curl_init('https://whats360.live/api/v1/campaigns/status?' . $q);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
echo curl_exec($ch);
```

```javascript
const q = new URLSearchParams({
  token: 'YOUR_TOKEN',
  instance_id: 'DEVICE_ID',
  campaign_id: 'CAMPAIGN_ID',
});
const res = await fetch(`https://whats360.live/api/v1/campaigns/status?${q}`, { method: 'GET' });
console.log(res.status, await res.text());
```

```python
import urllib.parse, urllib.request
q = urllib.parse.urlencode({
    "token": "YOUR_TOKEN",
    "instance_id": "DEVICE_ID",
    "campaign_id": "CAMPAIGN_ID",
})
req = urllib.request.Request(f"https://whats360.live/api/v1/campaigns/status?{q}", method="GET")
print(urllib.request.urlopen(req).read().decode())
```
