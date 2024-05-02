---
title: 'ACSD-51574: Afbeelding niet bijgewerkt op voorzijde bij vervanging door een andere afbeelding'
description: Pas de ACSD-51574-patch toe om het Adobe Commerce-probleem op te lossen waarbij de afbeelding niet op de voorzijde wordt bijgewerkt nadat deze door een andere afbeelding is vervangen.
feature: Configuration
role: Admin
exl-id: a6f26126-71c3-43c2-bba4-60a914d7ec11
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-51574: Afbeelding niet vooraf bijgewerkt wanneer deze wordt vervangen door een andere afbeelding

De ACSD-51574-patch verhelpt het probleem waarbij de afbeelding niet op de voorzijde wordt bijgewerkt nadat deze door een andere afbeelding is vervangen. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.37 is geïnstalleerd. De patch-id is ACSD-51574. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De afbeelding wordt niet op de voorgrond bijgewerkt nadat u deze hebt vervangen door een andere afbeelding.

<u>Stappen om te reproduceren</u>:

1. Maak een product met een paar afbeeldingen.
1. Bewerk het product en upload een afbeelding met een bekende naam (Voorbeeld: *image.jpg*).
1. Sla het product op.
1. Bewerk het product opnieuw en verwijder de oude versie van de afbeelding en upload de nieuwe versie van de afbeelding met dezelfde naam. **Zorg ervoor dat de nieuwe versie zichtbaar anders is om het probleem te zien.**
1. Sla het product op. Zowel de beheerder als de voorzijde geeft de afbeeldingen weer.
1. Bewerk het product opnieuw en upload dezelfde nieuwe afbeelding opnieuw (met dezelfde naam).
1. Sla het product op en controleer de productpagina op de voorzijde.

<u>Verwachte resultaten</u>:

De afbeelding die de tweede keer wordt geüpload, moet de nieuwe afbeelding zijn, samen met de naam van de gewijzigde afbeelding.

<u>Werkelijke resultaten</u>:

De afbeelding die de tweede keer wordt geüpload, is de eerder verwijderde oudere versie van de afbeelding in plaats van dezelfde nieuwe afbeelding.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
