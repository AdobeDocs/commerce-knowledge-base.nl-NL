---
title: 'MDVA-34023 patch: "No such entity with addressId" error'
description: De patch MDVA-34023 lost het probleem op waar "Geen dergelijke entiteit met addressId"fouten willekeurig op Webbrowser van een klant voorkomen.
exl-id: bdf8f97d-856a-4dd7-bf21-941d1493496c
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# MDVA-34023 patch: &quot;No such entity with addressId&quot; error

De MDVA-34023-patch lost het probleem op waarbij `No such entity with addressId` de fouten komen willekeurig op Webbrowser van een klant voor.

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.15 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce over wolkeninfrastructuur 2.3.1

**Compatibel met Adobe Commerce-versies:** Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Ga naar **Winkels** > **Instellingen** > **Configuratie** > **Tabblad Klanten** > **Persistent winkelwagentje**.
1. Set **Persistentie inschakelen** = *Ja*, set **Persistentie bij afmelden wissen** = *Nee*.    ![persistent_shopping_cart_magento_2.4.1.png](/help/support-tools/patches-available-in-qpt-tool/assets/persistent_shopping_cart_magento_2.4.1.png)
1. Maak een nieuwe klant en definieer de standaardadressen voor verzending en facturering.
1. Afmelden.
1. Meld u aan met de **Onthoud mij** Selectievakje geselecteerd.
1. Ga naar de `customer_entity` DB-tabel en wijzig de `default_billing` en `default_shipping` Id&#39;s voor niet-bestaande id&#39;s.
1. Afmelden.

<u>Verwachte resultaten</u>:

Er worden geen fouten weergegeven, zoals u had verwacht.

<u>Werkelijke resultaten</u>:

Het uitzonderingslogboek wordt geproduceerd:

```php
Exception.log:
{"0":"No such entity with addressId = XXXXX","1":"#0 /vendor\/magento\/module-customer\/Model\/AddressRegistry.php(49): Magento\\Framework
Exception
NoSuchEntityException::singleField('addressId', 'XXXXX')
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
