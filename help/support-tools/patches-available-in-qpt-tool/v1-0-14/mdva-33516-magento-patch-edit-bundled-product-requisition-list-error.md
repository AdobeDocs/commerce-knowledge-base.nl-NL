---
title: 'MDVA-33516 patch: edit bundled product Requisition List error'
description: Met de MDVA-33516-patch is het probleem verholpen waarbij u bij het bewerken van het type bundelproduct in de lijst Aanvraag wordt omgeleid naar een pagina met itemfouten in de lijst met aanvragen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: 76a16982-f977-4674-b05e-23f4ac355d52
feature: B2B, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-33516 patch: edit bundled product Requisition List error

Met de MDVA-33516-patch is het probleem verholpen waarbij u bij het bewerken van het type bundelproduct in de lijst Aanvraag wordt omgeleid naar een pagina met itemfouten in de lijst met aanvragen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.3.4

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce over cloudinfrastructuur 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Fout bij het bewerken van gebundelde producten op de aanvraaglijst.

<u>Vereisten</u>:

* B2B is geïnstalleerd.
* Aanvraaglijst is ingeschakeld.

<u>Stappen om te reproduceren</u>:

1. Maak een gebundeld product met twee eenvoudige producten.
1. Ga naar de pakketproductpagina en klik op **Aanpassen en toevoegen aan winkelwagentje** knop.
1. Selecteer een van de opties in het vervolgkeuzemenu en klik op **Toevoegen aan aanvraaglijst** om een nieuwe aanvraaglijst te maken. Voor gedetailleerde stappen raadpleegt u [Handboek Magento > Mijn lijst met aanvragen > Een aanvraaglijst maken](https://docs.magento.com/user-guide/customers/account-dashboard-requisition-lists.html#create-a-requisition-list) in onze gebruikershandleiding.
1. Ga naar de nieuw gemaakte aanvraaglijst (Mijn account > **Mijn aanvraaglijsten**).
1. Klik op de knop **Weergave** in de *Handelingen* kolom.
1. Klik op de knop **Bewerken** knop.

<u>Verwachte resultaten</u>:<br>

Geen fouten.

<u>Werkelijke resultaten</u>:

De pagina &quot;Uw aanpassing&quot;, met een afbeelding van het gebundelde product, de prijs en het volgende foutbericht:

```
Fatal error: Uncaught Error: Call to a member function isAvailableForCompare() on null in /var/www/html/var/view_preprocessed/pub/static/vendor/magento/module-catalog/view/frontend/templates/product/view/addto/compare.phtml:1 Stack trace: #0 /var/www/html/vendor/magento/framework/View/TemplateEngine/Php.php(59): include() #1 /var/www/html/vendor/magento/framework/View/Element/Template.php(271): Magento\Framework\View\TemplateEngine\Php->render(Object(Magento\Catalog\Block\Product\View\AddTo\Compare), '/var/www/html/v...', Array) #2 /var/www/html/vendor/magento/framework/View/Element/Template.php(301): Magento\Framework\View\Element\Template->fetchView('/var/www/html/v...') #3 /var/www/html/vendor/magento/framework/View/Element/AbstractBlock.php(1099): Magento\Framework\View\Element\Template->_toHtml() #4 /var/www/html/vendor/magento/framework/View/Element/AbstractBlock.php(1103): Magento\Framework\View\Element\AbstractBlock->Magento\Framework\View\Element   {closure} () #5 /var/www/html/vendor/magento/framework/View/Element/ in /var/www/html/var/view_preprocessed/pub/static/vendor/magento/module-catalog/view/frontend/templates/product/view/addto/compare.phtml
  on line 1
```

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
