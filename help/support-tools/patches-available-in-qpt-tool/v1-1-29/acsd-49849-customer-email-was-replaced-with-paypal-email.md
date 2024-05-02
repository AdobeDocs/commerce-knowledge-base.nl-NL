---
title: 'ACSD-49849: e-mail van de klant is vervangen door PayPal-e-mail'
description: Pas de ACSD-49849-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de e-mail van de klant is vervangen door PayPal-e-mail bij het plaatsen van een bestelling met PayPal Express via GraphQL.
exl-id: 826ea90a-ac10-43e8-aa88-bd69b152ded8
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-49849: e-mail van de klant wordt vervangen door [!DNL PayPal] email

De ACSD-49849-patch verhelpt het probleem waarbij de e-mail van een klant wordt vervangen door een [!DNL PayPal's] e-mail wanneer u een bestelling plaatst met [!DNL PayPal Express] via GraphQL. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 is geïnstalleerd. De patch-id is ACSD-49849. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een e-mailadres van een klant wordt vervangen door een [!DNL PayPal's] e-mail wanneer u een bestelling plaatst met [!DNL PayPal Express] via GraphQL.

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. Inschakelen en configureren [!DNL PayPal Express] en instellen **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**.
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** en maak een eenvoudig product.
1. Voltooi het uitchecken door de gast met GraphQL. Raadpleeg voor meer informatie de [GraphQL-zelfstudie over uitchecken](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) in Adobe Commerce Developer Documentation.
1. Gebruiken [!DNL PayPal Express] als betalingsmethode.
1. Noteer het e-mailbericht dat u hebt gebruikt in de stap waar u het bestand hebt opgeslagen [e-mail instellen voor winkelwagentje](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) in Adobe Commerce Developer Documentation.
1. Nadat de bestelling is geplaatst, gaat u naar Adobe Commerce Admin en controleert u het e-mailbericht in de gemaakte bestelling.

<u>Verwachte resultaten</u>:

Het e-mailadres is hetzelfde als dat is ingesteld tijdens het uitchecken.

<u>Werkelijke resultaten</u>:

De e-mailset die tijdens het uitchecken is ingesteld, wordt overschreven door de e-mailset in het dialoogvenster [!DNL PayPal] account.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
