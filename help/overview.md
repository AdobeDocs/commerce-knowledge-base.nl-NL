---
title: Adobe Commerce Support Knowledge Base
description: Alles wat u moet weten om problemen op te lossen en uw Commerce-winkel te onderhouden.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 607b835da518536196654734f62d78d095099476
workflow-type: tm+mt
source-wordcount: '1615'
ht-degree: 0%

---

# Adobe Commerce Support Knowledge Base

>[!NOTE]
>
>De Adobe Commerce Support Knowledge Base Guide zal binnenkort worden geherstructureerd, waarbij de inhoud wordt verplaatst naar andere locaties in Adobe Experience League. Ondertussen zullen we de inhoud in deze handleiding blijven onderhouden en bijwerken.

![ homepage van de Kennisbank ](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

De informatie in deze Kennisbank wordt ontworpen als aanvulling op [ de Documentatie van de Ontwikkelaar van Adobe Commerce ](https://developer.adobe.com/commerce/docs), en [ Handleiding van de Merchant van Adobe Commerce ](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html), en andere publicaties van Adobe Commerce. Het behandelt het oplossen van problemen en beste praktijken, gastheeraankondigingen, antwoorden FAQs, en benadrukt specifieke scenario&#39;s die (om het even welke reden) niet vermeld in de officiële documentatie zijn.

## Wat staat er in deze Knowledge Base?

| CATEGORIE | BESCHRIJVING |
| --- | --- |
| [ Hulpmiddelen van de Steun ](/help/support-tools/overview.md) | Verbeter uw e-commercewinkelervaring met de verschillende ondersteuningsinstrumenten die Adobe Commerce biedt. Wij bieden gepersonaliseerde beste praktijken, diagnose en controlehulpmiddelen, en de meest relevante informatie over uw plaats. |
| [ Mededelingen ](/help/announcements/overview.md) | Ontvang belangrijke updates van de Adobe Commerce-teams. |
| [ het Oplossen van problemen ](/help/troubleshooting/overview.md) | Haal oplossingen en patches voor zelfbediening van het Adobe Commerce Support-team. |
| [ Gids van de Gebruiker van het Centrum van de Hulp ](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | Leer hoe u uw ondersteuningstickets beheert, gedeelde toegang verleent en de Knowledge Base op effectieve wijze doorbladert. |
| [ hoe te ](/help/how-to/overview.md) | Kies voor duidelijke stapsgewijze instructies van het Adobe Commerce Support-team. |
| [ Veelgestelde vragen ](/help/faq/overview.md) | Veelgestelde vragen over het beleid, de strategieën en de specifieke eigenschappen van Adobe Commerce zijn te vinden. |

## Nieuwe functies

<table style="width:100%">
  <tr>
    <th style="width:70%">Beschrijving</th>
    <th style="width:15%">Type</th>
    <th style="width:15%">Datum</th>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25075"> het Scannen van het Hulpmiddel van het Scannen van de Veiligheid keert "kan niet bepalen als uw server 2FA"gebruikt:</a> om de fout op te lossen, controleer of de <code>Magento_TwoFactorAuth</code> module is onbruikbaar gemaakt. Als u de controle wilt doorstaan, moet deze over het algemeen zijn ingeschakeld.
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60632-address-saved-on-every-order-attempt"> ACSD-60632: Adres dat met elke ordepoging wordt bewaard:</a> het ACSD-60632 flard lost de kwestie op waar een nieuw adres met elke poging van de orderplaatsing wordt bewaard, ongeacht of de orde met succes wordt gecreeerd of niet. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.51 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60326-graphql-query-error-customer-return-status"> ACSD-60326: De vraag van GraphQL op klant geeft status terug geeft een fout:</a> Het ACSD-60326 flard moeilijke situatie waar een fout in de vraag van GraphQL voor klant terugkeert status voorkomt. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.51 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59925-sorting-items-in-media-gallery"> ACSD-59925: Het sorteren van punten in de Galerij van Media door positie in GraphQL:</a> ACSD-59925 flardmoeilijke situatie waar de punten in de Galerij van Media niet door positie worden gesorteerd, leidend tot een onjuiste vertoningsorde. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.52 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-61322-products-not-assigned-to-shared-catalogue"> ACSD-61322: De producten niet die aan Gedeelde Catalogus worden toegewezen zijn inbegrepen in de Sitemap van XML:</a> het markering ACSD-61322 moeilijke situatie waar de producten/de categorieën niet die aan de Gedeelde Catalogus voor de Standaard (Algemene) groep worden toegewezen nog inbegrepen in de Sitemap van XML zijn. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.52 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60590-optimized-bestseller-report-generation"> ACSD-60590: Het verbeteren van prestaties van Bestsellers Geaggregeerde Dagelijkse de generatie van het Rapport:</a> het flard ACSD-60590 moeilijke situatie waar het Bestsellers Geaggregeerde Dagelijkse Rapport een significante hoeveelheid tijd vergt om voor een groot volume van geplaatste orden te produceren. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.52 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59865-cart-price-rule-fix-for-insufficient-quantity-issue"> ACSD-59865: De Regel van de Prijs van de Kar annuleert vorige regels wegens ontoereikende producthoeveelheid:</a> ACSD-59865 flardfixes de kwestie waar de <em> waarde van de Korting van de Korting van de Korreligheid </em> in <em> Vaste waardekorting </em>, <em> Procent van de korting van de productprijs </em>, en <em> krijgt Y </em> Regels voor winkelwagenprijzen annuleert niet langer de handeling van eerdere regels. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.52 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/error-when-filtering-orders-in-admin"> Fout wanneer het filtreren van orden in Admin:</a> Dit artikel verstrekt een flard voor de kwestie van Adobe Commerce waar een fout voorkomt wanneer het proberen om orden in Admin door datum te filtreren, tonend het bericht: <em> schending van de de beperkingsbeperking van de Integriteit: 1052 Kolom "created_at"waar de clausule dubbelzinnig is </em>.
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25030"> Adobe Commerce: De Kwesties van Inline JavaScript op checkout pagina in de beperkte wijze van het Beleid van de Veiligheid van de Inhoud (CSP):</a> Dit artikel verstrekt gedetailleerde verklaringen en oplossingen voor kwesties die met douane JavaScript worden ontmoet die via de Manager van de Markering van Adobe Commerce Admin en van Google in Adobe Commerce 2.4.7 wordt toegevoegd tijdens controle wanneer <strong> CSP beperkte wijze </strong> wordt toegelaten.
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-61195-empty-cart-on-final-graphql-page"> ACSD-61195: Het verzoek van GraphQL van de Kar ontbreekt om punten op definitieve pagina terug te keren:</a> het markering ACSD-61195 bevestigt de kwestie waar geen wortelpunten op de laatste pagina voor het bevel van GraphQL van de kar zijn teruggekeerd. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.51 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-59514-forms-in-admin-with-page-builder-throw-error-in-browser-console"> ACSD-59514: Forms in Admin met de Bouwer van de Pagina werpen fout in browser console:</a> ACSD-59514 herstelt het flard waar de vormen in Admin met de Bouwer van de Pagina de fout <em> Bouwer van de Pagina teruggeven voor 5 seconden zonder loslaat </em> in de browser console na het voorleggen van de vorm, en de veranderingen kunnen niet worden bewaard. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.50 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60538-if-product-is-disabled-attributes-dont-show"> ACSD-60538: De attributen tonen niet correct als het product in <em> Alle Kijken van de Opslag </em> wordt onbruikbaar gemaakt:</a> ACSD-60538 flardmoeilijke situaties de kwestie waar als een product in <em> Alle Kijken van de Opslag </em> wordt onbruikbaar gemaakt en slechts in specifieke gebieden van de opslagmening wordt toegelaten, tonen de productattributen niet correct in de reactie van GraphQL, waardoor het product niet correct wordt weergegeven. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.51 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-58352-return-attribute-labels-for-the-default-store-are-returned-via-graphql-api"> ACSD-58352: De de attributenetiketten van de terugkeer voor de standaardopslag zijn teruggekeerd via GraphQL API:</a> ACSD-58352 flardmoeilijke situatie waar de etiketten van de terugkeerattributen voor de standaardopslag via GraphQL API zijn teruggekeerd wanneer een niet-standaard opslagmening in de verzoekkopbal wordt gespecificeerd. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.50 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-24983"> het <em> drop-down van de Rekeningen van de Schakelaar </em> mist van uw rekening:</a> Dit artikel verstrekt een oplossing aan de kwestie van Adobe Commerce waar <em> de rekeningen van de Schakelaar </em> dropdown van uw rekening mist, en u hebt toegang verloren om kaartjes namens de handelaar voor te leggen.
    </td>
    <td>Nieuw artikel</td>
    <td>17 oktober 2024</td>
  </tr>

<tr>  
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-56979-product-images-removed-after-staging-update-deleted"> ACSD-56979: De beelden van het product die na het opvoeren verwijderde update worden verwijderd:</a> ACSD-56979 herstelt de kwestie waar de productbeelden na het schrappen van een het opvoeren update worden verwijderd. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.49 wordt geïnstalleerd.  
    </td>
    <td>Nieuw artikel</td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-48210-store-view-specific-scope-attribute-overrides-global-values"> ACSD-48210: De de meningsspecifieke werkingsgebiedattributen van de opslag treden globale waarden met voeten:</a> het ACSD-48210 flard lost de kwestie op waar wanneer het bijwerken van het attribuut van het Werkingsgebied van de a <em> Website </em> binnen een specifieke opslagmening de attributenwaarden in het globale werkingsgebied met voeten treedt. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.50 wordt geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-59280-fix-for-reflection-union-type-error"> ACSD-59280: De fout van RefCollectionUnionType::getName () in 2.4.4-pX installaties:</a> het flard ACSD-59280 lost de kwestie op waar de vraag aan ongedefinieerde methode <code>ReflectionUnionType::getName()</code> fout tijdens de installatie van 2.4.4-pX versies voorkomt. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.50 wordt geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-54887-customer-shopping-cart-gets-cleared-after-session-expiry"> ACSD-54887: Het winkelwagentje van de klant wordt ontruimd nadat de klantenzitting is verlopen:</a> ACSD-54887 herstelt de flard waar het het winkelwagentje van de klant wordt ontruimd nadat de klantenzitting met <em> Persistent het Winkelen Kart </em> toegelaten is verlopen. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.50 wordt geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-60303-admin-order-placement-fix"> ACSD-60303: Het probleem van de orderplaatsing van Admin die met toegelaten HTML minificatie wordt opgelost:</a> ACSD-60303 flardmoeilijke situatie waar een orde van Admin niet kan worden geplaatst als de minificatie van de HTML wordt toegelaten. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.50 wordt geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57045-url-rewrites-cause-infinite-page-looping-after-website-root-unchecked-hierarchy"> ACSD-57045: URL herschrijft oorzaak oneindige pagina het van een lus voorzien na <em> Wortel van de Website </em> ongecontroleerd van Hiërarchie:</a> ACSD-57045 flardmoeilijke situatie waar URL opnieuw schrijft oorzaak oneindige pagina het van een lus voorzien nadat <em> Wortel van de Website </em> van Hiërarchie wordt ongecontroleerd. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.49 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/ascd-58446-deleting-a-team-with-child-users-or-teams-via-graphql-gives-an-uninformative-error-message"> ACSD-58446: Het schrappen van een team met kindgebruikers of teams via GraphQL geeft een uninformatieve foutenmelding:</a> ACSD-58446 flardfixes de kwestie van Adobe Commerce waar het schrappen van een team met kindgebruikers of teams via GraphQL een uninformatief foutenmelding inconsequent met UI terugkeert. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.49 wordt geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-58375-wrong-youtube-api-key-configuration-causes-an-error-when-adding-a-youtube-video-at-the-store-view-level"> ACSD-58735: De onjuist gevormde sleutel van YouTube API veroorzaakt fout wanneer het toevoegen van video op het niveau van de opslagmening:</a> ACSD-58735 herstelt de flard waar de verkeerde belangrijkste configuratie van YouTube API een fout veroorzaakt wanneer het toevoegen van een video van YouTube op het niveau van de opslagmening. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.49 wordt geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57086-orders-placed-from-non-default-websites-with-terms-conditions-processed-incorrectly"> ACSD-57086: De orden van niet-gebrek websites met toegelaten voorwaarden worden verkeerd verwerkt:</a> het flard ACSD-57086 bevestigt de kwestie waar de orden die van niet-gebrek websites met toegelaten voorwaarden worden geplaatst niet correct worden verwerkt. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.49 wordt geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58141-phpsessid-regenerates-on-post-requests-for-logged-in-customers-with-l2-redis-cache-enabled"> ACSD-58141: PHPSESSID regenereert op de verzoeken van de POST voor het programma geopende klanten als L2 Redis geheime voorgeheugen wordt toegelaten:</a> ACSD-58141 flardmoeilijke situatie waar PHPSESSID op de verzoeken van de POST voor een het programma geopende klant regenereert als L2 Redis geheime voorgeheugen wordt toegelaten, en de klant wordt bijgewerkt van Admin. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.50 wordt geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58790-fixes-pinch-to-zoom-functionality-on-the-product-detail-page-images-in-mobile-view-on-chrome"> ACSD-58790: lost knijpfunctionaliteit aan gezoem op de beelden van de productdetailpagina in mobiele mening op Chrome op:</a> het markering ACSD-58790 verhelpt de kwestie van Adobe Commerce waar het beeld in mobiele mening op Chrome niet op het beeld zoals verwacht inzoomde. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.50 wordt geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58442-fixes-issue-devices-768px-mobile-view-instead-desktop"> ACSD-58442: Verhelpt de kwestie waar de apparaten met 768px breedte die als mobiel worden behandeld, menu en kopbal veroorzaken om in mobiele mening te laden niet Desktop:</a> ACSD-58442 herstelt de flard van Adobe Commerce waar de apparaten met een breedte van 768px als mobiel worden behandeld, veroorzakend het menu en de kopbal in plaats in een mobiele mening te laden van een bureaublad. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.50 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>17 oktober 2024</td>
  </tr>
</table>
