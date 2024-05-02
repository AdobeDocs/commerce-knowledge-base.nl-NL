---
title: 'ACSD-52906: Het probleem met X-Magento-Vary cookie oplossen voor het in cache plaatsen van aangemelde klanten'
description: Pas de ACSD-52906-patch toe om het Adobe Commerce-probleem op te lossen waarbij het X-Magento-Vary-cookie onjuist is ingesteld voor aangemelde klanten.
feature: Cache
role: Admin, Developer
exl-id: 863e0808-9208-467d-8d56-9dd7a7f4354d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-52906: Het oplossen van X-Magento-Vary koekjeskwestie voor login klanten

De ACSD-52906-patch verhelpt het probleem waarbij het X-Magento-Vary-cookie onjuist is ingesteld voor aangemelde klanten. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.36 is geïnstalleerd. De patch-id is ACSD-52906. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

X-Magento-Vary koekje wordt verkeerd geplaatst voor het programma geopende klanten die tot het zelfde klantensegment behoren, veroorzakend ongepast caching voor sommige pagina&#39;s.

<u>Vereisten</u>:

Adobe Commerce Inventory management (MSI)-modules worden geïnstalleerd en ingeschakeld.

<u>Stappen om te reproduceren</u>:

1. Configureren [!DNL Varnish] of [!DNL Fastly] cache.
1. Creeer een nieuw klantensegment en wijs het aan toe *Geregistreerd* klanten.
1. Maak twee klanten, bijvoorbeeld klant1 en klant2.
1. Wis de cache.
1. Meld u aan als klant1 en ga naar de startpagina.
1. Open een incognitopagina in uw browser.
1. Ga naar een andere pagina dan de startpagina.
1. Meld u aan als klant2.
1. Ga naar de startpagina.
1. Controleer of de pagina in het cachegeheugen is opgeslagen in de browserDev-console.

<u>Verwachte resultaten</u>:

De pagina wordt opgehaald uit de cache.

<u>Werkelijke resultaten</u>:

De pagina is niet in cache geplaatst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
