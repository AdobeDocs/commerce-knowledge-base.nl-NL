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

De ACSD-56858-patch verhelpt het probleem waarbij rolinerechten onjuist worden weergegeven voor een beperkte bedrijfsbeheerder in de B2B-omgeving. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.47 is geïnstalleerd. De patch-id is ACSD-56858. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De roltoestemmingen voor een beperkte bedrijfbeheerder in het milieu B2B worden onjuist getoond.

<u> Stappen om </u> te reproduceren:

1. Begin door vestiging een bedrijf, toevoegend een bedrijfbeheerder en bedrijfgebruikers.
1. Meld u aan als bedrijfsbeheerder bij de winkel en maak verschillende rollen voor verschillende gebruikers.
1. Wijs deze rollen toe zoals nodig, zoals het beperken van toegang voor sommige taken terwijl het toestaan van volledige toegang voor anderen.
1. Wijs deze rollen met volledige toegang tot een gebruiker buiten bedrijfadmin toe.
1. Meld u aan bij een niet-bedrijfs-beheergebruiker, bijvoorbeeld bij een bedrijf_manager.
1. Navigeer naar **[!UICONTROL Roles and permission]** en bewerk de rol.
1. Bericht dat de getoonde toestemmingen niet de toestemmingen aanpassen die in het gegevensbestand van het bedrijf voor die rolidentiteitskaart worden geplaatst.

<u> Verwachte resultaten </u>:

De rollen en de toestemming verschijnen correct voor de niet-bedrijf admin gebruiker.

<u> Ware resultaten </u>:

De rollen verschijnen niet correct voor de niet-bedrijf admin gebruiker zoals per de gegevensbestandverslagen in de toestemmingslijst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
