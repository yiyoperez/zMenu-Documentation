---
description: List of the commands and their permissions
---

# 📜 Commands and Permissions

## Commands

<table data-full-width="true"><thead><tr><th width="409.9844776750376">Command</th><th width="160.56947162426616">Permission</th><th>Description</th></tr></thead><tbody><tr><td>/zm (aliases: /zmenu)</td><td>zmenu.use</td><td>Display the list of commands.</td></tr><tr><td>/zm open &#x3C;menu> [&#x3C;player>] [&#x3C;display message>] [&#x3C;args>]</td><td>zmenu.open</td><td>Opens the specified inventory.</td></tr><tr><td>/zm reload</td><td>zmenu.reload</td><td>Reload configurations.</td></tr><tr><td>/zm reload config</td><td>zmenu.reload</td><td>Reload config.json and messages.yml files</td></tr><tr><td>/zm reload inventory [&#x3C;inventory name>]</td><td>zmenu.reload</td><td>Reload inventories files</td></tr><tr><td>/zm reload command [&#x3C;command name>]</td><td>zmenu.reload</td><td>Reload commands files</td></tr><tr><td>/zm version</td><td></td><td>Show plugin version.</td></tr><tr><td>/zm convert</td><td>zmenu.convert</td><td>Convert DeluxeMenu to zMenu.</td></tr><tr><td>/zm list</td><td>zmenu.list</td><td>Inventory list</td></tr><tr><td>/zm create &#x3C;file name> &#x3C;inventory size> &#x3C;inventory name></td><td>zmenu.create</td><td>Create a new inventory file, you just have to add items afterwards.</td></tr><tr><td>/zm save &#x3C;item name></td><td>zmenu.save</td><td>Save the item you have in hand in the plugin configuration format.</td></tr><tr><td>/zm giveopenitem &#x3C;inventory> [&#x3C;player>]</td><td>zmenu.open.item</td><td>Allows to retrieve the item that must be used to open the inventory during a click</td></tr><tr><td>/&#x3C;command></td><td>Custom permission</td><td>Open specific file.</td></tr></tbody></table>

List of commands for the player data system [here](player-data.md).

### Open command with argument

You can use the/zm open command with arguments (like [here](commands.md#informations)).

For example, with default inventory `example_punish`. You will be able to define the two arguments to be used. You can do this in two ways.

* The first is to specify the names of the arguments, as follows: `<argument name>:<argument value>`\
  Example: `/zm open zmenu:example_punish Maxlego08 false target:Maxlego09 reason:test`\
  Result: `%zmenu_argument_target%` and `%zmenu_argument_reason%`\
  You can also add more argument like that: `/zm open zmenu:example_punish Maxlego08 false target:Maxlego09 reason:"this is a really long reason"`
* The second is to directly use the value, so the argument name will be 0 for the first value, 1 for the second etc...\
  Example: `/zm open zmenu:example_punish Maxlego08 false Maxlego09 test`\
  Result: `%zmenu_argument_0%` and `%zmenu_argument_1%`

## Convert

To convert your DeluxeMenu configurations to zMenu you must use the **zMenuConvert** extension.

Download link: [https://groupez.dev/resources/zmenuconvert.266](https://groupez.dev/resources/zmenuconvert.266)

After installing the plugin you need to run the command **/zm convert**. Your menus and commands will be created in the `inventories/convert` and `commands/convert` folders.

Be careful, the conversion may contain errors, you must check your files to make sure there are no problems.&#x20;

Github: [https://github.com/Maxlego08/zMenuConvert](https://github.com/Maxlego08/zMenuConvert)
