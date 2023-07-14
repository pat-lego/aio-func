# AN AIO Function

Welcome to my Adobe I/O Application!

## Setup

- `aio app init [PROJECT_FOLDER]`
- You dont have to pick a template you can just hit enter and skip a template
- Disable the UI and Event since we are just building an action
- Populate the `.env` file in the project root and fill it as shown [below](#env)

## Deploy & Cleanup

- `aio app deploy` to build and deploy all actions on Runtime and static files to CDN
- `aio app undeploy` to undeploy the app

## Invoke

- `aio rt action invoke aio-func/generic`

This will return an activation id which will look like this:

```
{
  "activationId": "7da508f26972416fa508f26972c16fc4"
}
```

## Invoke with Params

- `aio rt action invoke aio-func/generic --param name "Patrique"`

This will return an actication id, note in this scenario that we provided an input param to the params object within the main function which will be logged at a later point.

## List Activation

- `aio rt activation get [ACTIVATIONID]`

This `ACTIVATIONID` comes from the Invoke section and you can use that to see the result of your project

Example result:
```
{
  "actionHost": "10.152.169.245",
  "activationId": "7da508f26972416fa508f26972c16fc4",
  "annotations": [
    {
      "key": "path",
      "value": "35196-myfunc-stage/aio-func/generic"
    },
    {
      "key": "waitTime",
      "value": 3249
    },
    {
      "key": "kind",
      "value": "nodejs:16"
    },
    {
      "key": "timeout",
      "value": false
    },
    {
      "key": "limits",
      "value": {
        "concurrency": 200,
        "logs": 10,
        "memory": 256,
        "timeout": 60000
      }
    },
    {
      "key": "initTime",
      "value": 421
    }
  ],
  "duration": 426,
  "end": 1689361216617,
  "invokerInstanceId": {
    "instance": 3,
    "instanceType": "invoker",
    "uniqueName": "rt-invoker-3",
    "userMemory": "1500000000000000 B"
  },
  "logs": [],
  "name": "generic",
  "namespace": "35196-myfunc-stage",
  "podName": "wskrt-invoker-33-94731-35196myfuncstage-generic",
  "publish": false,
  "response": {
    "result": {
      "body": "My name is undefined",
      "statusCode": 200
    },
    "size": 48,
    "status": "success",
    "success": true
  },
  "start": 1689361216191,
  "subject": "35196-myfunc-stage",
  "version": "0.0.2"
}
```

## List the logs

- `aio rt activation logs [ACTIVATIONID]`

This will print the logs for the activation. Note that you need to have a logger in your code in order to see logs from the invocation.

## Config

### `.env`

You can generate this file using the command `aio app use`. 

```bash
# This file must **not** be committed to source control

## please provide your Adobe I/O Runtime credentials
# AIO_RUNTIME_AUTH=
# AIO_RUNTIME_NAMESPACE=
```

### `app.config.yaml`

- Main configuration file that defines an application's implementation. 
- More information on this file, application configuration, and extension configuration 
  can be found [here](https://developer.adobe.com/app-builder/docs/guides/appbuilder-configuration/#appconfigyaml)

## Project Location 

https://developer.adobe.com/console/projects/35196/4566206088344715307/overview