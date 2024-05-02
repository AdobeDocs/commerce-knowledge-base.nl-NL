---
title: 'ACSD-49877: video automatisch afspelen werkt niet op mobiele apparaten [!DNL Safari]'
description: Pas de ACSD-49877-patch toe om het Adobe Commerce-probleem op te lossen waarbij de video automatisch afspelen niet werkt op mobiele apparaten [!DNL Safari] wanneer de video rechtstreeks is gekoppeld aan een extern videobestand.
exl-id: 454f7cec-29b9-485b-93be-2a4f2eb77da7
feature: CMS
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-49877: video automatisch afspelen werkt niet op mobiele apparaten [!DNL Safari]

De ACSD-49877 verhelpt het probleem waarbij de optie voor automatisch afspelen op mobiele apparaten [!DNL Safari] werkt niet wanneer de video rechtstreeks aan een extern videobestand is gekoppeld. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 is geïnstalleerd. De patch-id is ACSD-49877. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de [!magento/quality-patches] naar de nieuwste versie te kopiëren en de compatibiliteit op de [[!DNL Quality Patches Tool]: Zoeken naar patches]. Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Automatisch afspelen van video werkt niet op mobiele apparaten [!DNL Safari] wanneer de video rechtstreeks aan een extern videobestand is gekoppeld en niet aan een streaming service.

<u>Vereisten</u>:
[!DNL Page Builder] worden geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Maak een nieuwe CMS-pagina en bewerk de **[!UICONTROL Content Value]** with [!DNL Page Builder].
1. Voeg een *Tab* -element aan de inhoud toevoegen en een *Video-element* in de *Tab*.
1. Klik nu op de tandwielknop om de knop *Video-element*.
1. Een koppeling naar een MP4-videobestand toevoegen aan de [!UICONTROL Video URL] veld.
1. Markeer de **[!UICONTROL Autoplay]** veld als *Ja*.
1. Klik op **[!UICONTROL Save]**.
1. De onlangs gemaakte pagina openen op [!DNL Safari] een iPhone gebruiken.

<u>Verwachte resultaten</u>

De optie Automatisch afspelen werkt op [!DNL Safari] een iPhone gebruiken.

<u>Werkelijke resultaten</u>

De optie Automatisch afspelen werkt niet [!DNL Safari] een iPhone gebruiken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
