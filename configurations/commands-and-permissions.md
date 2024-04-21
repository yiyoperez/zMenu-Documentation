---
description: List of the commands and their permissions
---

# Commands and Permissions

## Commands

<table data-full-width="true"><thead><tr><th width="409.9844776750376">Command</th><th width="160.56947162426616">Permission</th><th>Description</th></tr></thead><tbody><tr><td>/zm (aliases: /zmenu)</td><td>zmenu.use</td><td>Mostra la lista dei comandi.</td></tr><tr><td>/zm open &#x3C;menu> [&#x3C;player>] [&#x3C;display message>] [&#x3C;args>]</td><td>zmenu.open</td><td>Apri l'inventario specificato.</td></tr><tr><td>/zm reload</td><td>zmenu.reload</td><td>Aggiorna le configurazioni.</td></tr><tr><td>/zm reload config</td><td>zmenu.reload</td><td>Aggiorna la config.json e i file linguistici</td></tr><tr><td>/zm reload inventory [&#x3C;inventory name>]</td><td>zmenu.reload</td><td>Aggiorna i menu</td></tr><tr><td>/zm reload command [&#x3C;command name>]</td><td>zmenu.reload</td><td>Aggiorna i file dei comandi</td></tr><tr><td>/zm version</td><td></td><td>Mostra la versione del plugin.</td></tr><tr><td>/zm convert</td><td>zmenu.convert</td><td>Converti DeluxeMenu a zMenu.</td></tr><tr><td>/zm list</td><td>zmenu.list</td><td>Lista inventari</td></tr><tr><td>/zm create &#x3C;file name> &#x3C;inventory size> &#x3C;inventory name></td><td>zmenu.create</td><td>Crea un nuovo menu, dovrai solamente personalizzarlo</td></tr><tr><td>/zm save &#x3C;item name></td><td>zmenu.save</td><td>Salva l'oggetto che stai tenendo nel plugin per un utilizzo futuro.</td></tr><tr><td>/zm giveopenitem &#x3C;inventory> [&#x3C;player>]</td><td>zmenu.open.item</td><td>Consente di ritrovare l'oggetto che deve essere usato per aprire il menu</td></tr><tr><td>/&#x3C;command></td><td>Custom permission</td><td>Apre un file.</td></tr></tbody></table>

Lista di comandi per i dati dei giocatori [qui](player-data.md).

### Comando per aprire menu (con arguments)

You can use the/zm open command with arguments (like [here](commands.md#informations)).

Per esempio, con l'inventario predefinito `example_punish`. Potrai definire 2 arguments che potrai usare. Puoi farlo in 2 modi:

* 1. Specifica il nome degli arguments, esempi: `<argument name>:<argument value>`\
  Esempio: `/zm open zmenu:example_punish Maxlego08 false target:Maxlego09 reason:test`\
  Risultato: `%zmenu_argument_target%` and `%zmenu_argument_reason%`\
  Puoi anche aggiungere più arguments: `/zm open zmenu:example_punish Maxlego08 false target:Maxlego09 reason:"this is a really long reason"`
* The second is to directly use the value, so the argument name will be 0 for the first value, 1 for the second etc...\
  Esempio: `/zm open zmenu:example_punish Maxlego08 false Maxlego09 test`\
  Risultato: `%zmenu_argument_0%` and `%zmenu_argument_1%`

## Convert

Per convertire i tuoi menu da DeluxeMenu a zMenu devi usare **zMenuConvert**

Download link: [https://groupez.dev/resources/zmenuconvert.266](https://groupez.dev/resources/zmenuconvert.266)

After installing the plugin you need to run the command **/zm convert**. Your menus and commands will be created in the `inventories/convert` and `commands/convert` folders.

Be careful, the conversion may contain errors, you must check your files to make sure there are no problems.&#x20;

Github: [https://github.com/Maxlego08/zMenuConvert](https://github.com/Maxlego08/zMenuConvert)
