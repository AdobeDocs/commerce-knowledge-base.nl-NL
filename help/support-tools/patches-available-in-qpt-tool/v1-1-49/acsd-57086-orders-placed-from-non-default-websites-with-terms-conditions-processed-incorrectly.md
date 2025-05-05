---
title: 'ACSD-57086: bestellingen van niet-standaard websites waarvoor de voorwaarden zijn ingeschakeld, worden onjuist verwerkt'
description: Pas de ACSD-57086-patch toe om het Adobe Commerce-probleem op te lossen waarbij bestellingen die van niet-standaard websites met ingeschakelde voorwaarden zijn geplaatst, niet correct worden verwerkt.
feature: Orders
role: Admin, Developer
exl-id: 400e3673-9c61-4acd-8e37-e9a2e0bf9379
source-git-commit: e61dd2874a2b6cb4c49aa6916c6273a2cb9f9e60
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# ACSD-57086: bestellingen van niet-standaard websites waarvoor de voorwaarden zijn ingeschakeld, worden onjuist verwerkt

De ACSD-57086-patch verhelpt het probleem dat bestellingen die van niet-standaard websites met ingeschakelde voorwaarden zijn geplaatst, niet correct worden verwerkt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 wordt geïnstalleerd. De patch-id is ACSD-57086. Dit probleem is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Tijdens het gebruik van een multi-store opstelling met verwerking AsyncOrder, worden de orden die op om het even welke websites/opslag buiten de belangrijkste website worden geplaatst verworpen wegens kwesties met werkingsgebied behandeling in de rij consumentencode.

<u> Stappen om </u> te reproduceren:

1. Installeer [!DNL RabbitMQ] en voer `bin/magento setup:upgrade` uit om de wachtrijen voor [!DNL RabbitMQ] te maken.
1. AsyncOrder-verwerking configureren met:

   ```bash
   bin/magento setup:config:set --checkout-async 1
   ```

1. Maak een secundaire website, een winkel en een winkelweergave.
1. Maak een product dat door beide websites wordt gedeeld.
1. Voorwaarden en bepalingen inschakelen:
   1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** .
   1. Plaats *[!UICONTROL Enable Terms And Conditions]* aan *ja*.
1. Configureer de voorwaarden voor beide websites:
   1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Terms And Conditions]** > **[!UICONTROL Add New Condition]** .
   1. Gebruik de volgende instellingen:
      * *[!UICONTROL Condition Name]*: *Om het even welk*
      * *[!UICONTROL Status]*: *[!UICONTROL Enabled]*
      * *[!UICONTROL Applied]*: *[!UICONTROL Manually]*
      * *[!UICONTROL Store View]*: *[!UICONTROL Default Store View]*
   1. Maak een andere voorwaarde voor de tweede website-/winkelweergave.
1. Wijzig de standaardwebsite door naar **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** te gaan. Klik op de tweede website, controleer *[!UICONTROL Set as Default]* en sla deze op.
1. De cache wissen met:

   ```bash
   bin/magento cache:clear
   ```

1. Ga naar de Storefront en voeg een product aan de kar toe. Ga door met het afrekenen en plaats een bestelling (u ziet een selectievakje in de stap Betalingsmethode om de voorwaarden en bepalingen te accepteren).
1. Ga terug naar Admin nadat u de bestelling hebt geplaatst en verander de standaardwebsite weer naar de oorspronkelijke hoofdwebsite en sla deze op.
1. Cache wissen:

   ```bash
   bin/magento cache:clear
   ```

1. Voer het volgende bevel in werking om de rijconsument te beginnen:

   ```bash
   bin/magento queue:cons:start placeOrderProcessor
   ```

<u> Verwachte resultaten </u>:

De bestelling is voldaan en wordt niet automatisch afgewezen.

<u> Ware resultaten </u>:

De status van de orde wordt *verworpen* met de volgende commentaar:

*de orde werd niet geplaatst. Ga eerst akkoord met de voorwaarden en probeer vervolgens uw bestelling opnieuw te plaatsen.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
