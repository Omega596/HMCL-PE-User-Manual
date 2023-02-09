# Solve the problem yourself(WIP)

> If you can't find a crash report when a crash occurs, it's better to say "I've crashed and what to do" than to go to the street and find a fortune teller to figure out why it crashed, so where to find them?
>
> &#x20;                                                                                                                                           \--943

## Check Modlist

For beginners, the first thing you can do is to start by looking at the bottom of the entire crash log, where there is a self-shaped table with all the modules that have been identified.

![](<../../.gitbook/assets/image (5) (1) (1).png>)

Here we note the column with LCHI or LCHE on the left, each letter carries its own meaning

| Letter                              | Meaning                                                                                           |
| ----------------------------------- | ------------------------------------------------------------------------------------------------- |
| <mark style="color:red;">'U'</mark> | Unloaded<mark style="color:red;">(Indicates that the loading was aborted)</mark>                  |
| <mark style="color:red;">'E'</mark> | Errored<mark style="color:red;">(Indicates that the mod failed to start due to errors)</mark>     |
| 'D'                                 | Disabled                                                                                          |
| 'L'                                 | Loaded                                                                                            |
| 'C'                                 | Constructed                                                                                       |
| 'H'                                 | Pre-initialized                                                                                   |
| 'I'                                 | Initialized                                                                                       |
| 'J'                                 | Post-initialized                                                                                  |
| 'A'                                 | Available                                                                                         |

## Deeper Analysis

![](<../../.gitbook/assets/image (1) (1) (3).png>)

Why is there also a place at the top that shows the mod where the error occurred, so if I look at it from the top will I get a more detailed answer?

Yes, if we look at the sentences following Description and Caused by above, we can roughly determine what mod caused the crash

## Other issues

You can find java.lang.XXX in the next line of the Description, The following are some of the XXX representatives' questions:

### NoClassDefFoundError

#### Server side:

(1)The server side lacks classes and methods related to the GUI like the client side, and the client mod will show that the classes are not found when calling these methods

Solutions:Remove mods that only work on the client side

### ClassCastException

#### both Server\&Client

Unable to perform class conversion, in layman's terms, a mod conflict

Solutions:Remove one (or muiltiple) of the conflicting mods

### LoaderException

#### both Server\&Client

There was a problem loading the mod

Solution: Check [Check Modlist section](solve-the-problem-yourself-wip.md#check-modlist) to find Errored Mods, Replace or delete the mod or update the loader

### OutOfMemoryError

#### both Server\&Client

Solution: Increase your RAM allocation

### Exception while ticking a block

#### both Server\&Client

Solution: Find the "-- Block being ticked --" section, learn the block coordinates, and use some methods to remove the block, or if it is a mod block, remove the mod and then remove the now black and purple block,

If it is in a server and you know the coords. of that block, and you are a server owner or a admin, then you do /setblock x y z Minecraft:air

