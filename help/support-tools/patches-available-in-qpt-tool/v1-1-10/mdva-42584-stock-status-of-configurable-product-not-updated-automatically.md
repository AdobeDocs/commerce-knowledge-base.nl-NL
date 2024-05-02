---
title: "MDVA-42584: voorraadstatus van configureerbaar product niet automatisch bijgewerkt"
description: De MDVA-42584-patch lost het probleem op waarbij de voorraadstatus van het configureerbare product niet automatisch wordt bijgewerkt wanneer het eenvoudige product wordt bijgewerkt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 is geïnstalleerd. De patch-id is MDVA-42584. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: bf2697a2-8d15-408b-8d59-7b4173537e60
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-42584: voorraadstatus van configureerbaar product niet automatisch bijgewerkt

De MDVA-42584-patch lost het probleem op waarbij de voorraadstatus van het configureerbare product niet automatisch wordt bijgewerkt wanneer het eenvoudige product wordt bijgewerkt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 is geïnstalleerd. De patch-id is MDVA-42584. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De voorraadstatus van het configureerbare product in de achtergrond wordt niet automatisch bijgewerkt wanneer zijn eenvoudig product wordt geplaatst aan **In voorraad** via API of import.

<u>Vereisten</u>:

MSI geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Een configureerbaar product maken, **InvCheck001**, met twee opties: **InvCheck001-M** en **InvCheck001-L**.
1. Zowel de eenvoudige producten moeten Hoeveelheid hebben en zij moeten zijn **In voorraad** zodat het configureerbare product ook **In voorraad** op de achtergrond.
1. Nu kunt u zowel eenvoudige producten bijwerken als Hoeveelheid instellen op **0** en de status van de voorraad **Uit voorraad**.
1. Vernieuw het configureerbare product en verifieer de voorraadstatus wordt bijgewerkt aan **Uit voorraad**.
1. Gebruik het volgende API-eindpunt en stel het eenvoudige product in **InvCheck001-M** tot **In voorraad** met Aantal > 0.

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. Ga naar de back-end en controleer de hoeveelheid en voorraadstatus van het eenvoudige product **InvCheck001-M**. Het is bijgewerkt naar **In voorraad**.
1. Vernieuw het configureerbare product en controleer de voorraadstatus.

<u>Verwachte resultaten</u>:

De voorraadstatus van het configureerbare product **InvCheck001** op de achtergrond wordt automatisch bijgewerkt naar **In voorraad**.

<u>Werkelijke resultaten</u>:

De voorraadstatus van het configureerbare product is nog **Uit voorraad**.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
