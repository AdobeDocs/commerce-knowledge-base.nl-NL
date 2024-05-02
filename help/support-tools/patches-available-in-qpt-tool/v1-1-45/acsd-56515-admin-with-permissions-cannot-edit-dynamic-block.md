---
title: 'ACSD-56515: Admin with website-level permissions cannot edit [!UICONTROL Dynamic Block]'
description: Pas de ACSD-56515-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de beheerder met bevoegdheden op websiteniveau het volgende niet kan toevoegen of bewerken [!UICONTROL Dynamic Block].
feature: Roles/Permissions, Admin Workspace
role: Admin, Developer
exl-id: 5aa6b11e-b467-4076-ad36-162966cbf6df
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-56515: beheer met bevoegdheden op websiteniveau kan geen bewerkingen uitvoeren [!UICONTROL Dynamic Block]

De ACSD-56515-patch verhelpt het probleem waarbij de beheerder met bevoegdheden op websiteniveau de taak niet kan toevoegen of bewerken [!UICONTROL Dynamic Block]. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 is geïnstalleerd. De patch-id is ACSD-56515. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De beheerder met bevoegdheden op websiteniveau kan de [!UICONTROL Dynamic Block].

<u>Stappen om te reproduceren</u>:

1. Maak een secundaire website met opslag en voorvertoning.
1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]** en maak een gebruikersrol die beperkt is tot het secundaire websitebereik met alle beschikbare bronnen.
1. Maak een beheerder met de hierboven gemaakte rol.
1. Meld u aan met de beperkte beheerder en maak een [!UICONTROL Dynamic Block].

<u>Verwachte resultaten</u>:

De beheerder met beperkingen van de website kan een [!UICONTROL Dynamic Block].

<u>Werkelijke resultaten</u>:

De volgende fout treedt op: *Er zijn meer machtigingen nodig om dit item weer te geven*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
