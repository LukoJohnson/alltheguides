---
title: What is Bulk Cells?
description: Explains the characteristics of bulk cells
authors: 
    - Boold
---

# *Everything About It*

This sub-chapter brings to you the overview of **bulk cells** & it's accompanying trinkets.  

## What Are Those?

### Bulk Cells

**MEGA Bulk Item Storage Cell**, further referred as 'Bulk Cells', is a storage cell from an addon mods called **MEGA Cells** by ninety.  

Bulk Cells is an incredibly powerful cell. A single cell can only holds 1 type of item, **but** it stores item in ``BigInt`` value. Which is **frickin' big**, the limitations is your system memory. **Practically infinite**.  
> Read more about [BigInt Max Limit](https://stackoverflow.com/questions/12088436/what-does-biginteger-having-no-limit-mean)   

??? tip "Did you know that?"
    Assuming:  
    - You can theoretically produces a resource at a ``maxInt`` value per tick (2.147.483.647 of iron ingots per tick for example)  
    - And do it 24/7  

    It still requires **6 years, 10 months, and 7 days** to only reach max capacity of ``maxLong`` (a 19 digits numbers). And ``BigInt`` can holds **more** than 268.000.000 digits (relative to your system memory of course) ! This also means you **do not** need any kind of Overflow Prevention... (or is it?)  


!!! abstract "But hey, there's more"
    On top of storing items, Bulk Cells also have the abilities to **compress & decompress** items automatically! 

### Compression & Decompression
Having to make a pattern to craft ``nuggets`` from an ``iron ingots``, and another pattern for crafting ``iron block``, AND THEN another pattern to craft those back into iron ingots is surely **labor-intensive**, especially when you're playing a pack that **adds more than** just iron, gold, copper, & diamonds. Up until now, you might be familiar by using **Storage Drawers** to do this kind of thing. A Compacting Drawers to be exact.  

!!! danger "But this comes with a small problem for drawers"  
    Compacting Drawers (and any other variants of physical-storage-compactor from other mods) for the longest time existing never plays nice with AE2. This is because when a storage controller (ones you used to read all the drawers content) reads by a Storage Bus (External Storage application), **it reports the content incorrectly**.
    ??? example "Example of misreports to AE2"
        ![](img-bulk/booldCompactingMisreport.png){.center}  
        ![](img-bulk/booldCompactingExample.png){.center height='75px'}
        Here we can see that the system reads we have 81 nuggets, 9 iron ingots, and 1 iron block. But clearly **we don't have those**, since that would just means we have 3 iron blocks. When the drawer itself definitely shows **it only has 1**. This also sometimes referred as "**Over-Report**"      


!!! note "Luckily the Bulk Cells already takes care of that for us :3"

### Compression Card

![](img-bulk/compressionCard.png){.center width='75px' height='75px'}  
Compression Card is a **Card Upgrade** which you can install to a bulk cell **inside a Cell Workbench**. This thing makes the bulk cell assigned with it **considered as valid** by the network to do **compression** of that cell contents.
!!! danger "Not assigning a Compression Card = No Compression!"
??? example "Comparisons between Assigning Compression vs No Compression"
    ![](img-bulk/booldCompressComparison.png)  

### Decompression Module

![](img-bulk/decompressionModule.png){.center width='75px' height='75px'}  
Decompression Module is a **cable sub-part**, meaning it can only be attached into a **regular-sized ME cable** (won't connect into dense). Simultaneously with compression cards, this thing instead enables **the network** itself to be able to do any decompression. To install it, just place it anywhere in the network (like the **Wireless Access Point**).  
!!! danger "Any decompression requires a **functional CPU Multiblock** !"


## Storage Drawers vs Bulk Cells

One might wonder,
!!! quote "Huh. Bulk cells seems just like **Storage Drawers**. Both can **stores alot** & **compresses items**. Why would I use these cells instead of drawers?"  

Then let me present to you the ups & downs.  

!!! warning "Disclaimer"
    This is not to say **one is worse** than another. Both has their own pros & cons. **DO NOT** weaponize this table to go ham on another user preferences.  

| **Storage Drawers** ![](img-bulk/storageDrawer.png){.center width='32' height='32'} | **Bulk Cells** ![](img-bulk/decompressionModule.png){.center width='32' height='32'} |
|:---:|:---:|
| Holds up to 2.1 Billions of items | Practically holds infinite items  |
| Very cheap | Relatively more expensive |
| Very easy to get into | Quite complex to start |
| Partitions done by using items + Config Tool | Partitions done by Cell Workbench + Cards |
| Compacting Drawers can misreport item amounts | Precise compression |
| Higher-form compression might be tricky  | Handles every-form of compression innately + built-in decompression |
| Takes up more physical spaces | Quite space-efficient |
| Storage Bus readings (External Storage)  can affect performance when scaled up | Innate AE2 support (storage cell)  means more optimized when scaled up |

???+ success "Additional Notes"
    ??? tip "Regarding Space-Efficient..."
        ![](img-bulk/booldSizeComparison.png){.center}  
        This is the looks of storing 20 items in bulks. ME Drive from base AE2 holds 10 cell each, and ME Extended Drive from **ExtendedAE** mods can holds 20 cell each. Making it more compact with **1:20 ratio** of space to item types compared to drawers.
    ??? tip "Regarding External Storage..."
        External Storage is perfectly fine to do. Slight delay (performance affection) is bound to happen because it tries to read every slots in a **drawer network** that a storage bus able to read to. This is also mentioned by the **in-game guide**.  

> Applied Energistics 2 | [CurseForge](https://legacy.curseforge.com/minecraft/mc-mods/applied-energistics-2)  
> Functional Storage | [CurseForge](https://legacy.curseforge.com/minecraft/mc-mods/functional-storage)  
> MEGA Cells | [CurseForge](https://legacy.curseforge.com/minecraft/mc-mods/mega-cells)  
> ExtendedAE | [CurseForge](https://legacy.curseforge.com/minecraft/mc-mods/ex-pattern-provider)