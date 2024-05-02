---
title: 'ACSD-50234: Onjuiste naam van klant in bevestigingsbericht voor bestellingen die zijn geplaatst met [!DNL PayPal]'
description: Pas de ACSD-50234-patch toe om het Adobe Commerce-probleem op te lossen waarbij de naam van de klant onjuist wordt weergegeven in het bevestigingsbericht voor bestellingen die zijn geplaatst met [!DNL PayPal].
exl-id: b2e9c25a-5dd5-4b37-81e3-ca960078da77
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50234: Onjuiste naam van klant in bevestigingsbericht voor bestellingen die zijn geplaatst met [!DNL PayPal]

De ACSD-50234-patch verhelpt het probleem waarbij de naam van de klant onjuist wordt weergegeven in het bevestigingsbericht voor bestellingen die zijn geplaatst met [!DNL PayPal]. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 is geïnstalleerd. De patch-id is ACSD-50234. De kwestie is opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.4-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bevestigingse-mail voor orders die zijn geplaatst met [!DNL PayPal] geeft de verkeerde naam van de klant weer.

<u>Stappen om te reproduceren</u>

1. Inschakelen **[!UICONTROL PayPal Express Checkout]**.
1. Navigeer als gast naar de voorzijde.
1. Voeg producten toe aan de kar.
1. Afhandeling met **[!UICONTROL PayPal Express Checkout]** als betalingsmethode.
1. Controleer het bevestigingsbericht voor bestelling.

<u>Verwachte resultaten</u>

Het bevestigingsbericht voor de bestelling, het e-mailbericht voor de factuur en alle e-mails over de verzending worden naar de naam van de klant verzonden.

<u>Werkelijke resultaten</u>

Het bevestigingsbericht voor de bestelling, het e-mailbericht voor de factuur en alle e-mails over de verzending worden verzonden naar *Gast*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
