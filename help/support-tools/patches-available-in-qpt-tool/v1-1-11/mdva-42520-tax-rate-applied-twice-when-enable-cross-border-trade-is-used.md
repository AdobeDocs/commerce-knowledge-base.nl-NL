---
title: '"MDVA-42520: tweemaal toegepast belastingtarief wanneer "grensoverschrijdende handel inschakelen" wordt gebruikt"'
description: De MDVA-42520-patch voorziet in de mogelijkheid dat het belastingtarief tweemaal wordt toegepast wanneer het **Grensoverschrijdende handel inschakelen* wordt gebruikt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 is geïnstalleerd. De patch-id is MDVA-42520. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: c1ca44eb-fe92-4f28-807a-3a4563433386
feature: Catalog Management, Orders, Taxes
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# MDVA-42520: tweemaal toegepast belastingtarief bij gebruik van &quot;Enable Cross Border Trade&quot;

De MDVA-42520-patch voorziet in de mogelijkheid dat het belastingtarief tweemaal wordt toegepast wanneer het **Grensoverschrijdende handel inschakelen** wordt gebruikt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 is geïnstalleerd. De patch-id is MDVA-42520. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het belastingtarief wordt tweemaal toegepast wanneer **Grensoverschrijdende handel inschakelen** wordt gebruikt.

<u>Stappen om te reproduceren</u>:

1. Inschakelen **Bedrijf**, **Gedeelde catalogus**, en **Offerte**
1. Configureer belastingen volgens de schermafbeelding. Zorg ervoor dat u **Grensoverschrijdende handel**.

   ![belastinginstellingen](/help/support-tools/patches-available-in-qpt-tool/assets/tax_settings_1.png){width="700"}

1. Een belastingtarief voor Duitsland instellen (10%).
1. Maak een belastingregel om het belastingtarief toe te passen.
1. Een bedrijf en een aangepaste gedeelde catalogus maken.
1. Maak een product met een prijs van 100 en neem het op in de aangepaste gedeelde catalogus met een prijskorting van 20%.
1. Een klant met een Duits adres maken en dit aan het bedrijf toewijzen
1. Voeg tien producten toe aan de kaart als klant.
1. Ga naar het winkelwagentje en vraag een prijsopgave.
1. Open dit citaat op de achtergrond en probeer om een extra korting van 10% toe te voegen.

<u>Verwachte resultaten</u>:

Subtotaal prijsopgave (inclusief btw) en Eindtotaal prijsopgave (inclusief btw) = $720

<u>Werkelijke resultaten</u>:

Subtotaal prijsopgave (inclusief btw) en Eindtotaal prijsopgave (inclusief btw) = $ 649,50.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
