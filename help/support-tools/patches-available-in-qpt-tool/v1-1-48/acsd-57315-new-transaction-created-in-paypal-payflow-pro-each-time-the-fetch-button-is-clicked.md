---
title: 'ACSD-57315: Nieuwe transactie wordt gemaakt in [!DNL PayPal Payflow Pro] telkens wanneer op de knop Ophalen wordt geklikt.'
description: Pas de ACSD-57315-patch toe om het Adobe Commerce-probleem op te lossen waarin een nieuwe transactie wordt gemaakt [!DNL PayPal Payflow Pro] telkens als de vangknop op het scherm van de meningstransactie in wordt geklikt [!UICONTROL Admin].
feature: Payments
role: Admin, Developer
source-git-commit: b7f85e4fdb7ef4a6328a1a411dac765dd8da083e
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57315: Nieuwe transactie wordt gemaakt in [!DNL PayPal Payflow Pro] elke keer dat op de knop Ophalen wordt geklikt

De ACSD-57315-patch verhelpt het probleem waarbij een nieuwe transactie wordt gemaakt in [!DNL PayPal Payflow Pro] telkens als de vangknop op het scherm van de meningstransactie in wordt geklikt [!UICONTROL Admin]. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.48 is geïnstalleerd. De patch-id is ACSD-57315. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er wordt een nieuwe transactie gemaakt in [!DNL PayPal Payflow Pro] telkens als de vangknop op het scherm van de meningstransactie in wordt geklikt [!UICONTROL Admin].

<u>Stappen om te reproduceren</u>:

1. Configureren [!DNL PayPal Payflow Pro].
1. De transactiemethode instellen op *[!UICONTROL Sale]*.
1. Een order plaatsen met *Creditcard*.
1. De transactie openen vanuit [!UICONTROL Admin].
1. Klik op de knop **[!UICONTROL Fetch]** knop.
1. Controleren [!DNL PayPal] rekening voor transacties die verband houden met de geplaatste order.

<u>Verwachte resultaten</u>:

Er wordt geen nieuwe betalingstransactie gemaakt.

<u>Werkelijke resultaten</u>:

Er wordt een nieuwe betalingstransactie gemaakt voor een bestelling die al is betaald.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
