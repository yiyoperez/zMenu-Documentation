---
Descrizione: Sistema dati del giocatore
---

# Dati del giocatore

Con zMenu puoi memorizzare i dati per il giocatore e utilizzarli con i placeholders. In questo modo puoi creare contatori, cooldown e molto altro!

Ogni dato contiene una chiave, un valore e una data di scadenza. Se inserisci **0** i dati non scadranno mai. La data di scadenza è un timestamp.

## Comandi

Il pwermesso per utilizzare questi comandi è: `zmenu.players`

<table><thead><tr><th width="410">Comandi</th><th>Descrizione</th></tr></thead><tbody><tr><td>/zm players</td><td>Mostra la lista dei comandi per i dati dei giocatori.</td></tr><tr><td>/zm players set &#x3C;player> &#x3C;key> &#x3C;expiration> &#x3C;value></td><td>Imposta dei dati nuovi. Devi impostare il tempo in secondi. Immettere 0 per non aavere una scadenza.</td></tr><tr><td>/zm players remove &#x3C;player> &#x3C;key></td><td>Togliere dati.</td></tr><tr><td>/zm players get &#x3C;player> &#x3C;key></td><td>Ottenere dati.</td></tr><tr><td>/zm players kets &#x3C;player></td><td>Da in dietro la lista delle chiavi di un giocatoe.</td></tr><tr><td>/zm players clear &#x3C;player></td><td>Elimina i dati di un giocatore.</td></tr><tr><td>/zm players clearall</td><td>Elimina i dati di tutti i giocatori.</td></tr><tr><td>/zm players add &#x3C;player> &#x3C;key> &#x3C;value></td><td>Aggiunge un numero al valore, funziona solo per i numeri.</td></tr><tr><td>/zm players subtract &#x3C;player> &#x3C;key> &#x3C;value></td><td>Sottrae un numero da un valore, funziona solo per i numeri.</td></tr></tbody></table>

## Placeholders

I placeholders possono essere utilizzati in un inventario per visualizzare un item o per ottenere un permesso. Puoi bloccare l'accesso a un pulsante con un placeholder. Puoi vedere un esempio [qui](../plugins-files.md).

<table><thead><tr><th width="426.56591923371104">Placeholder</th><th>Descrizione</th></tr></thead><tbody><tr><td><code>%zmenu_player_value_&#x3C;key>%</code></td><td>Da in dietro il valore contenuto in una chiave. </td></tr><tr><td><code>%zmenu_player_expire_format_&#x3C;key>%</code></td><td>Da in dietro la data di scadenza formattata secondo una chiave.</td></tr><tr><td><code>%zmenu_player_expire_&#x3C;key>%</code></td><td>Da in dietro la data di scadenza secondo una chiave.</td></tr><tr><td><code>%zmenu_player_key_exist_&#x3C;key>%</code></td><td>Da in dietro true o false. Ti permette di sapere se una chiave esiste.</td></tr></tbody></table>
