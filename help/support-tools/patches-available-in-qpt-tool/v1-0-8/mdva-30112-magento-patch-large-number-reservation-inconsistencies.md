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

De MDVA-30112-patch lost het probleem op waarbij u onverwacht veel [inconsistenties in het voorbehoud](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) in de `inventory_reservation` tabel. Voorbehoud inconsistenties omvatten niet-geregistreerde open orders en volledige orders die niet zijn geregistreerd. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce over wolkeninfrastructuur 2.3.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.4 - 2.3.5-p2, 2.4.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De [troebelgrootte](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#list-inconsistencies-command) waarde is de waarde voor het aantal orders dat tegelijkertijd moet worden geladen. Als er meer orders zijn dan deze waarde, beschouwt Adobe Commerce de bestellingen met de status in behandeling als inconsistenties.

>[!NOTE]
>
>Er is een patch MDVA-33281 die drie andere problemen met betrekking tot inconsistentie in de inventaris verhelpt. Dit omvat een Fatale PHP fout tijdens het uitvoeren `bin/magento inventory:reservation:list-inconsistencies` in de CLI. Een ander probleem dat is opgelost, zijn dubbele gegevens in de lijst met inconsistenties. Ook de kwestie waar een reservering wordt gemaakt voordat een bestelling wordt geplaatst (vorige uitvoering op basis van reservering na geplaatste bestelling). Raadpleeg voor de oplossing: [MDVA-33281: problemen in verband met inventarisinconsistentie](/help/support-tools/patches-available-in-qpt-tool/v1-0-14/mdva-33281-magento-patch-inventory-inconsistency-issues.md) in onze kennisbasis voor ondersteuning.

<u>Vereisten</u>:

U stelt het volgende bevel in CLI in werking om van reserveringsinconsistenties in de lijst te maken `inventory_reservation` tabel:

```
magento inventory:reservation:list-inconsistencies
```

U ziet een onverwacht groot aantal reserveringsinconsistenties en/of het bevel voltooit nooit.

<u>Stappen om te reproduceren</u>:

1. Stel het volgende bevel in CLI in werking om de inconsistenties op te lossen:

   ```
   bin/magento inventory:reservation:list-inconsistencies -r | bin/magento inventory:reservation:create-compensations
   ```

1. Plaats drie bestellingen:
   * Wijs elk product toe.
   * Gebruik de betalingsmethode voor cheque/postwissel, zodat de status van de bestelling in behandeling is.
1. U ziet drie records met een hoeveelheid van -1 in het dialoogvenster `inventory_reservation` tabel. Stel het volgende bevel in CLI in werking om het even welke inconsistenties te zien:

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

<u>Verwachte resultaten</u>:

Adobe Commerce moet inconsistenties in &quot;hangende&quot; statusorders niet oplossen. De inconsistenties in de voorraden moeten worden opgelost voor orders met de status &quot;complete&quot;, &quot;closed&quot; en &quot;canceled&quot;.

<u>Werkelijke resultaten</u>:

Wanneer er orden meer dan de gespecificeerde tros-grootte waarde zijn, beschouwt Adobe Commerce orden met &quot;hangende&quot;status als inconsistenties en voegt veelvoudige inconsistenties toe die verslagen voor de zelfde orde oplossen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
