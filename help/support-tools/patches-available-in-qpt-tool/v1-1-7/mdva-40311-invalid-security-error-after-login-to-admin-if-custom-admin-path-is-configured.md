---
title: 'MDVA-40311: Fout "Ongeldige beveiliging of formuliersleutel" na aanmelding bij Admin als aangepast beheerpad is geconfigureerd.'
description: '''De MDVA-40311-patch verhelpt het probleem waarbij de Admin-gebruiker een foutbericht krijgt: *Ongeldige beveiliging of formuliersleutel. Vernieuw pagina* na aanmelding bij Admin als het aangepaste beheerpad is geconfigureerd en de geheime sleutel is ingeschakeld. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 is geïnstalleerd. De patch-id is MDVA-40311. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4. "'
exl-id: d4562f09-0aed-438e-8c2e-90557aa2f146
feature: Admin Workspace, Compliance, Security
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-40311: Fout &quot;Ongeldige beveiliging of formuliersleutel&quot; na aanmelding bij Admin als aangepast beheerpad is geconfigureerd

De MDVA-40311-patch verhelpt het probleem waarbij de Admin-gebruiker een foutbericht krijgt: *Ongeldige beveiliging of formuliersleutel. Vernieuw de pagina*, na aanmelding bij de beheerder als het aangepaste beheerpad is geconfigureerd en de geheime sleutel is ingeschakeld. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 is geïnstalleerd. De patch-id is MDVA-40311. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruiker krijgt een foutbericht: *Ongeldige beveiliging of formuliersleutel. Vernieuw de pagina*, na aanmelding bij de beheerder als het aangepaste beheerpad is geconfigureerd en de geheime sleutel is ingeschakeld.

<u>Stappen om te reproduceren</u>:

* Meld u met een geldige gebruikersnaam en wachtwoord aan als Admin-gebruiker.

<u>Verwachte resultaten</u>:

Gebruiker kan zich aanmelden zonder foutbericht.

<u>Werkelijke resultaten</u>:

*Ongeldige beveiliging of formuliersleutel. Vernieuw de pagina* foutbericht wordt weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
