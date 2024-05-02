---
title: "ACSD-51102: Catalogusregel toegepast op een groot aantal producten die niet correct zijn geïndexeerd"
description: Pas de ACSD-51102-patch toe om het Adobe Commerce-probleem op te lossen waarbij een catalogusregel die wordt toegepast op een groot aantal producten niet correct wordt geïndexeerd wanneer de regel wordt ingeschakeld door een geplande update.
feature: Catalog Management, Products
role: Admin
exl-id: 5c1c5f9c-9cce-4b11-8058-0e12a4bf93fd
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# ACSD-51102: Catalogusregel toegepast op een groot aantal producten die niet correct zijn geïndexeerd

De ACSD-51102-patch verhelpt het probleem waarbij een catalogusregel die op een groot aantal producten wordt toegepast, niet correct wordt geïndexeerd wanneer de regel wordt ingeschakeld door een geplande update. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 is geïnstalleerd. De patch-id is ACSD-51102. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een catalogusregel die op een groot aantal producten wordt toegepast wordt niet correct geïndexeerd wanneer de regel door een geplande update wordt toegelaten.

Vereisten:

* De baan van de kroon wordt opstelling en loopt elke minuut.

<u>Stappen om te reproduceren</u>:

1. Maak een grote catalogus met duizenden producten om de gebruiksduur van de *catalogusregel* indexeerprogramma&#39;s van meer dan 120 seconden wanneer catalogusregels worden ingeschakeld.
2. Twee catalogusregels maken met *Actief* status ingesteld op *Nee*.  Bijvoorbeeld: *Test 1* en *Test 2*. Elke regel zou alle producten in de catalogus moeten beïnvloeden en de indexer veroorzaken om meer dan 120 seconden te lopen.
3. Zorg ervoor dat de status van de indexeerder is *Gereed*.
4. Creeer geplande updates om deze twee regels toe te laten. *Test 2* schema begint kort na *Test 1*. Bijvoorbeeld met een verschil van 1 minuut.
5. Controleer de productprijzen op de winkelserver.

<u>Verwachte resultaten</u>

Kortingen op beide regels worden toegepast.

<u>Werkelijke resultaten</u>

Alleen de eerste regelkorting wordt toegepast.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] hulplijn.
