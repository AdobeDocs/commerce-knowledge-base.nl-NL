---
title: 'MDVA-40311: Fout "Ongeldige beveiliging of formuliersleutel" na aanmelding bij Admin als aangepast beheerpad is geconfigureerd.'
description: '''De MDVA-40311-patch verhelpt het probleem waarbij de Admin-gebruiker een foutbericht krijgt: *Ongeldige beveiliging of formuliersleutel. Vernieuw pagina* na aanmelding bij Admin als het aangepaste beheerpad is geconfigureerd en de geheime sleutel is ingeschakeld. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 is geïnstalleerd. De patch-id is MDVA-40311. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4. "'
exl-id: d4562f09-0aed-438e-8c2e-90557aa2f146
feature: Admin Workspace, Compliance, Security
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-40311: Fout &quot;Ongeldige beveiliging of formuliersleutel&quot; na aanmelding bij Admin als aangepast beheerpad is geconfigureerd

Het flard MDVA-40311 lost de kwestie op waar de gebruiker Admin een foutenmelding krijgt: *Ongeldige veiligheid of vormsleutel. Vernieuw de pagina* na aanmelding in Admin als het aangepaste beheerpad is geconfigureerd en de geheime sleutel is ingeschakeld. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 geïnstalleerd is. De patch-id is MDVA-40311. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker Admin krijgt een foutenmelding: *Ongeldige veiligheid of vormsleutel. Vernieuw de pagina* na aanmelding in Admin als het aangepaste beheerpad is geconfigureerd en de geheime sleutel is ingeschakeld.

<u> Stappen om </u> te reproduceren:

* Meld u met een geldige gebruikersnaam en wachtwoord aan als Admin-gebruiker.

<u> Verwachte resultaten </u>:

Gebruiker kan zich aanmelden zonder foutbericht.

<u> Ware resultaten </u>:

*Ongeldige veiligheid of vormsleutel. Vernieuw de pagina* foutmelding.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in onze ontwikkelaarsdocumentatie.
