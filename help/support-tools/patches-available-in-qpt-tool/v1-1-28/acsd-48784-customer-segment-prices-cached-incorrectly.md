---
title: "ACSD-48784: Prijzen van klantensegmenten die onjuist tussen klantengroepen zijn in de cache zijn geplaatst"
description: Pas de ACSD-48784-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de prijzen van klantensegmenten onjuist tussen klantgroepen worden vastgelegd.
exl-id: 6be11fd0-5c93-4ac7-8664-7e2a289c9e38
feature: Admin Workspace, Cache, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-48784: Prijzen van klantensegmenten worden onjuist in cache geplaatst tussen klantengroepen

De ACSD-48784-patch verhelpt het probleem waarbij de prijzen van klantensegmenten onjuist tussen klantengroepen worden vastgelegd. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 is geïnstalleerd. De patch-id is ACSD-48784. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De de segmentprijzen van de klant worden in het voorgeheugen ondergebracht verkeerd tussen klantengroepen.

<u>Vereisten</u>:

Configureren [!DNL Varnish] of [!DNL Fastly].

<u>Stappen om te reproduceren</u>:

1. Schakel het in cache plaatsen van volledige pagina&#39;s in uw winkel in.
1. Meld u aan bij de site als een gebruiker met speciale klantgroepprijzen.
1. Ga naar een productpagina voor een product met speciale klantgroepprijzen. Waarnemen van *speciale prijs*.
1. Open in een aparte browser dezelfde productpagina als een gastgebruiker zonder u aan te melden. Neem de normale prijs waar.
1. Open de beheerinterface van Adobe Commerce en wis de Adobe Commerce en [!DNL Fastly] cache voor deze winkel.
1. Verwijder in de aangemelde browser de `X-Magento-Vary` cookie.
1. Laad in de aangemelde browser dezelfde productpagina meerdere keren opnieuw totdat het in cache plaatsen volledig is leeggemaakt.
1. In niet-het programma geopende browser, herlaad de productpagina om de prijs van de klantengroep nu te zien.

<u>Verwachte resultaten</u>:

Op de productpagina wordt de juiste prijs voor specifieke klantengroepen weergegeven.

<u>Werkelijke resultaten</u>:

* Gastgebruikers zien de speciale aangemelde gebruikersprijs.
* Als het product eenmaal is toegevoegd, wordt op de minikaart de juiste prijs vermeld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
