---
title: '"ACSD-53658: **[!UICONTROL Recently Viewed Product]** gegevens zijn niet correct bijgewerkt in de weergave Opslaan.'''
description: Pas de ACSD-53658-patch toe om het Adobe Commerce-probleem op te lossen waar **[!UICONTROL Recently Viewed Product]** gegevens worden niet correct bijgewerkt in de winkelweergave.
feature: CMS, Personalization
role: Admin, Developer
exl-id: 4086dcee-37e5-4393-9048-ce19a2d248e9
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-53658: **[!UICONTROL Recently Viewed Product]** gegevens worden niet correct bijgewerkt in de winkelweergave

De ACSD-53658-patch verhelpt het probleem waarbij **[!UICONTROL Recently Viewed Product]** gegevens worden niet correct bijgewerkt in de winkelweergave. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 is geïnstalleerd. De patch-id is ACSD-53658. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De **[!UICONTROL Recently Viewed Product]** gegevens worden niet correct bijgewerkt in de winkelweergave.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij het deelvenster Beheer.
1. Maak een tweede opslagweergave voor de standaardwebsite.
1. Maak een eenvoudig product.
1. Stel een andere productnaam in voor de nieuwe winkelweergave.
1. Een **[!UICONTROL Recently Viewed Product]** widget.
1. Configureer deze widget voor weergave op de startpagina.
1. Open de productpagina in de Storefront vanuit de standaardwinkelweergave.
1. Open de startpagina.
1. Schakel over naar de tweede winkelweergave met de opslagschakelaar.

<u>Verwachte resultaten</u>:

De productnaam wordt bijgewerkt in de widget.

<u>Werkelijke resultaten</u>:

De productnaam wordt niet bijgewerkt in de widget.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
