---
title: 'ACSD-53722: Prijswijzigingen van gebundelde productopties in $0'
description: Pas de ACSD-53722-patch toe om het Adobe Commerce-probleem op te lossen waarbij de prijs van de gebundelde productopties verandert in $0 wanneer geplande updates voor verschillende bereiken actief worden.
feature: Products
role: Admin, Developer
exl-id: da4c25ac-78bc-4d4e-a55e-826924a099e9
source-git-commit: e587b70a270bca624fb60a1b0940c05221da3aef
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-53722: Prijswijzigingen van gebundelde productopties in $0

De ACSD-53722-patch verhelpt het probleem waarbij de prijs van de gebundelde productopties verandert in $0 wanneer geplande updates voor verschillende bereiken actief worden. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 is geïnstalleerd. De patch-id is ACSD-53722. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prijs van gebundelde productopties verandert in $0 wanneer geplande updates voor verschillende bereiken actief worden.

<u>Stappen om te reproduceren</u>:

1. Maak twee websites, A en B.
1. Configuratie instellen onder **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** = **[!UICONTROL Website]**.
1. Een gebundeld product met een vaste prijs maken op websites A en B:

   * Gebundelde productprijs = Vast = *0*

1. Voeg één eenvoudig product als drop-down optie voor de bundel toe. Stel de volgende prijzen in:

   * Eenvoudig product: alle winkelweergaven, prijs in gebundelde optie = *120*
   * De website van het eenvoudige product A prijs binnen gebundelde optie = *130*
   * B-prijs van eenvoudige website van product binnen gebundelde optie = *140*

1. Plan een update om het gebundelde product op website A uit te schakelen.

<u>Verwachte resultaten</u>:

De geplande update voor website A heeft geen invloed op de prijs van website B.

<u>Werkelijke resultaten</u>:

Na de geplande update wordt de prijs van de gebundelde productoptie op website B gewijzigd in **$0**.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
