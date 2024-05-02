---
title: "ACSD-48204: Catalogusprijsregel gemaakt op basis van *Yes/No*-kenmerk houdt geen rekening met geselecteerd bereik"
description: Pas de ACSD-48204-patch toe om het Adobe Commerce-probleem op te lossen waarbij de regel voor catalogusprijzen die is gemaakt op basis van het kenmerk *Yes/No*, geen rekening houdt met het geselecteerde bereik.
exl-id: 9b0b4d62-c4c5-40d7-a279-52f59ee7ac42
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-48204: Catalogusprijsregel gemaakt op basis van *Ja/Nee* kenmerk houdt geen rekening met geselecteerd bereik

De ACSD-48204-patch verhelpt het probleem waarbij de prijsregel voor catalogi die is gemaakt op basis van *Ja/Nee* kenmerk houdt geen rekening met het geselecteerde bereik. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 is geïnstalleerd. De patch-id is ACSD-48204. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De regel voor catalogusprijzen is gemaakt op basis van *Ja/Nee* kenmerk houdt geen rekening met het geselecteerde bereik.

<u>Stappen om te reproduceren</u>:

1. Maak twee websites (standaard en W2).
1. Een productkenmerk maken van *Ja/Nee* type.
   * Set [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Maak een configureerbaar product op basis van een willekeurig kenmerk met twee variaties (V1 en V2).
   * Voeg de *Ja/Nee* attribuut aan de configureerbare reeks van variatiekenmerken
   * Voor een van de variaties (V1) stelt u de waarde in op *[!UICONTROL Yes]* op de niet-standaard website (W2)
1. Een catalogusregel maken:
   * Toegepast op beide websites
   * Voorwaarde: *Ja/Nee* kenmerkwaarde is *[!UICONTROL Yes]*
   * Korting = 50%
1. Open het configureerbare product op de niet-standaard website (W2).
1. Controleer of de 50% korting is toegepast op de V1-variatie.
1. Open de V1-variatie in Adobe Commerce Admin.
   * Naar de standaardwebsite schakelen
   * Geen wijzigingen aanbrengen en het product opslaan
1. Vernieuw de configureerbare pagina van de productwinkel.

<u>Verwachte resultaten</u>:

Bij de variatie V1 wordt de korting van 50% nog steeds toegepast omdat er geen wijzigingen zijn aangebracht.

<u>Werkelijke resultaten</u>:

De korting verdwijnt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
