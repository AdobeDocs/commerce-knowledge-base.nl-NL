---
title: 'ACSD-58008: Het uitgeven van de einddatum als *empty* veroorzaakt de programmaupdate om te verdwijnen'
description: Pas de ACSD-58008-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij het bewerken van de einddatum als *empty* ertoe leidt dat de update van het schema verdwijnt.
feature: Staging, Page Content
role: Admin, Developer
source-git-commit: 174ed3b35edeb26b09b04bc7d88111a5719e08f8
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-58008: De einddatum bewerken als *leeg* zorgt ervoor dat de planningupdate verdwijnt

De ACSD-58008-patch verhelpt het probleem waarbij de einddatum als *leeg* zorgt ervoor dat de update van het schema verdwijnt. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 is geïnstalleerd. De patch-id is ACSD-58008. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De einddatum bewerken als *leeg* zorgt ervoor dat de planningupdate verdwijnt

<u>Stappen om te reproduceren</u>:

1. Aanmelden als [!UICONTROL Admin].
1. Ga naar **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** en maakt u een pagina.
1. Selecteer de gemaakte pagina en klik op **[!UICONTROL Schedule New Update]**. *(Navigeer naar de rechterbovenhoek van de pagina)*.
1. Maak vier updates. *(Bijvoorbeeld als een verhoging van* 2 *minuten)*.
1. Werk de *update 2* en wijzig de tijd in een tijd die voor de laatste ligt *update 4*.
1. Sla de aangebrachte updates op.

<u>Verwachte resultaten</u>:

In de planningsupdate worden de *update 3*.

<u>Werkelijke resultaten</u>:

In de update voor schema wordt het dialoogvenster *update 3*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.