---
title: Bulk Cells Introduction
description: Mainly focused on Bulk Cells & The concepts of Bulk storages
authors: 
    - Boold
---

# Bulk Cells

This is a quick overview to the best storage addons you'll ever need :]  

In this section, You'll find **How to Use Bulk Cells**, the **characteristic of the Bulk Cells** itself, and the **general idea of "Bulk Storage"**.  

## Bulk Concepts

!!! danger "You can skip to ``How To Use`` sub-chapter if you dislike reading"  
???+ warning "Familiarize yourself with these required items"
    ![](img-bulk/booldBulkRequirements.png)  
    * Cell Workbench  
    * MEGA Bulk Item Storage Cell  
    * MEGA Decompression Module  
    * Compression Card  

### Where bulk terms is used
Before we went deeper, One might asks what is "bulk" and why we use it in storage, or where do we find it? moreover related to AE2.  

Now take a look at this mess:  

![](img-bulk/booldRandomMess.png)  

From the image above, there's **random things** like building blocks, seeds, some saplings, and miscellaneous materials. We also notices that most of these items **does not exceeed 1000**. We'll call this as **Random Mess** for now.  

In contrast, from the image below, we can see that those items is **stored at a very big numbers** compared to the previous ones. Instead, we'll refer this as **Bulk Mess**  

![](img-bulk/booldBulkMess.png)  

### General vs Bulk Storage 

All of those random bits and pieces of items previously typically stored insides what we call a **"General Storage"**. In a literal sense, every dumps & junks we insert to the network, will **eventually ends up** in this type of storages. Just like the Random Mess we had before. Any other things then (generally) will be stored insides a **"Bulk Storage"**  
!!! note "A literal "storing items in bulks" !"

### Partition?

Just in case it's not obvious now, 'partitioning' cells is an important aspect when we talk about bulk storage. Imagine your creeper farm generating thousands of gunpowder per minutes, this will clogs up your 'general storage' quickly over time (you don't want your cells is filled up with gunpowder **only** didn't ya?).  

In this case, we **partitions** a cell (generally the ones who can stores alot) and assigned it to a specific cell. **Priority System** in AE2 means you can tell items to go into a specific storage (or drives) first, before it goes into another storage.  

???+ info "Items route in the network on General Storage vs Bulk Storage & Partitions in-between"
    ![](img-bulk/booldPriorityInsert.png)  
    The system works like this:   
    1. You insert the items into the network   
    2. The network now tried to "store" said items into the valid 'storage'  
    3. It checks the valid storage with the highest priority (in this case, Bulk storage, which only accepts gunpowder)  
    4. If it fails to store said items into the Bulk Storage (say, a stick), it checks again the next valid storage  
    > Thus gunpowder always get stored first inside bulk storage, and anything that isn't gunpowder stored inside general storage. It doesn't clogs the system, and you can always dump more junks into the system. **This is why bulk storage is important** 

For a better grasp of the differences between the two, take a look at this table:  

| **General Storage** <br> ![](img/itemCell.png) | **Bulk Storage** <br> ![](img/bulkCell.png) |
|:---:|:---:|
| Typically stores random things | Typically stores specific items (mainly resources/mob drops/farm drops) |
| Ex. Cobble walls, doors, fence, lantern, furnace | Ex. Iron ingots, spruce logs, diamonds, rotten flesh, wheat |
| Doesn't really wants "partition" | Partition is a must (at the very least, highly suggested) |
| Requires less works | Usually more steps to do |
| Good for dumping unorganized items | Good for optimizing your network contents |
| Tends to be used less per ME Drive | Tends to be used more per ME Drive |
| Identic with lower amount of items (less than 5k, etc.) | Identic with high number of items (thousands/millions/billions even!) |
  

## What Is Bulk Cells?

**MEGA Bulk Item Storage Cell**, further referred as 'Bulk Cells', is a storage cell from an addon mods called MEGA Cells by ninety.  

