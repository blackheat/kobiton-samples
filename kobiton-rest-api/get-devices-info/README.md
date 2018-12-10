# Kobiton "Getting device(s) information" sample code

Kobiton has provided sample script for utilizing Kobiton REST API `/devices` endpoint. The provided script demonstrates :
- [get-devices.js](./get-devices.js) :
  + Getting detailed information of `all` devices, including `private`, `favorite` and `cloud` devices.
  + Getting detailed information of devices which name contains the provided search string, including `private`, `favorite` and `cloud` devices.

> Note : 
> - The provided scripts are written in NodeJS. You can take a look at the provided script to view the flow, concepts and idea.
> - The flow, concepts and idea in the provided script can also be applied into other programming languages.

> More information about Kobiton REST API `/devices` endpoint can be found at https://api.kobiton.com/docs/#devices

## A. Preparations
### 1. Prerequisites
- cURL installed.
  - `Windows`: Visit https://curl.haxx.se/windows/ for instructions on how to download and install cURL on Windows.
  - `Linux`: cURL is installed by default in most Linux distributions. If not, please refer to corresponding distro instructions on how to download and install cURL.
  - `macOS`: cURL installed by default.

### 2. Getting Kobiton Username and API Key: 
Kobiton Username and API key are required for authenticating with Kobiton API.

> If you don't have a Kobiton account, visit https://portal.kobiton.com/register to create one.

To get your Kobiton Username and API Key, follow instructions at `IV. Configure Test Script for Kobiton` section on [our blog](https://kobiton.com/blog/tutorial/parallel-testing-selenium-webdriver/).

## B. Samples

In this section, we will be providing sample use cases for `/devices` endpoint using bash commands with cURL.
> For more information about Kobiton REST APIs and their usages, visit [Kobiton REST API Documentation](https://api.kobiton.com/docs/).

### B.1 Getting devices information
- When execute the commands provided in this section, remember to replace these variables with your values:
  - `<YOUR_KOBITON_USERNAME>`: Your Kobiton Username.
  - `<YOUR_KOBITON_API_KEY>`: Your Kobiton API Key.
  - `<YOUR_GROUP_ID>`: Your group ID.

- Expected output for all samples in this section:
```javascript
{"privateDevices":[...],"favoriteDevices":[...],"cloudDevices":[...]}
```

#### B.1.1 Getting all devices
- User has no organization and no group:
```bash
curl -X GET 'https://api.kobiton.com/v1/devices' \
  -H 'Accept: application/json' \
  -u <YOUR_KOBITON_USERNAME>:<YOUR_KOBITON_API_KEY>
```

Example:
```bash
curl -X GET 'https://api.kobiton.com/v1/devices' \
  -H 'Accept: application/json' \
  -u kobitondemo:4bbaa732-d920-4de2-a93b-43f2369f478d
```

- User has organization and in group(s):
```bash
curl -X GET 'https://api.kobiton.com/v1/devices?groupID=<YOUR_GROUP_ID>' \
  -H 'Accept: application/json' \
  -u <YOUR_KOBITON_USERNAME>:<YOUR_KOBITON_API_KEY>
```

Example:
```bash
curl -X GET 'https://api.kobiton.com/v1/devices?groupId=260' \
  -H 'Accept: application/json' \
  -u kobitondemo:4bbaa732-d920-4de2-a93b-43f2369f478d
```

#### B.1.2 Getting online devices
- User has no organization and no group:
```bash
curl -X GET 'https://api.kobiton.com/v1/devices?isOnline=true' \
  -H 'Accept: application/json' \
  -u <YOUR_KOBITON_USERNAME>:<YOUR_KOBITON_API_KEY>
```

Example:
```bash
curl -X GET 'https://api.kobiton.com/v1/devices?isOnline=true' \
  -H 'Accept: application/json' \
  -u kobitondemo:4bbaa732-d920-4de2-a93b-43f2369f478d
```

- User has organization and in group(s):
```bash
curl -X GET 'https://api.kobiton.com/v1/devices?groupID=<YOUR_GROUP_ID>&isOnline=true' \
  -H 'Accept: application/json' \
  -u <YOUR_KOBITON_USERNAME>:<YOUR_KOBITON_API_KEY>
```

Example:
```bash
curl -X GET 'https://api.kobiton.com/v1/devices?groupId=260&isOnline=true' \
  -H 'Accept: application/json' \
  -u kobitondemo:4bbaa732-d920-4de2-a93b-43f2369f478d
```

### B.1.3 Getting online Android devices
- User has no organization and no group:
```bash
curl -X GET 'https://api.kobiton.com/v1/devices?platformName=Android&isOnline=true' \
  -H 'Accept: application/json' \
  -u <YOUR_KOBITON_USERNAME>:<YOUR_KOBITON_API_KEY>
```

Example:
```bash
curl -X GET 'https://api.kobiton.com/v1/devices?platformName=Android&isOnline=true' \
  -H 'Accept: application/json' \
  -u kobitondemo:4bbaa732-d920-4de2-a93b-43f2369f478d
```

- User has organization and in group(s):
```bash
curl -X GET 'https://api.kobiton.com/v1/devices?groupID=<YOUR_GROUP_ID>&platformName=Android&isOnline=true' \
  -H 'Accept: application/json' \
  -u <YOUR_KOBITON_USERNAME>:<YOUR_KOBITON_API_KEY>
```

Example:
```bash
curl -X GET 'https://api.kobiton.com/v1/devices?groupId=260&platformName=Android&isOnline=true' \
  -H 'Accept: application/json' \
  -u kobitondemo:4bbaa732-d920-4de2-a93b-43f2369f478d
```

### B.1.4 Getting information of online Galaxy S8 running Android 7.0
- User has no organization and no group:
```bash
curl -X GET 'https://api.kobiton.com/v1/devices?deviceName=Galaxy%20S8&platformName=Android&isOnline=true' \
  -H 'Accept: application/json' \
  -u <YOUR_KOBITON_USERNAME>:<YOUR_KOBITON_API_KEY>
```

Example:
```bash
curl -X GET 'https://api.kobiton.com/v1/devices?deviceName=Galaxy%20S8&platformName=Android&isOnline=true' \
  -H 'Accept: application/json' \
  -u kobitondemo:4bbaa732-d920-4de2-a93b-43f2369f478d
```

- User has no organization and no group:
```bash
curl -X GET 'https://api.kobiton.com/v1/devices?groupID=<YOUR_GROUP_ID>&deviceName=Galaxy%20S8&platformName=Android&isOnline=true' \
  -H 'Accept: application/json' \
  -u <YOUR_KOBITON_USERNAME>:<YOUR_KOBITON_API_KEY>
```

Example:
```bash
curl -X GET 'https://api.kobiton.com/v1/devices?groupId=260&deviceName=Galaxy%20S8&platformName=Android&isOnline=true' \
  -H 'Accept: application/json' \
  -u kobitondemo:4bbaa732-d920-4de2-a93b-43f2369f478d
```
