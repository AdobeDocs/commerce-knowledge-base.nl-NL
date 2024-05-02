---
title: 'ACSD-51528: verschillend gedrag bij slang_case-opmaak'
description: Pas de ACSD-51528-patch toe om het Adobe Commerce-probleem op te lossen, waarbij er verschillende gedragingen optreden voor slang_case-opmaak.
exl-id: dd878321-8032-41f3-8dcd-acb0cc023b44
feature: Variables
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-51528: verschillende gedragingen bij slang_case-opmaak

De ACSD-51528-patch corrigeert verschillende gedragingen bij het opmaken van slangen_hoofdletters. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.32 is geïnstalleerd. De patch-id is ACSD-51528. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De verschillende gedragingen bij slang_case-opmaak.

<u>Stappen om te reproduceren</u>:

1. Test de `\Magento\Framework\Api\DataObjectHelper::populateWithArray` gebruiken met verschillende namen van eigenschappen.
1. De eigenschappen met namen als *NewPName* moeten worden omgezet in *new_p_name* in plaats daarvan worden ze omgezet in *new_name*.
1. Ook, wanneer het gebruiken van *getNewPName* functie in het object, *null* wordt geretourneerd omdat de *Abstract model* zal correct de vraag omzetten aan *new_p_name* beide functies onverenigbaar met elkaar maken.

<u>Verwachte resultaten</u>

De **[!UICONTROL populateWithArray]** functie moet de objecteigenschappen correct omzetten in slang_case, zodat deze compatibel zijn met de **[!DNL AbstractModel's]** `Getters` en `Setters`.

<u>Werkelijke resultaten</u>

Wanneer u de opdracht **[!UICONTROL populateWithArray]** functie, om het even welke objecten eigenschappen die twee of meer hoofdletters in een rij in zijn naam bevatten zullen de snake_case transformatie veroorzaken om in de definitieve gegevensserie onjuist te zijn.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
