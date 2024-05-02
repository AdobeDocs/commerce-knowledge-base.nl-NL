---
title: "ACSD-51853: gekopieerde tekststijlen worden niet toegepast met behulp van de paginaontwikkelaar"
description: Pas de ACSD-51853-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de gekopieerde tekststijlen niet worden toegepast wanneer de paginaontwikkelaar wordt gebruikt.
feature: Page Builder
role: Admin
exl-id: 1efd3147-1ae0-468b-af04-1632fbaaefda
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-51853: gekopieerde tekststijlen worden niet toegepast met behulp van de paginaontwikkelaar

De ACSD-51853-patch verhelpt het probleem waarbij de gekopieerde tekststijlen niet worden toegepast wanneer de paginaontwikkelaar wordt gebruikt. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.34 is geïnstalleerd. De patch-id is ACSD-51853. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gekopieerde tekststijlen worden niet toegepast wanneer de paginaontwikkelaar wordt gebruikt

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij Beheer.
1. Ga naar > **content** > **pagina&#39;s** > **Een pagina openen** > **Bewerken met Page Builder**.
1. Rij slepen en *Tekst* van **[!UICONTROL Elements]**.
1. Kopiëren **verrijkte inhoud**, plakt u die tekst in een **[!UICONTROL Page Builder]**.

<u>Verwachte resultaten</u>

De gekopieerde tekst wordt met alle stijlen geplakt.

<u>Werkelijke resultaten</u>

De gekopieerde tekst wordt als platte tekst geplakt en alle stijlen gaan verloren.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
