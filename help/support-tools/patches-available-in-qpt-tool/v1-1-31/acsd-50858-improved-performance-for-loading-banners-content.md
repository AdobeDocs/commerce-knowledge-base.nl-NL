---
title: "ACSD-50858: Verbeterde prestaties voor het laden van banners'-inhoud"
description: Pas de ACSD-50858-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de bannerprestaties worden beïnvloed op de winkelwagentje/afhandelingspagina als gevolg van buitensporige DB-query's en een langere laadtijd.
exl-id: f9526d66-fc0e-44a0-8c72-b9f183004840
feature: Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-50858: Betere prestaties voor het laden van banners&#39;-inhoud

De ACSD-50858-patch verhelpt een probleem op het gebied van bannerprestaties op de pagina Kaart/Afhandeling: *excessieve DB-query&#39;s en langere laadtijd voor pagina&#39;s*. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.31 is geïnstalleerd. De patch-id is ACSD-50858. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prestaties van de banner worden beïnvloed op de winkelwagentje-/afhandelingspagina door *excessieve DB-query&#39;s en langere laadtijd voor pagina&#39;s*.

Dit probleem is opgelost door de manier te wijzigen waarop de inhoud van banners wordt geladen. Hierdoor is het aantal DB-query&#39;s met 99,99% en de laadtijd van de pagina met ~99% verminderd.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij Admin en maak een eenvoudig product.
1. Maak een klant, hetzij via Admin of de frontend, en voeg er een verzendadres voor toe.
1. Banners.php naar de map verplaatsen `magento_root/pub/` map.
1. Banners genereren met de opdracht  `php pub/banners.php` gebruiken. Het zal 10.000 eenvoudige banners en 1.000 banners met verkoopregels produceren.
1. Meld u aan bij de klant die u eerder op de voorzijde hebt gemaakt.
1. Voeg het eerder gemaakte product toe aan het winkelwagentje.
1. Ga naar de afhandelingspagina (Afrekenen/Kar).
1. Controleer de `banner/ajax/load` laadtijd verzoek:

   * Zonder `bin/magento dev:query-log:enable`
   * Met `bin/magento dev:query-log:enable`

     ```
     grep 'magento_banner_content' var/debug/db.log  | wc -l
     ```

<u>Verwachte resultaten</u>:

Daling van het aantal vragen van DB voor `magento_banner_content` en laadtijd wagentje-/uitcheckpagina.

<u>Werkelijke resultaten</u>:

Verhoging van het aantal vragen van DB voor `magento_banner_content` en laadtijd wagentje-/uitcheckpagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Aanvullende informatie

<u>banners.php content</u>:

```php
\Banner::class);
    $banner->setIsEnabled(
        \Magento\Banner\Model\Banner::STATUS_ENABLED
    )->setName(
        'Test Dynamic Block '.$i
    )->setTypes(
        ''
    )->setStoreContents(
        [0 => 'Dynamic Block Content '.$i]
    )->save();
}

$objectManager = \Magento\Framework\App\ObjectManager::getInstance();

/** @var \Magento\SalesRule\Model\Rule $salesRule */
$salesRule = $objectManager->create(\Magento\SalesRule\Model\Rule::class);
$salesRule->setData(
    [
        'name' => '50% Off ',
        'is_active' => 1,
        'customer_group_ids' => [\Magento\Customer\Model\GroupManagement::NOT_LOGGED_IN_ID],
        'coupon_type' => \Magento\SalesRule\Model\Rule::COUPON_TYPE_NO_COUPON,
        'conditions' => [
            [
                'type' => \Magento\SalesRule\Model\Rule\Condition\Address::class,
                'attribute' => 'base_subtotal',
                'operator' => '>',
                'value' => 0
            ]
        ],
        'simple_action' => 'by_percent',
        'discount_amount' => 50,
        'discount_step' => 0,
        'stop_rules_processing' => 1,
        'website_ids' => [
           1
        ]
    ]
);
$salesRule->save();

for ($i = 0; $i < 1000; $i++) {

    $banner = $objectManager->create(\Magento\Banner\Model\Banner::class);
    $banner->setData(
        [
            'name' => 'Get 50% Off ',
            'is_enabled' => \Magento\Banner\Model\Banner::STATUS_ENABLED,
            'types' => [], /*Any Banner Type*/
            'store_contents' => ['<img src="http://example.com/banner_40_percent_off.png" />'],
            'banner_sales_rules' => [$salesRule->getId()],
        ]
    );
    $banner->save();
}
```

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
