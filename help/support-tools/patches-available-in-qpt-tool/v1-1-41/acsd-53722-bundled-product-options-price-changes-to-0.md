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

De ACSD-53722-patch verhelpt het probleem waarbij de prijs van de gebundelde productopties verandert in $0 wanneer geplande updates voor verschillende bereiken actief worden. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 wordt geïnstalleerd. De patch-id is ACSD-53722. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prijs van gebundelde productopties verandert in $0 wanneer geplande updates voor verschillende bereiken actief worden.

<u> Stappen om </u> te reproduceren:

1. Maak twee websites, A en B.
1. Stel de configuratie in onder **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** = **[!UICONTROL Website]** .
1. Een gebundeld product met een vaste prijs maken op websites A en B:

   * Gebundelde productprijs = Vast = *0*

1. Voeg één eenvoudig product als drop-down optie voor de bundel toe. Stel de volgende prijzen in:

   * De eenvoudige alle opslagmeningen van het product allen binnen gebundelde optie = *120*
   * De eenvoudige prijs van de websiteA van het product binnen gebundelde optie = *130*
   * De eenvoudige B prijs van de website van het product binnen gebundelde optie = *140*

1. Plan een update om het gebundelde product op website A uit te schakelen.

<u> Verwachte resultaten </u>:

De geplande update voor website A heeft geen invloed op de prijs van website B.

<u> Ware resultaten </u>:

Na de geplande update wordt de prijs van de gebundelde productoptie op website B gewijzigd in **$0**.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
