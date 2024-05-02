---
title: '''ACSD-56842: Uitgestelde proxy''s en proxyfabrieken ontbreken na het uitvoeren van ''setup:di:compileren".'
description: Pas de ACSD-56842-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de uitgestelde proxy's en proxyfabrieken ontbreken nadat 'setup' is uitgevoerd:di:compileren".
feature: Deploy, Catalog Management
role: Admin, Developer
exl-id: 2d12e36c-d8b7-4253-91d8-28b50477ccd9
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-56842: Uitgestelde proxy&#39;s en proxyfabrieken ontbreken na uitvoering `setup:di:compile`

De ACSD-56842-patch verhelpt het probleem waarbij de uitgestelde proxy&#39;s en proxyfabrieken ontbreken nadat ze zijn uitgevoerd `setup:di:compile`. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 is geïnstalleerd. De patch-id is ACSD-56842. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De uitgestelde proxy&#39;s en proxyfabrieken ontbreken na het uitvoeren `setup:di:compile`.

<u>Stappen om te reproduceren</u>:

1. Een aangepaste module maken met de naam *Magento_CustomModule*.
1. In de *[!UICONTROL etc]* van de module, creeer een `di.xml` met deze inhoud:

   ```xml
    <?xml version="1.0"?>
     <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
        <type name="Magento\Catalog\Model\ProductLink\CollectionProvider">
           <arguments>
              <argument name="providers" xsi:type="array">
                 <item name="crosssell" xsi:type="object">
                      Magento\Catalog\Model\ProductLink\CollectionProvider\Crosssell\Proxy
                 </item>
                   <item name="upsell" xsi:type="object">Magento\Catalog\Model\ProductLink\CollectionProvider\Upsell\Proxy</item>
                     <item name="related" xsi:type="object">Magento\Catalog\Model\ProductLink\CollectionProvider\Related\Proxy</item>
              </argument>
           </arguments>
         </type>
            <type name="Magento\Catalog\Model\Product">
               <arguments>
                  <argument name="catalogProductStatus" xsi:type="object">
                   Magento\Catalog\Model\Product\Attribute\Source\Status\Proxy
                  </argument>
                   <argument name="productLink" xsi:type="object">
                     Magento\Catalog\Model\Product\Link\Proxy
                   </argument>
               </arguments>
             </type>
     </config>
   ```

1. Stel de [!UICONTROL Production] modus: `bin/magento deploy:mode:set production`.
1. Verwijder de gegenereerde map uit de hoofdmap van de magento.
1. De opdracht uitvoeren `bin/magento setup:di:compile`.
1. Controleer de gegenereerde map.

<u>Verwachte resultaten</u>:

* Proxybestanden worden gemaakt na compilatie.
* Fabrieksbestanden worden gemaakt na compilatie.

<u>Werkelijke resultaten</u>:

In de gegenereerde map wordt het proxybestand gegenereerd voor proxyargumenten die zonder regeleinde worden gegeven, en niet voor de argumenten die met een regeleinde worden gegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