Bulk Cells is incredibly powerful. A single cell can only holds 1 type of item, **but** it stores item in ``BigInt`` value. Which is ``truly big``, the limitations is your system memory. **practically infinite**.  
> Read more about [BigInt Max Limit](https://stackoverflow.com/questions/12088436/what-does-biginteger-having-no-limit-mean)   

??? info "Did you know that?"
    Assuming:  
    - You can theoretically produces a resource at a ``maxInt`` value per tick (2.147.483.647 of iron ingots for example)  
    - And do it 24/7  

    It still requires **6 years, 10 months, and 7 days** to only reach max capacity of ``MaxLong``(a 19 digits numbers). And ``BigInt`` can stores **more** than 268.000.000 digits (relative to system memory) ! this also means you do **not** need any kind of Overflow Destruction (or is it?).  


!!! abstract "But hey, there's more"
    On top of storing items, Bulk Cells also have the abilities to **compress & decompress** items automatically! 

### Compress & Decompress
Having to make a pattern to craft ``nuggets`` from an ``iron ingots``, and another pattern for crafting ``iron block``, AND THEN another pattern to craft those back into iron ingots is surely labour-intensive. Up until now, you might be familiar by using **Storage Drawers** to do this kind of thing. A Compacting Drawers to be exact.  

!!! danger "But this comes with a small problem for drawers"  
    Compacting Drawers (and any other variants of physical-storage-compactor from other mods) for the longest time existing never plays nice with AE2. This is because when a storage controller (ones you used to read all the drawers content) reads by a Storage Bus (External Storage application), **it reports the content incorrectly** (it should only report once)
???+ info "Example of compactors misreports to AE2"
    ![](img-bulk)
    [//] : # (insert pict about compress)
    Here we can see that the system reads we have 81 nuggets, 9 iron ingots, and 1 iron block. But clearly **we don't have those**, since that would just means we have 3 iron blocks. Which the drawer itself definitely shows **it only has 1**      


!!! note "Luckily the Bulk Cells already takes care of that for us :3"

### Storage Drawers vs Bulk Cells

One might wonder,
!!! quote "Huh. This seems just like **Storage Drawers**. Both can **stores alot** & **compresses items**. Why would I use these cells instead of drawers?"  

Then let me present to you the ups & downs.  
WIP

## How does it work?

!!! danger "Disclaimer"
    This sub-chapter may or may not explain it 1:1 to the actual backend code logic. This sub-chapter only gives you the rough ideas on why things works.

!!! tip "**Decompression Module is crucial** for the network. It enables the network to do all compression/decompression (despite the name only suggests decompressing items). Otherwise your Bulk Cells is just a **fancy infinite chest**"

???+ info "Compressing/Upcrafting"
    It has been mentioned before that **Bulk Cells can compress items automatically**. With the analogy of having to make patterns to craft ``nuggets`` to ``ingots``, then ``ingots`` to ``blocks``, then ``blocks`` to ``1x blocks``, and etc. this can adds up alot in the **pattern provider**. Instead, we can use **Compression Card** inside the bulk cells to enable 'compression'. This will **allow the network** to automatically makes a *ghost-pattern* that handles **all compression**. Yes, ***everything***. From as small as nuggets, up to 9x variants (if possible).

???+ info "Decompressing/Downcrafting"  
    Borrowing the previous analogy, we also wanted to downcraft ``1x blocks`` back into ``blocks`` and more. The bulk cells also **handles downcrafting quite similar to compressing**. When a craft request a form of items at a smaller variant 
    !!! example "Example, make 9 ``iron blocks`` but we only have ``3x iron blocks``"
    Then the system also makes a *ghost-patterns* that handles ``crafting 3x iron into 2x``, ``2x into 1x``, and more until it reaches the desired amount from the system (9 iron blocks).

??? question "Yes, but WHEN it does compression/decompress?"
    Generally it happens **when the network interacts with item amounts**.  
    This includes, but not limited to:  
    1. Items **entering** the network  
    2. The Network **exporting out** items  
    3. You, the player, directly taking out/dumping items in the **Terminal**  
    !!! warning "for a regular player usage (it means Me, & **YOU**), all of this doesn't really need to worry about. Dont't sweat it out :)"

!!! danger "Regarding Energy Usage"
    It is also worth noting that **every contents (items/gas/fluid/etc.) movement inside an AE2 network requires energy** (in the form of AE). Compressing/Decompressing **is no exception**. On a rare case, One can have not enough network buffer to do any item compression, oftentimes resulting in a **failed Crafting Request**.


    

 
## How to use it?

> *Here comes the main dish*  

Up to this point, you should already know why bulk matters, how to do partitions, and the items required for it as well (refer to the notes in Bulk Concepts)

> Functional Storage | [CurseForge](https://legacy.curseforge.com/minecraft/mc-mods/functional-storage)  
> MEGA Cells | [CurseForge](https://legacy.curseforge.com/minecraft/mc-mods/mega-cells)  
> ExtendedAE | [CurseForge](https://legacy.curseforge.com/minecraft/mc-mods/ex-pattern-provider)