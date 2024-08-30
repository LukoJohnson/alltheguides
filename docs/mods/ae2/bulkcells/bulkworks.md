---
title: How Does Bulk Cell Works
description: Mainly focused on Bulk Cells & The concepts of Bulk storages
authors: 
    - Boold
---

# How does it works?

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
    3. A **Crafting Requests** from an automation/player-requests for certain compressed items variants  
    4. You, the player, directly taking out/dumping items in the **Terminal**  
    !!! warning "for a regular player usage (it means Me, & **YOU**), all of this doesn't really need to worry about. Dont't sweat it out :)"
    !!! tip "If you insert/extract items within the network, if it's possible, it will always gets **unified with other compressed variants**. And the system shows the **highest compressed form possible** in the network (here, it's 9x iron & 3 5x iron) ![](img-bulk/booldCompressedStoring.png)"

!!! danger "Regarding Energy Usage"
    It is also worth noting that **every contents (items/gas/fluid/etc.) movement inside an AE2 network requires energy** (in the form of AE). Compressing/Decompressing **is no exception**. On a rare case, One can have not enough network buffer to do any item compression, oftentimes resulting in a **failed Crafting Request**.

> Functional Storage | [CurseForge](https://legacy.curseforge.com/minecraft/mc-mods/functional-storage)  
> MEGA Cells | [CurseForge](https://legacy.curseforge.com/minecraft/mc-mods/mega-cells)  
> ExtendedAE | [CurseForge](https://legacy.curseforge.com/minecraft/mc-mods/ex-pattern-provider)