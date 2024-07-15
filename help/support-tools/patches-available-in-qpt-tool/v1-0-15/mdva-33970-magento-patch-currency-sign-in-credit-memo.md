---
title: 'MDVA-33970 patch: currency sign in credit memo'
description: De patch MDVA-33970 lost het probleem op waarbij een Dollar ($)-teken werd weergegeven in plaats van de gelokaliseerde valuta in een creditmemo. Dit gebeurt wanneer een bereik **Website** wordt gebruikt voor een kenmerk **Price**.
exl-id: 47a03067-86ef-4a55-8c21-921781062b53
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# MDVA-33970 patch: currency sign in credit memo

De patch MDVA-33970 lost het probleem op waarbij een Dollar ($)-teken werd weergegeven in plaats van de gelokaliseerde valuta in een creditmemo. Dit komt voor wanneer het werkingsgebied van de a **Website** voor a **Prijs** attributen wordt gebruikt.

Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 geïnstalleerd is. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.3.4-p2

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur en Adobe Commerce op-gebouw 2.3.4 - 2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Voorwaarden </u>:

In dit voorbeeld worden de volgende instellingen gebruikt:

* 2 Websites bestaan - elk heeft a **Opslag** en a **Mening van de Opslag**.
* De **StandaardConfig** heeft de Dollar van Singapore als **Valuta** (**Opslag > Configuratie > Algemeen > de Opstelling van de Valuta**):
   * **BasisValuta** = *de Dollar van Singapore*
   * **StandaardValuta van de Vertoning** = *de Dollar van Singapore*
   * **Toegestane Valuta&#39;s** = *de Dollar van Singapore*
* **Website 1** heeft a **Standaard Config**.
* **Website 2** heeft Maleisische Ringgit als **Valuta**:
   * **= *Maleisische Ringgit***
   * **StandaardValuta van de Vertoning** = *Maleisische Ringgit*
   * **Toegestane Valuta&#39;s** = *Maleisische Ringgit*
* Ga naar **Opslag > de Symbolen van de Valuta**, en Reeks:
   * **MYR (Maleisische Ringgit)** = *RM*
   * **SGD (de Dollar van Singapore)** = *SGD* (**Norm van het Gebruik** = *Gecontroleerd*)
* Sommige **Product** bestaat.

<u> Stappen om </u> te reproduceren:

1. Maak een **Orde** van **Website 2** (u kunt opstelling het als Gebrek om extra montages te vermijden).
1. Login aan **Admin**.
1. Open de nieuwe volgorde.
1. Controle dat het **Symbool van de Valuta** = *RM*.
1. Creeer een **Factuur**.
1. Controle dat het **Symbool van de Valuta** = *RM* in de factuur.
1. Creeer a **Memo van het Krediet**.
1. Controle dat het **Symbool van de Valuta** ** * = *RM* in het **Memo van het Krediet**.
1. Open het **lusje van de Memo&#39;s van het Krediet** in **Orde**.
1. Controleer het **Symbool van de Valuta** in het net.
1. Open **Verkoop > de Memo&#39;s van de Krediet**.
1. Controleer het **Symbool van de Valuta** in het net.

<u> Verwachte resultaten </u>:

Het correcte gelokaliseerde valutasymbool wordt gebruikt, zoals verwacht.

<u> Ware resultaten </u>:

Het Dollar-teken ($) wordt gebruikt, ook al is dit niet ingesteld in de beheerinstellingen.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in het hulpmiddel QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
