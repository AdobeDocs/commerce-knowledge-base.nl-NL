---
title: 'ACSD-52929: Overbodig verzoek om standaardbronitems opnieuw te indexeren'
description: Pas de markering ACSD-52929 toe om het Adobe Commerce-probleem op te lossen waarbij er een overtollig verzoek is om de standaardbronitems opnieuw te indexeren wanneer de inventarisindexator in de asynchrone modus is geconfigureerd.
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 978fe0d0-3917-4ba2-94bb-01c607a825cc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-52929: Overbodig verzoek om standaardbronitems opnieuw te indexeren

De markering ACSD-52929 lost het probleem op waar er een overtolligheid van verzoeken om standaardbronpunten opnieuw te indexeren is wanneer de inventarisindexator op async wijze wordt gevormd. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.38 is geïnstalleerd. De patch-id is ACSD-52929. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er is een overtolligheid van verzoeken om standaardbronpunten opnieuw te indexeren wanneer de inventarisindexeerder op asynchrone wijze wordt gevormd.

<u>Stappen om te reproduceren</u>:

1. Configureren [!DNL RabbitMQ].
1. Schakel asynchrone herindexstrategie in door naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** en instellen **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**.
1. Een aangepaste inventarisbron maken.
1. Aanmelden bij [!DNL RabbitMQ] dashboard en ga naar het tabblad Wachtrijen.
1. Controleren `inventory.indexer.sourceItem` rij en zorg ervoor het nul berichten heeft.
1. Een eenvoudig product openen vanaf de achtergrond en toevoegen *[!UICONTROL stock only]* naar de aangepaste bron en sla het product op.
1. Laad de `inventory.indexer.sourceItem` wachtrij in de [!DNL RabbitMQ] het dashboard en controleert dan de berichten.

<u>Verwachte resultaten</u>:

Er is slechts één bericht in de wachtrij voor de aangepaste bron.

<u>Werkelijke resultaten</u>:

Twee berichten worden getoond in de rij: voor de standaardbron en andere voor de douanebron.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
