---
title: 'ACSD-56858: discrepantie bij rolmachtigingen in B2B-bedrijfsbeheer'
description: Pas de ACSD-56858-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij rolinerechten onjuist worden weergegeven voor een beperkte bedrijfsbeheerder in de B2B-omgeving.
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
exl-id: d446f815-78bf-42ec-bc2b-a5934b15b416
source-git-commit: 4bf5deb1115705560acc8410441219943329c1a4
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-56858: discrepantie bij rolmachtigingen in B2B-bedrijfsbeheer

De ACSD-56858-patch verhelpt het probleem waarbij rolinerechten onjuist worden weergegeven voor een beperkte bedrijfsbeheerder in de B2B-omgeving. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.47 is geïnstalleerd. De patch-id is ACSD-56858. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De roltoestemmingen voor een beperkte bedrijfbeheerder in het milieu B2B worden onjuist getoond.

<u>Stappen om te reproduceren</u>:

1. Begin door vestiging een bedrijf, toevoegend een bedrijfbeheerder en bedrijfgebruikers.
1. Meld u aan als bedrijfsbeheerder bij de winkel en maak verschillende rollen voor verschillende gebruikers.
1. Wijs deze rollen toe zoals nodig, zoals het beperken van toegang voor sommige taken terwijl het toestaan van volledige toegang voor anderen.
1. Wijs deze rollen met volledige toegang tot een gebruiker buiten bedrijfadmin toe.
1. Meld u aan bij een niet-bedrijfs-beheergebruiker, bijvoorbeeld bij een bedrijf_manager.
1. Navigeren naar **[!UICONTROL Roles and permission]** en bewerk de rol.
1. Bericht dat de getoonde toestemmingen niet de toestemmingen aanpassen die in het gegevensbestand van het bedrijf voor die rolidentiteitskaart worden geplaatst.

<u>Verwachte resultaten</u>:

De rollen en de toestemming verschijnen correct voor de niet-bedrijf admin gebruiker.

<u>Werkelijke resultaten</u>:

De rollen verschijnen niet correct voor de niet-bedrijf admin gebruiker zoals per de gegevensbestandverslagen in de toestemmingslijst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
