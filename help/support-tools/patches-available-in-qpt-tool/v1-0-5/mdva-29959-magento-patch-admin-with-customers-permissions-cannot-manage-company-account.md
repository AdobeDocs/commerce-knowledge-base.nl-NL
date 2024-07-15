---
title: 'MDVA-29959 patch: admin with "Customers" permissions cannot manage company account'
description: MDVA-29959 flard beschikbaar in het [Hulpmiddel van de Patronen van de Kwaliteit (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) hulpmiddelversie 1.0.5 verhelpt de kwestie waar een beperkte admin gebruiker met alle toestemmingen voor "Klant"ACL geen bedrijven kan beheren (voeg of schrap een bedrijf toe). De kwestie is in B2B voor Adobe Commerce 2.3.4 opgelost.
exl-id: ee246380-d37e-4c24-8435-97ae80088227
feature: Admin Workspace, B2B, Companies, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# MDVA-29959 patch: admin with &quot;Customers&quot; permissions cannot manage company account

MDVA-29959 flard beschikbaar in het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) hulpmiddelversie 1.0.5 bevestigt de kwestie waar een beperkte admin gebruiker met alle toestemmingen voor &quot;Klant&quot;ACL geen bedrijven kan beheren (voeg of schrap een bedrijf toe). De kwestie is in B2B voor Adobe Commerce 2.3.4 opgelost.

## Betrokken producten en versies

B2B voor Adobe Commerce op cloudinfrastructuur 2.3.0-2.3.3-p1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruiker met alle machtigingen voor ACL van &quot;Klant&quot; kan geen bedrijven beheren (voeg een bedrijf toe of verwijder het bedrijf).

<u> Stappen om te reproduceren </u>

1. In Commerce Admin, creeer een nieuwe admin rol en wijs een gebruiker aan die rol toe.
1. Alleen &quot;Klant&quot;-bronnen toewijzen aan de rol.
1. Meld u aan als een gebruiker met deze rol.
1. Probeer een bedrijfsaccount te verwijderen.

<u> Verwacht resultaat:</u>

Het bedrijfsaccount is verwijderd.

<u> Ware resultaat:</u>

U kunt het bedrijfsaccount niet verwijderen. U krijgt *Sorry, hebt u toestemmingen nodig om deze inhoud te bekijken.* foutbericht.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
