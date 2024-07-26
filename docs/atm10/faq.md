---
title: ATM10 FAQ
description: ATM10 Frequently Asked Questions
authors: 
---

# FAQ

**All The Mods 10** Frequently Asked Questions

---

???+ Danger "ALPHA DISCLAIMER"
	ATM10 is in public ***alpha***, meaning there will be bugs, missing mods, no traditional ATM endgame, missing quests, etc. It will be getting frequent updates as mod devs update to 1.21, and the ATM dev team continues to work on adding new mods, quests, and scripts. [You can report bugs and make suggestions here.](https://github.com/AllTheMods/ATM-10/issues/)
	

???+ Abstract "Gameplay FAQs"
	??? Question "How do I change `/home`, `/tpa` etc cooldown?"
		To change the behavior of `/home` or to re-enable `/back` and `/rtp`, edit `saves/worldName/serverconfig/ftb-essentials.snbt`. **The world/server has to be stopped for the changes to take effect.**
		
	??? Question "I can't complete '`questName`' even though I fufilled the requirements?"
		You can enable edit quests in the bottom right of the quest screen (you need OP for this) and then r-click the broken quest and `Complete Instantly` it OR click the quest then r-click the reward and `Reset Progress` if you still want the rewards.

	??? Question "How do I increase claimed/force loaded chunks?"
		- Add claimed chunks: `/ftbchunks admin extra_claim_chunks <player> <set/add> <amount>`
		- Add force-loaded chunks: `/ftbchunks admin extra_force_load_chunks <player> <add/set> <amount>`

???+ Warning "Technical FAQs"
	???+ Question "Why isn't '`insert name`' mod in ATM10 yet?"
		ATM packs does not literally contain "All The Mods". Our main focus is having mods that's not: 1) buggy, 2) ruins performance or progression and 3) is updated to 1.21. If a mod supports Minecraft version **1.21**, and **Neo Forge**, you may make a [suggestion](https://github.com/AllTheMods/ATM-10/issues/2).
	
	???+ Question "I found a bug/dupe in the pack. How can I report it?"
		To report bugs, dupes or similar, head over to the [ATM10 GitHub](https://github.com/AllTheMods/ATM-10/issues) and open a new issue describing the occurrence.

	??? Question "What are the recommended Java arguments for this pack?"
		- **Client arguments**: send `?args` in the **#bot-spam** channel in our [Discord](https://discord.com/invite/allthemods).
		- **Server arguments**: send `?svargs` in the **#bot=spam** channel in our [Discord](https://discord.com/invite/allthemods).

	??? Question "Why does my game crash while launching?"
		Lack of RAM most likely. Send `?allocate` in the **#bot-spam** channel in our [Discord](https://discord.com/invite/allthemods) to learn how to allocate more RAM. If that's not the problem, head to **#atm10-techsupport** and send `?logs` to see how to upload your crash/latest log.

	??? Question "I crashed and got `Error code 1`, please help"
		`Exit code 1` is a generic error from Minecraft. It is no different than "game didn't load, no longer attempting to load. Please refer to the output error log created by your launcher" if you are unsure... please feel free to ask for further instructions on how to locate, post, and get help for your specific error so that we may further assist you in our [Discord](https://discord.com/invite/allthemods). Try running `?logs` instead.
