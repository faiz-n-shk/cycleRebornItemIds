Guide to modifying stats and inventory in Mongo DB

WARNING: This can only be done after you have setup and successfully played The Cycle: Frontier with the local server running.

Prep Work for Modifying Stats

    1. Open Mongo DB

    2. Click �Add New Connection�

    3. In the Name Box type something. Any name will work. I used 123

    4. Click Save and Connection

    5. On the left side of MongoDB you should now see a small Laptop Icon with whatever you had typed in the Name Box next to it. Underneath that there should be multiple drop down menus. Click on ProspectDb.

    6. Below ProspectDb three new options should appear with Folder Icons next to them. Click PlayFabUserData.
        ? PlayFabUserData holds all of the user characteristics from The Cycle: Frontier. This includes Vendor Levels, Aurum Totals, K-Mark Totals, current character equipment, Fortuna Pass Level, and much more.

    7. In the center of MongoDB a bunch of data fields should pop up. What you want to look for when scrolling through them will be the �Key� field. This is the name of what that data entry does. For example: The first data entry should be �FactionProgressKorolev�. This your total XP gained within Korolev. There are two pages of these data entries that you can scroll through.

Modifying Faction Level

        1. If you would like to modify the your XP gained with the factions, select the data entry of the faction you would like to modify i.e. �FactionProgressKorolev� and click the pencil icon on the right side of the data entry to edit the information.

        2. In the Value Field, replace the 0 with 450000. This will set your level with that faction to 20 in game. Make sure to type within the quotation marks and do not put a comma within your number.

        3. After modifying the value, look to the right of the data entry and click the Update icon. That field should now be updated in the database.

        4. If you would like to modify all of the faction levels, repeat these steps.

Modifying Currency

    1. With the data entries in the center of MongoDB there should be an arrow button above the entries and to the right that will take you to the second page. Click that button.

    2. Scroll down until you find the data entry with the Key named �Balance�. Select this entry and press the pencil on the right to edit.

    3. In the Value field there should be 3 items in quotations. These are �IN�, �AU�, and �SC� which stands for Insurance Tokens, Aurum, and K-Marks respectively. You can modify these values with what ever amount you would like. Just replace the number that is there with whatever quantity you wish to have of each currency. When finished, press update on the right of that data entry.

Modifying Inventory

