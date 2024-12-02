---
title: 'ACSD-51907: gebruikers met beperkte beheerdersrechten kunnen geen creditnota voor offline restitutie maken'
description: Pas de ACSD-51907-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de gebruiker met beperkte beheerdersrechten geen creditmemo met een offlinerestitutie kan maken.
exl-id: 564e8524-f2dc-453c-be78-a920fbd47d71
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-51907: gebruikers met beperkte beheerdersrechten kunnen geen creditnota voor offline restitutie maken

De ACSD-51907-patch verhelpt het prestatieprobleem waarbij een gebruiker met beperkte beheerdersrechten geen creditmemo met een offline restitutie kan maken. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.33 is geïnstalleerd. De patch-id is ACSD-51907. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Beperkte gebruikers van beheerders kunnen geen creditnota met een off-line terugbetaling tot stand brengen.

<u> Stappen om </u> te reproduceren:

1. Creeer a **klant** op de standaardwebsite.
1. Creeer **nieuwe website** met verwante *opslag* en *opslagmening*.
1. Standaardwebsite instellen op nieuwe website, caches wissen.
1. De klantenconfiguratie van de verandering: **Admin** > **Opslag** > **Configuratie** > **Klanten** > **de Configuratie van de Klant** > **de Rekeningen van de Klant van het Aandeel = Globale**.
1. Creeer een nieuwe admin gebruikersrol met het rolwerkingsgebied dat aan nieuwe gecreeerde website *wordt geplaatst (toegang tot verkoopgegevens slechts)* in **Admin** > **Systeem** > **Toestemmingen**.
1. Maak een nieuw beheerdersaccount met deze rol.
1. Nieuwe bestelling maken met de online betalingsmethode *(bijvoorbeeld Auth.net of PayPal)* .
1. Meld u aan als gebruiker met beperkte beheerdersrechten.
1. Ga naar **Verkoop** > **Orden** > dan **de pagina van de ordemening**.
1. Maak een factuur.
1. Navigeer naar het tabblad Facturen.
1. Klik op **Factuur**.
1. Klik op **[!UICONTROL Credit Memo]** .
1. Controleer **[!UICONTROL Refund to Store Credit]** checkbox, plaats het tekstgebied dichtbij het aan de *1* waarde.
1. Klik op de knop **[!UICONTROL Refund Offline]** .

<u> Verwachte resultaten </u>:

Het creditmemo wordt gecreeerd, en *$1* wordt teruggegeven aan het opslagkrediet.

<u> Ware resultaten </u>:

Het foutenbericht, *Meer toestemmingen zijn nodig om dit punt* te bekijken wordt getoond.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
