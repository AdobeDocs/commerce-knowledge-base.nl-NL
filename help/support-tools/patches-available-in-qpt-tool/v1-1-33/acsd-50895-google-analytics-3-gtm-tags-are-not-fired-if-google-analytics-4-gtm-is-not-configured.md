---
title: "ACSD-50895: [!DNL Google Analytics] 3 GTM-tags worden niet geactiveerd als [!DNL Google Analytics] 4 GTM is niet geconfigureerd."
description: Pas de ACSD-50895-patch toe om het Adobe Commerce-probleem op te lossen, waarbij [!DNL Google Analytics] 3 GTM-tags worden niet geactiveerd als [!DNL Google Analytics] 4 GTM is niet geconfigureerd.
role: Admin
exl-id: da48f6f1-a68b-4a9c-a79a-d7bd01b65dc2
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50895: [!DNL Google Analytics] 3 GTM-tags worden niet geactiveerd als [!DNL Google Analytics] 4 GTM is niet geconfigureerd

De ACSD-50895-patch verhelpt het probleem waarbij [!DNL Google Analytics] 3 GTM-tags worden niet geactiveerd als [!DNL Google Analytics] 4 GTM is niet geconfigureerd. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 is geïnstalleerd. De patch-id is ACSD-50895. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!DNL Google Analytics] 3 GTM-tags worden niet geactiveerd als [!DNL Google Analytics] 4 GTM is niet geconfigureerd.

<u>Stappen om te reproduceren</u>:

1. Meld u aan als beheerder.
1. Inschakelen **[!DNL Google Analytics 3]** en **[!DNL Google Tag Manager]** in **Beheerder** > **Winkel** > **Configuratie** > **Verkoop** > **GOOGLE API** > **Googles Analytics**.
1. Schakel de optie **[!DNL Google Analytics 4]** en **[!DNL Google Tag Manager]**.
1. Open de productpagina in de winkelruimte.

<u>Verwachte resultaten</u>:

De GTM-tags worden geactiveerd wanneer alleen **[!DNL Google Analytics]** 3 GTM is ingeschakeld.

<u>Werkelijke resultaten</u>:

De GTM-tags worden niet geactiveerd wanneer **[!DNL Google Analytics]** 4 GTM is uitgeschakeld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
