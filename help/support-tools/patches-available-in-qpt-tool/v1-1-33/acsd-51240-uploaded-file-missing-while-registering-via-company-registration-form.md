---
title: "ACSD-51240: Geüploade bestand ontbreekt bij registratie via bedrijfsregistratieformulier"
description: Pas de ACSD-51240-patch toe om het Adobe Commerce-probleem op te lossen waarbij het geüploade bestand ontbreekt tijdens de registratie via het bedrijfsregistratieformulier.
exl-id: e5822c54-4e77-46b0-84b6-5e25c3845974
source-git-commit: e1fe8936c56f422ae591c6424d8a72621093db81
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51240: Geüploade bestand ontbreekt bij registratie via bedrijfsregistratieformulier

>[!NOTE]
>
>Deze pleister wordt vervangen door [ACSD-55628](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55628-upload-file-company-registration-form-replace-file-customer-attribute-storefront.md).

De ACSD-51240-patch verhelpt het probleem waarbij het geüploade bestand ontbreekt tijdens de registratie via het bedrijfsregistratieformulier. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 is geïnstalleerd. De patch-id is ACSD-51240. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 &lt; 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Probleem

Geüpload bestand ontbreekt bij registratie via bedrijfsregistratieformulier.

<u>Stappen om te reproduceren</u>:

1. Set **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B >Company]** > **[!UICONTROL Enable]** = *Ja*.
1. Creeer een nieuw klantenattribuut van **[!UICONTROL File]** tekst, set **[!UICONTROL Show in StoreFront]** = *Ja* en selecteert u **[!UICONTROL all forms]**.
1. Creeer een nieuw bedrijf op de Storefront en upload een beeld voor het nieuwe attribuut.
Open het bedrijf en de admin gebruiker op de Storefront.

<u>Verwachte resultaten</u>:

Het geüploade bestand wordt weergegeven.

<u>Werkelijke resultaten</u>:

Het geüploade bestand wordt niet weergegeven op de bedrijfspagina of op de pagina met beheerdersklanten in het dialoogvenster [!UICONTROL Commerce Admin].

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
