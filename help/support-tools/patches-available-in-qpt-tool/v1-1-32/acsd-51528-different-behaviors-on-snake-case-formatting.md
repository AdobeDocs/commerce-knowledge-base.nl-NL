---
title: 'ACSD-51528: verschillende gedragingen bij slang_case-opmaak'
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

De ACSD-51528-patch corrigeert verschillende gedragingen bij het opmaken van slangen_hoofdletters. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.32 wordt geïnstalleerd. De patch-id is ACSD-51528. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De verschillende gedragingen bij slang_case-opmaak.

<u> Stappen om </u> te reproduceren:

1. Test de functie `\Magento\Framework\Api\DataObjectHelper::populateWithArray` met verschillende eigenschapnamen.
1. De eigenschappen met namen zoals *NewPName* zouden in *new_p_name* moeten worden omgezet, in plaats daarvan worden zij omgezet aan *new_pname*.
1. Ook, wanneer het gebruiken van de *getNewPName* functie in het voorwerp, *ongeldig* zal zijn teruggekeerd omdat *Abstract model* correct de vraag aan *new_p_name* zal omzetten die beide functies onverenigbaar met elkaar maken.

<u> Verwachte resultaten </u>

De functie **[!UICONTROL populateWithArray]** moet de objecteigenschappen correct transformeren in slang_case, zodat deze compatibel zijn met de **[!DNL AbstractModel's]** `Getters` en `Setters` .

<u> Ware resultaten </u>

Wanneer u de functie **[!UICONTROL populateWithArray]** gebruikt, zullen objecteigenschappen die twee of meer hoofdletters in een rij in de naam bevatten, ertoe leiden dat de transformatie van snake_case onjuist is in de uiteindelijke gegevensarray.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