WARNING: Modifying your inventory incorrectly can cause the game not to load anymore!
SECOND WARNING: Only add 1 new item to the game at a time. Make sure to restart the game after every change to make sure it worked.

    1. Within the second page of data entries in MongoDB there should be an entry with the Key �Inventory�. Select this entry and click the pencil on the right to edit.

    2. The Value section of this entry is very large and difficult to edit in MongoDB. To easily make changes, select everything within the Value section of the entry. This can be done by highlighting the brackets before the words ItemId and moving your mouse to the right, or by clicking somewhere within the value text box and pressing CTRL + A to highlight it all.

    3. Right click and copy or CTRL + C to copy the text. Then we are going to paste it into 2 separate Text Documents. You can do that by opening the program Note Pad in your computer twice. Then right click in one of the text documents and click paste. Do this with both text documents.

    4. Save one of the text documents to your desktop under the name Inventory Backup. This is just in case something doesn�t work right and you need to go back. You may close the Inventory Backup for now. Leave the other text document open.

    5. Within in the text document you should see a long list of entries that look something like this:

        {"itemId":"54a11e06-64cb-4c84-911c-4871946db2e6","baseItemId":"WP_E_SMG_Bullet_01","primaryVanityId":0,"secondaryVanityId":0,"amount":2,"durability":-1,"modData":{"m":[]},"rolledPerks":[],"insurance":"","insuranceOwnerPlayfabId":"9FB23FAB0D2EC5AB","insuredAttachmentId":"","origin":{"t":"","p":"","g":""}},

    6. You can break these entries down into sections, �ItemId�, �baseItemId�, and �amount�. These are the only values that you will have to do anything with.

    7. In order to make a new weapon in your stash copy the inventory entry above or copy any inventory entry that has a baseItemId that starts with WP. When copying an inventory entry it is very important that you do not include the starting square bracket [ in the selection. Make sure to start selecting the entry from the { bracket before �ItemId� and select all of the way to the comma before the same bracket of another inventory entry. Paste it between the square bracket [ and the other bracket { at the start of the inventory list.

    8. Now that you have a fresh entry in your inventory go ahead and change and single letter or number within the string of letters and numbers under the �ItemId� section. This makes sure that the game won�t think that the item you made is a duplicate of another item with the same ID that is already in your inventory. For example: "itemId":"54a11e06-64cb-4c84-911c-4871946db2e6" I would change the 5 at the start of the ItemId to a 4 making it look like this "itemId":"44a11e06-64cb-4c84-911c-4871946db2e6"

        ? Side Note: If you add more than one item, make sure to change a different number/letter with every new item.

    9. After you have modified the ItemId, the next step is to modify the baseItemId. The baseItemId is the designation of what the weapon is. WP_E_SMG_Bullet_01 for example is a Weapon from Co-Tec that is a SMG that shoots bullets. This means that it would be the PDW seeing as it is the only Co-Tec SMG in the game. The baseItemId can be seen as ItemType_Vendor_WeaponType_AmmoType_01. To modify this value you simply have to replace the WP_E_SMG_Bullet_01 with any weapon Id from the list below. DO NOT COPY THE NAME NEXT TO THE WEAPON ID, That is just there so you know what weapon you are adding.


        ? WP_E_Launch_Nade_01        FF4Detonator
        ? WP_A_Launch_MSL_01        Komrad
        ? WP_A_Sniper_Gauss_01        Karma
        ? WP_A_HVY_Shell_01        Karla
        ? WP_D_HVY_Exotic_01        Haze
        ? WP_G_HVY_Beam_01        Zeus
        ?
        ? WP_D_Sniper_Gauss_01        KineticArbitor
        ? WP_G_Sniper_Energy_01        Basilisk
        ? WP_D_SMG_Energy_01        Brute
        ? WP_A_AR_Bullet_01        KOR
        ? WP_A_Pistol_Bullet_01        Hammer
        ?
        ? WP_G_AR_Beam_01            Gorgon
        ? WP_A_BR_Bullet_01        KBR
        ? WP_D_AR_Bullet_01        Advo
        ? WP_D_SGun_Shard_01        Shattergun
        ? WP_G_SMG_Needle_01        Flechettte
        ?
        ? WP_D_LMG_Energy_01        ICAgarentee
        ? WP_D_BR_Shard_01        Lacerator
        ? WP_A_SGun_Energy_01        Maelstrom
        ? WP_G_AR_Energy_01        PhasicLancer
        ?
        ? WP_D_Pistol_Bullet_01        Bulldog
        ? WP_G_Pistol_Energy_01        Scarab
        ? WP_G_AR_Needle_01        Manticore
        ? WP_A_SMG_Shard_01        Scrapper
        ?
        ? WP_E_Pistol_Bullet_01        K28
        ? WP_E_SGun_Bullet_01        Trenchgun
        ? WP_E_SMG_Bullet_01        PDW
        ? WP_E_AR_Energy_01        AR55
        ? WP_E_Sniper_Bullet_01        c-32boltaction
        ? WP_E_Pistol_Bullet_01_scrappy    RustyK28
        ? WP_E_SGun_Bullet_01_scrappy    rustytrench
        ? WP_E_SMG_Bullet_01_scrappy    rustypdw
        ? WP_E_AR_Energy_01_scrappy    rustyar55

    10. To add any other piece of equipment into your stash, repeat steps 8 and 9. This time instead of replacing the baseItemId with a weapon ID, replace the baseItemId with one of the items below.

Note: Any Armors or Helmets will have to have their correct durability. So where it says durability: -1 within the inventory entry replace the -1 with the correct armor value that the item should have. You can also modify the amount section for items such as ammo, stims, and other consumables.

        ? Mod_Korolev_Scanner_AlienCrystals
        ? ModKorolev_Scanner_HeavyMetals
        ? Mod_Korolev_Scanner_Veltecite
        ? Mod_Optic_2x_01
        ? Mod_Optic_4x_01
        ? Mod_Magazine_Light_03
        ? Mod_Magazine_Light_02
        ? Mod_Magazine_Light_01
        ? Mod_MagazineMedium_01
        ? Mod_Magazine_Heavy_01
        ? Mod_Magazine_Shotgun_01
        ? ModMuzzle_Small_Supressor_01
        ? ModMuzzle_Standard_Supressor_01
        ? Mod_Converter_Light_01
        ? Mod_Converter_Medium_01
        ? Mod_Converter_Heavy_01
        ? Mod_Converter_Shotgun_01
        ? Mod_ForeGrip_Angled_01
        ? Mod_RearGrip_01
        ? Mod_Tactical_Flashlight_01
        ? ModStockMarksman01
        ? ModStockStandard01
        ? Mod_MagazineMedium_02
        ? Mod_Magazine_Medium_03
        ? Mod_Magazine_Heavy_02
        ? Mod_Magazine_Heavy_03
        ? Mod_Magazine_Shotgun_02
        ? Mod_Magazine_Shotgun_03
        ? Mod_Magazine_Light_ReloadSpeed_01
        ? Mod_Magazine_Light_ReloadSpeed_02
        ? Mod_Magazine_Light_ReloadSpeed_03
        ? Mod_Magazine_Light_ReloadSpeed_04
        ? Mod_MagazineMedium_Reloadspeed_01
        ? Mod_Magazine_Medium_Reloadspeed_02
        ? Mod_Magazine_Medium_Reloadspeed_03
        ? Mod_Magazine_Medium_Reloadspeed_04
        ? Mod_Magazine_Heavy_ReloadSpeed_01
        ? Mod_Magazine_Heavy_ReloadSpeed_02
        ? Mod_Magazine_Heavy_ReloadSpeed_03
        ? Mod_Magazine_Heavy_ReloadSpeed_04
        ? Mod_Magazine_Shotgun_ReloadSpeed_01
        ? Mod_Magazine_Shotgun_ReloadSpeed_02
        ? Mod_Magazine_Shotgun_ReloadSpeed_03
        ? Mod_Magazine_Shotgun_ReloadSpeed_04
        ? Mod_Magazine_Light_EXTReload_01
        ? Mod_Magazine_Light_EXTReload_02
        ? ModMagazineMediumEXTReload01
        ? ModStockStandard02
        ? Mod_Stock_Standard_Equip_01
        ? Mod_Stock_Standard_Equip_02
        ? ModStockStandardADS01
        ? ModStockStandardADS02
        ? Mod__Stock_Standard_ADSEquip_01
        ? Mod_Stock_Standard_ADSEquip_02
        ? Mod_Stock_Marksman_02
        ? Mod_Stock_Marksman_Equip_01
        ? Mod_Stock_Marksman_Equip_02
        ? ModStockMarksmanADS01
        ? Mod_Stock_Marksman_ADS_02
        ? Mod_Stock_Marksman_ADSEquip_01
        ? Mod_Stock_Marksman_ADSEquip_02
        ? Mod_Muzzle_Small_Recoil_01
        ? Mod_Muzzle_Small_Recoil_02
        ? ModMuzzleSmallRecoil03
        ? ModMuzzleStandardRecoil01
        ? ModMuzzleStandardRecoil02
        ? Mod_Muzzle_Standard_Recoil_03
        ? Mod_Converter_Light_02
        ? Mod_Converter_Light_03
        ? ModConverterMedium02
        ? ModConverterMedium03
        ? Mod_Converter_Heavy_02
        ? Mod_Converter_Heavy_03
        ? Mod_Converter_Shotgun_02
        ? Mod_Converter_Shotgun_03
        ? Mod_Converter_Light_AIDMG_01
        ? Mod_Converter_Light_AIDMG_02
        ? Mod_Converter_Light_AIDMG_03
        ? Mod_Converter_Medium_AIDMG_01
        ? ModConverterMediumAIDMG02
        ? ModConverterMediumAIDMG03
        ? Mod_Converter_Shotgun_Slug_01
        ? Mod_ForeGrip_Angled_02
        ? Mod_ForeGrip_Equip_01
        ? Mod_ForeGrip_Equip_02
        ? Mod_ForeGrip_ADS_01
        ? Mod_ForeGrip_ADS_02
        ? Mod_ForeGrip_ADS_03
        ? Mod_RearGrip_02
        ? Mod_RearGrip_ADS_01
        ? Mod_RearGrip_ADS_02
        ? Mod_Optic_1x_01
        ? Mod_Optic_1x_02
        ? Mod_Optic_Variable_01
        ? Mod_Optic_8x_01
        ? Mod_Optic_6x_01
        ? ModKorolevScannerOil
        ?
        ? Consumable_Health_01
        ? Consumable_Health_02
        ? Consumable_Health_03
        ? Consumable_Health_04
        ? Consumable_Health_05
        ? Consumable_Health_06
        ? Consumable_SmokeGrenade_01Consumable_GasGrenade_01
        ? ConsumableAudioDecoy_01
        ? OTecStim_Adrenaline
        ? KineticShield
        ? Cloak
        ? KineticShieldDome
        ? HealingWard
        ? Consumable_Shield_01
        ? Consumable_Stamina_01
        ? Consumable_RoadFlare
        ? Bombardment
        ? ShockGrenade_01
        ? ShockGrenade_02
        ? ShockGrenade03
        ? ShockGrenade_04
        ? ShockGrenade05
        ?
        ? Shield01
        ? Shield02
        ? Shield03
        ? Shield04
        ? Shield05
        ? Shield_Tactical_01
        ? ShieldTactical02
        ? ShieldTactical03
        ? ShieldTactical04ShieldTactical05
        ? Shield_Restoration_01
        ? Shield_Restoration_02
        ? Shield_Restoration_03
        ? ShieldRestoration04
        ? Shield_Altered_01
        ? Shield_Altered_02
        ? Shield_Altered_03
        ?
        ? Helmet_01
        ? Helmet_02
        ? Helmet_03
        ? Helmet04
        ? Helmet_05
        ? Helmet_Tactical_01
        ? HelmetTactical02
        ? HelmetTactical03
        ? Helmet_Tactical_04
        ? Helmet_Tactical_05
        ? Helmet_Restoration_01
        ? Helmet_Restoration_02
        ? Helmet_Restoration_03
        ? Helmet_Restoration_04
        ? HelmetNV01
        ? Helmet_Altered_01
        ? Helmet_Altered_02
        ? Helmet_Altered_03
        ?
        ? Bag_01_broken
        ? Bag_01
        ? Bag_02
        ? Bag_03
        ? Bag_04
        ? Bag_05
        ? Bag_Altered_01
        ? Bag_Altered_02
        ? Bag_Altered_03
        ?
        ? TOOL_Mining_01
        ? TOOL_MineralScanner_01
        ? TOOL_Flashlight_01
        ? TOOL_Binocular_Basic_01



    11. After you are done modifying your inventory, CTRL + A within the text document or select all then CTRL + C or copy.

    12. Go back to MongoDB and click within the Value field of the inventory entry and press CTRL + A (Select All) and CTRL + V (Paste).

    13. Now press the update button on the right, and restart The Cycle: Frontier.

As long as everything was done correctly you should now have a new item in your inventory.

Troubleshooting

If for some reason the game does not load after modifying your inventory. This is how you can restore your inventory back to its previous state.

1. Go back into MongoDB, find the inventory entry, and edit it.

2. Click in the Value field and press CTRL + A then Delete.

3. Open the text document that you had saved earlier under the name Inventory Backup.

4. Copy all of the text from the Inventory Backup text document and press CTRL + C.

5. Click in the Value field within MongoDB under the Inventory entry and press CTRL + V.

6. Click Update on the right side of the entry.

7. Restart The Cycle: Frontier.
