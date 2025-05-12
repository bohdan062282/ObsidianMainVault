- *Ну по сути да, если например в скриптах использовать элементы, то лучше обращаться по именам, они более стабильны.*
- *Я так понимаю номаера закрепляются за сессией терминала и пока не будет принт. То есть по идее если я мувнул чето, то пока я не принтану, номера будут те же?*
- *Номера можно использовать через запятую `interface set 0,1,2 mtu=1460`*
- *Можно сокращать очевидные имена  `pin 10.1 c 3 si 100` иквалз ту `ping 10.0.0.1 count 3 size 100`*
- *In "/console/settings" menu, it is possible to enable option for replacing reserved characters with underscores for file name. `sanitize-names (yes|no Default: no)` (Replace reserved characters (\ / : * ?  |)  with underscores).
- *The "**:lock**" command locks the screen.*


### General Commands

Some commands are common to nearly all menu levels, namely: **print**, **set**, **remove**, **add**, **find**, **get**, **export**, **enable**, **disable**, **comment**, and **move**. These commands have similar behavior throughout different menu levels.

- **add** - this command usually has all the same arguments as **set**, except the item number argument. It adds a new item with the values you have specified, usually at the end of the item list, in places where the order of items is relevant. There are some required properties that you have to supply, such as the interface for a new address, while other properties are set to defaults unless you explicitly specify them.
    - Common Parameters
        - _copy-from_ - Copies an existing item. It takes the default values of a new item's properties from another item. If you do not want to make an exact copy, you can specify new values for some properties. When copying items that have names, you will usually have to give a new name to a copy
        - _place-before_ - places a new item before an existing item with a specified position. Thus, you do not need to use the move command after adding an item to the list. 
        - _disabled_ - controls disabled/enabled state of the newly added item(-s)
        - _comment_ - holds the description of a newly created item
    - Return Values
        - add command returns the internal number of item it has added
- **edit** - this command is associated with the **set** command. It can be used to edit values of properties that contain a large amount of text, such as scripts, but it works with all editable properties. Depending on the capabilities of the terminal, either a fullscreen editor or a single-line editor is launched to edit the value of the specified property. The edit field for console scripts is limited to 30 thousand characters.
- **find** - The find command has the same arguments as set, plus the flag arguments like _disabled_ or _active_ that take values _yes_ or _no_ depending on the value of the respective flag. To see all flags and their names, look at the top of the **print** command's output. The **find** command returns internal numbers of all items that have the same values of arguments as specified.
- **move** - changes the order of items in the list.
    - Parameters
        - first argument specifies the item(-s) being moved.
        - the second argument specifies the item before which to place all items being moved (they are placed at the end of the list if the second argument is omitted).
- **print** - shows all information that's accessible from a particular command level. Thus, **/system clock print** shows the system date and time, **/ip route print** shows all routes, etc. If there's a list of items in the current level and they are not read-only, i.e. you can change/remove them (an example of a read-only item list is /system history, which shows a history of executed actions), then print command also assigns numbers that are used by all commands that operate with items in this list.
    - Common Parameters
        - _from_ - show only specified items, in the same order in which they are given.
        - _where_ - show only items that match specified criteria. The syntax of _where_ the property is similar to the **find** command.
        - _brief_ - forces the print command to use tabular output form
        - _detail_ - forces the print command to use property=value output form
        - _count-only_ - shows the number of items
        - _file_ - prints the contents of the specific submenu into a file on the router.
        - _interval_ - updates the output from the _print_ command for every interval of seconds.
        - _oid_ - prints the OID value for properties that are accessible from SNMP
        - _without-paging_ - prints the output without stopping after each screenful.
- **remove** - removes specified item(-s) from a list.
- **set** - allows you to change values of general parameters or item parameters. The set command has arguments with names corresponding to values you can change. Use "F1" or double [Tab] to see a list of all arguments. If there is a list of items in this command level, then "set" has one action argument that accepts the number of item (or list of numbers) you wish to set up. This command does not return anything.
- **reset** - reset parameters to default values

Примерчик комбинации:
```bash
/ip firewall/filter/add chain=forward place-before=[find where comment=CommentX]  
/ip/firewall/filter/add chain=forward place-before="CommentX"
```

### List of keys

- `F1` Give the list of available commands command
- `F1` Give help on the command and list of arguments 

- `[Tab]` Complete the command/word. If the input is ambiguous, a second [Tab] gives possible options
- `F3` or `Ctrl-R` Search command history
- `F4` or `Ctrl-X` Toggle safe mode
- `F5` or `Ctrl-L` Repaint the screen
- `F7` Toggle hotlock mode
- `F8` Print entire multiline input
- `Ctrl-\` Split line
- `Home` or `Ctrl-A` Go to the beginning of the line
- `End` or `Ctrl-E` Go to the end of the line
- `Ctrl-C` Interrupt current action
- `Ctrl-D` Terminate session (on empty prompt)
- `Ctrl-K` Delete to the end of the line
- `Ctrl-U` Delete to the beginning of the line
- `Ctrl-T` Switch to a background task

- `/` Move up to base level
- `..` Move up one level
- `/command` Use command at the base level

**up**, **down** and **split** keys leave the cursor at the end of the line.

### Safe mode
The **"Safe Mode"** button in the Winbox GUI allows you to enter Safe Mode, while in the CLI, you can access it by either using the keyboard shortcut **F4** or pressing **[CTRL]+[X]**. To exit without saving the made changes in CLI, hit **[CTRL]+[D].**

You can see all such changes that will be automatically undone and tagged with an **F** flag in the system history:
![[Pasted image 20250512141907.png]]

Now, if the telnet connection (or WinBox terminal) is cut, then after a while (TCP timeout is **9** minutes) all changes that were made while in safe mode will be undone. Exiting session by **[Ctrl]+[D]** also undoes all safe mode changes, while **/quit** does not.

### HotLock Mod
When HotLock mode is enabled commands will be auto-completed.

Double`>>`is an indication that HotLock mode is enabled. For example, if you type "`/in et"`, it will be auto-completed to `/ip/address>> /interface/ethernet/`






