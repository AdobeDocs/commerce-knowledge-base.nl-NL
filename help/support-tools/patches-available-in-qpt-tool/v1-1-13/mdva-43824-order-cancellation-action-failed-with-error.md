---
title: '''MDVA-43824: De annuleringsactie van de bestelling is mislukt met de fout "U hebt het item niet geannuleerd""'
description: 'De MDVA-43824-patch lost het probleem op waarbij de annuleringsactie van de bestelling is mislukt met de fout: *U hebt het item niet geannuleerd*. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-43824. De kwestie wordt volgens de planning opgelost in Adobe Commerce 2.4.5.'
exl-id: e4d839d6-84ed-4157-80a1-fd482fef897c
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-43824: De annuleringsactie van de orde is mislukt met fout &quot;U hebt het punt niet geannuleerd&quot;

Met de MDVA-43824-patch wordt het probleem opgelost waarbij de annuleringsactie van de bestelling is mislukt door de fout: *Je hebt het object niet geannuleerd*. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-43824. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.6 - 2.3.7-p3, 2.4.1 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bestelling die door een aangemelde klant is geplaatst, kan niet worden geannuleerd. De annuleringsactie van de orde is mislukt met de volgende fout:

```
Zend_Db_Statement_Exception: SQLSTATE[23000]: Integrity constraint violation: 1452 Cannot add or update a child row: a foreign key constraint fails (`mer33515_ee24developpbdevelop`.`salesrule_customer`, CONSTRAINT `SALESRULE_CUSTOMER_RULE_ID_SEQUENCE_SALESRULE_SEQUENCE_VALUE` FOREIGN KEY (`rule_id`) REFERENCES `sequence_salesrule` (`sequen), query was: INSERT INTO `salesrule_customer` () VALUES (){code}
```

<u>Stappen om te reproduceren</u>:

1. Een regel voor verkopen maken (het type coupon is &quot;Specific Coupon&quot; of &quot;No Coupon&quot;).
1. Ga naar de winkel en meld u aan als klant en voeg een product toe aan de winkelwagentje.
1. Ga naar het winkelwagentje en pas de regel van de winkelwagenprijs toe als de regel van de winkelwagentje een coupon heeft als &quot;Specific Coupon&quot;. De regels voor de winkelwagenprijs moeten met succes worden toegepast.
1. Ga naar de kassa en plaats de bestelling met elke betalingsmethode.
1. Ga naar Commerce Admin > **Verkoop** > **Orders**.
1. Open de volgorde die in Stap 4 is geplaatst.
1. Klik op de knop **Annuleren** knop.

<u>Verwachte resultaten</u>:

De volgorde is zonder fouten geannuleerd.

<u>Werkelijke resultaten</u>:

De annuleringsactie van de orde is mislukt met de volgende fout: *U hebt het item niet geannuleerd.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
