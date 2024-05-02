---
title: 'ACSD-51899: standaard verzendadres onjuist ingevuld.'
description: Pas de ACSD-51899-patch toe om het Adobe Commerce-probleem op te lossen waarbij het standaardverzendadres automatisch wordt ingevuld met een onjuist adres.
feature: Checkout
role: Admin
exl-id: 67100fcd-e98f-4740-8f1f-fcc820f4c75d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-51899: standaardverzendadres wordt niet correct ingevuld

De ACSD-51899-patch verhelpt het probleem waarbij het standaardverzendadres automatisch wordt ingevuld met een onjuist adres. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.35 is geïnstalleerd. De patch-id is ACSD-51899. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het standaardverzendadres wordt automatisch ingevuld met een onjuist adres

<u>Stappen om te reproduceren</u>:

1. Inschakelen **Ophalen in winkel** onder verzendmethode.
1. Maken *voorraad* en *bron*.
1. Maak een product en wijs het product aan de bron toe.
1. Voeg een product toe aan winkelwagentje.
1. Klikken op **Doorgaan naar Afhandeling** uit mini-kar.
1. Voer het teste-mailadres in en selecteer **Winkel kiezen**.
1. Klik op de knop **Winkel selecteren** en selecteer de locatie van de winkel die u wilt kiezen.
1. Klik op de knop **next** knop.
1. Ga naar de **Startpagina** door op het winkellogo te klikken.
1. Open de **Minikaart**.
1. Klik op de onderste hyperlink met de naam **Winkelwagentje weergeven en bewerken**.
1. Klikken **Doorgaan naar Afhandeling**.
1. Klik op de verzendknop op de verzendpagina.

<u>Verwachte resultaten</u>

Het veld Verzendadres blijft leeg, behalve voor *Land, regio en postcode*.

<u>Werkelijke resultaten</u>

Het standaardverzendadres wordt automatisch ingevuld *Ophalen in winkel* adres na het vernieuwen van de pagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
