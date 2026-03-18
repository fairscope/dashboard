# dashboard

This is the [Node-RED](https://nodered.org/) project for the [PlanktoScope](https://www.planktoscope.org/).

## URLs

[/ps/node-red-v2/dashboard/](http://planktoscope.local/ps/node-red-v2/dashboard/) to access the dashboard
[/admin/ps/node-red-v2/](http://planktoscope.local/admin/ps/node-red-v2/) to access the Node-RED editor

## Development

Follow [Development Environment](https://github.com/fairscope/PlanktoScope/blob/main/documentation/docs/community/contribute/tips-and-tricks.md#development-environment)

You should then be able to commit and push to the dashboard repository.

⚠️ Make sure to use Node-RED to review your changes [see doc](https://nodered.org/docs/user-guide/projects/#local-changes)

You can commit via CLI or Node-RED. You can only push via CLI.

```sh
cd PlanktoScope/node-red/projects/dashboard
git push
```

## Read and Write Data in global.json

Data is stored in a file located at: [`/home/pi/PlanktoScope/node-red/context/global/global.json`](http://planktoscope.local/admin/fs/files/home/pi/PlanktoScope/node-red/context/global/global.json).

### Read Data

To retrieve a value stored in this file, use the following script in a Function Node:

```javascript
// Retrieve the global variable
msg.variable = global.get("variable")
return msg
```

### Template Node to Display and Modify Data

```html
<template>
  <v-text-field
    label="My variable"
    variant="outlined"
    v-model="msg.variable"
    @update:model-value="send({ variable: msg.variable })"
  ></v-text-field>
</template>
```

### Write Data

To set a value in the file, use the following script in a Function Node:

```javascript
// Set a value in the global context
global.set("variable", msg.variable)
return msg
```
