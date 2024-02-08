# Patterns

The patterns allow you to have a list of buttons that can be used in several inventories. Perfect to manage the decoraction of your inventories without having to copy the same thing dozens of times.



The patterns can be found in the patterns folder and you can create as many as you want.



[Example](../plugins-files.md#pattern1):

```yaml
name: "pattern1"
size: 54
# Displays the pattern on multiple pages, false by default
enableMultiPage: <true/false>
items:
    ...
```

A pattern must contain a `name`, its name will be used in inventories to identify the pattern.&#x20;

You then have a `size`, which is that of the inventory, you have to put patterns of the same size with the inventories, a pattern of size 18 cannot go with an inventory of cut 27 for example.

You then have a list of items, it’s the same as for [inventories](inventories.md#items).
