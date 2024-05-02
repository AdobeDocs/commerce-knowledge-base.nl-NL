---
title: 'ACSD-46869: configureerbare producten die niet worden bijgewerkt met REST API bij kassa'
description: De ACSD-46869-patch verhelpt het probleem waarbij de configureerbare producten niet worden bijgewerkt met behulp van REST API bij het uitchecken. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 is geïnstalleerd. De patch-id is ACSD-46869. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: d1bac489-f0f3-4b50-bc48-86c844230da7
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-46869: configureerbare producten die niet worden bijgewerkt met REST API bij het uitchecken

De ACSD-46869-patch verhelpt het probleem waarbij configureerbare producten niet worden bijgewerkt met behulp van REST API bij het uitchecken. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 is geïnstalleerd. De patch-id is ACSD-46869. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL QPT] landingspagina](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Configureerbare producten worden niet bijgewerkt met REST API tijdens het uitchecken.

<u>Stappen om te reproduceren</u>:

1. Maak een configureerbaar product met kleur- en formaatkenmerken.
1. Selecteren **[!UICONTROL Options]** en voeg het product toe aan de kar.
1. Ga naar **[!UICONTROL Checkout]** Werk de grootte meerdere keren bij, behalve voor hoeveelheid, en controleer de aanvraag en het antwoord.
1. U krijgt de volgende reactie wanneer u de grootte bijwerkt.

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>Verwachte resultaten</u>:

De waarde wordt bijgewerkt op basis van de wijzigingen.

<u>Werkelijke resultaten</u>:

`option_value` wordt niet bijgewerkt, dus wanneer de volgorde wordt geplaatst, heeft deze de waarde voor de oude grootte.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tools] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding voor het gereedschap Kwaliteitspatches.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in [!DNL QPT], zie [Patches beschikbaar in [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de handleiding voor het gereedschap Kwaliteitspatches.
