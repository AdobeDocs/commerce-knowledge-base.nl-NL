---
title: "MDVA-30112: inconsistenties in verband met de reservering van grote aantallen"
description: De patch MDVA-30112 lost het probleem op waarbij u een onverwacht groot aantal [inconsistenties in het reserveringsbestand](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) in de lijst "voorraad_reservering" hebt. Voorbehoud inconsistenties omvatten niet-geregistreerde open orders en volledige orders die niet zijn geregistreerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.4.2.
exl-id: db74fb61-dfeb-4e99-8513-d36fd68d2267
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# MDVA-30112: inconsistenties bij de reservering van grote aantallen

Het flard MDVA-30112 lost de kwestie op waar u een onverwacht groot aantal [ inconsistenties van de reservering ](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) in de `inventory_reservation` lijst hebt. Voorbehoud inconsistenties omvatten niet-geregistreerde open orders en volledige orders die niet zijn geregistreerd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 geïnstalleerd is. Het probleem is opgelost in Adobe Commerce versie 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce over wolkeninfrastructuur 2.3.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.4 - 2.3.5-p2, 2.4.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De [ troep-grootte ](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#list-inconsistencies-command) waarde is de waarde voor hoeveel orden in één keer te laden. Als er meer orders zijn dan deze waarde, beschouwt Adobe Commerce de bestellingen met de status in behandeling als inconsistenties.

>[!NOTE]
>
>Er is een patch MDVA-33281 die drie andere problemen met betrekking tot inconsistentie in de inventaris verhelpt. Dit omvat een Fatale PHP fout wanneer het lopen `bin/magento inventory:reservation:list-inconsistencies` in CLI. Een ander probleem dat is opgelost, zijn dubbele gegevens in de lijst met inconsistenties. Ook de kwestie waar een reservering wordt gemaakt voordat een bestelling wordt geplaatst (vorige uitvoering op basis van reservering na geplaatste bestelling). Voor de oplossing, verwijs naar [ MDVA-33281: de kwesties van de inventarisinconsistentie ](/help/support-tools/patches-available-in-qpt-tool/v1-0-14/mdva-33281-magento-patch-inventory-inconsistency-issues.md) in onze steun kennisbasis.

<u> Eerste vereisten </u>:

U voert het volgende bevel in CLI in werking om reserveringsinconsistenties in de `inventory_reservation` lijst te vermelden:

```
magento inventory:reservation:list-inconsistencies
```

U ziet een onverwacht groot aantal reserveringsinconsistenties en/of het bevel voltooit nooit.

<u> Stappen om </u> te reproduceren:

1. Stel het volgende bevel in CLI in werking om de inconsistenties op te lossen:

   ```
   bin/magento inventory:reservation:list-inconsistencies -r | bin/magento inventory:reservation:create-compensations
   ```

1. Plaats drie bestellingen:
   * Wijs elk product toe.
   * Gebruik de betalingsmethode voor cheque/postwissel, zodat de status van de bestelling in behandeling is.
1. In de tabel `inventory_reservation` ziet u drie records met -1 hoeveelheid. Stel het volgende bevel in CLI in werking om het even welke inconsistenties te zien:

   ```
   bin/magento inventory:reservation:list-inconsistencies
   ```

   Dit geeft geen resultaten, wat juist is.

1. Stel het volgende bevel in CLI in werking:

   ```
   Execute bin/magento inventory:reservation:list-inconsistencies      --bunch-size 1
   ```

   U ziet dat de statusopdrachten voor &quot;in behandeling&quot; worden weergegeven als inconsistenties.

1. Stel het volgende bevel in CLI in werking:

   ```
   bin/magento inventory:reservation:list-inconsistencies      -r --bunch-size 1 | bin/magento inventory:reservation:create-compensations
   ```

<u> Verwachte resultaten </u>:

Adobe Commerce moet inconsistenties in &quot;hangende&quot; statusorders niet oplossen. De inconsistenties in de voorraden moeten worden opgelost voor orders met de status &quot;complete&quot;, &quot;closed&quot; en &quot;canceled&quot;.

<u> Ware resultaten </u>:

Wanneer er orden meer dan de gespecificeerde tros-grootte waarde zijn, beschouwt Adobe Commerce orden met &quot;hangende&quot;status als inconsistenties en voegt veelvoudige inconsistenties toe die verslagen voor de zelfde orde oplossen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
