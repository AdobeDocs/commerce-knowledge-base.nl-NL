---
title: 'MDVA-40601: Kan geen gegevens ophalen over categorie gewijzigd via geplande update via GraphQL'
description: De MDVA-40601 Adobe Commerce-kwaliteitspatch verhelpt het probleem dat gebruikers een fout krijgen wanneer ze informatie over een categorie wijzigen via een geplande update via GraphQL. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.3 is geïnstalleerd. De patch-id is MDVA-40601. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: b1ea93e7-8d4a-4bdd-8267-cc60de25bd39
feature: Categories, GraphQL
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-40601: Kan geen gegevens ophalen over categorie gewijzigd via geplande update via GraphQL

De MDVA-40601 Adobe Commerce-kwaliteitspatch verhelpt het probleem dat gebruikers een fout krijgen wanneer ze informatie over een categorie wijzigen via een geplande update via GraphQL. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.3 geïnstalleerd is. De patch-id is MDVA-40601. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.3 en 2.4.2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.1 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers krijgen een fout wanneer ze proberen informatie op te halen over een categorie die is gewijzigd door een geplande update via GraphQL.

<u> Stappen om </u> te reproduceren:

1. Stel een categoriestructuur in met een subcategorie zoals hieronder beschreven:

   <pre>
   <code class="language-graphql">
   - Root
    - Some category
         - Some child category

   </code>
   </pre>

1. GraphQL-query uitvoeren met ID 49 &quot;Some Categorie&quot;.

   <pre>
    <code class="language-graphql">
    query &lbrace;
     category(id: 49) &lbrace;
      name
      children &lbrace;
        name
       &rbrace;
     &rbrace;
   &rbrace;
   </code>
   </pre>

   Resultaat

   <pre>
    <code class="language-graphql">
    &lbrace;
      "data": &lbrace;
        "category": &lbrace;
          "name": "Some category",
          "children": &lbrack;
            &lbrace;
              "name": "Some child category"
            &rbrace;
          &rbrack;
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>

1. Maak een update voor &#39;Een rubriek&#39; met een andere rubrieknaam.
1. Wacht tot de planningupdate is geactiveerd.
1. Voer dezelfde query uit als hierboven is opgegeven.

<u> Verwachte resultaten </u>:

Je ontvangt hetzelfde resultaat, maar dan met de bijgewerkte categorienaam.

<u> Ware resultaten </u>:

De volgende fout treedt op:

<pre>
<code class="language-graphql">
&lbrace;
  "errors": &lbrack;
    &lbrace;
      "debugMessage": "uasort() expects parameter 1 to be array, string given",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 2,
          "column": 3
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "category"
      &rbrack;
    &rbrace;
  &rbrack;,
  "data": &lbrace;
    "category": null
  &rbrace;
&rbrace;
</code>
</pre>

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

&#x200B;* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
&#x200B;* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over kwaliteitspatches voor Adobe Commerce:

&#x200B;* [ vrijgegeven Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitsflarden ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) zelf-te dienen.
&#x200B;* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
