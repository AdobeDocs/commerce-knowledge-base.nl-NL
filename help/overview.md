---
title: Adobe Commerce Support Knowledge Base
description: Alles wat u moet weten om problemen op te lossen en uw Commerce-winkel te onderhouden.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 6d22ea4725249df1528625672be405464b1411e8
workflow-type: tm+mt
source-wordcount: '920'
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
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25301"> los [!DNL New Relic] agentenkwesties met PHP 8.2 aan 8.3 verbetering in Adobe Commerce op:</a> wanneer u PHP van versie 8.2 aan 8.3 bevordert, zou u kunnen opmerken dat de [!DNL New Relic] agent ophoudt werkend in uw milieu van Adobe Commerce. Dit probleem is waargenomen in ophalings- en productieomgevingen. In dit artikel vindt u stappen om dit probleem op te lossen en op te lossen.
    </td>
    <td>Nieuw artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25321">[!DNL Security Scan Tool] retourneert "APSByy-xx security updates available", zelfs als de patch al is toegepast: </a> De [!DNL Security Scan Tool] rapporteert APSByy-xx security updates beschikbaar voor Adobe Commerce en Magento Open Source, ook al hebt u de patch al toegepast. U kunt deze melding negeren.
    </td>
    <td>Nieuw artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61845-error-occurs-for-requests-with-text-html-accept-header"> ACSD-61845: De fout komt voor voor verzoeken met text/html keurt kopbal goed:</a> het ACSD-61845 flard lost de kwestie op waar een HTTP- verzoek met slechts een text/html kopbal een 500 fout toe te schrijven aan media type wanverhoudingen in reactie behandeling. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.54 is geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61200-fixes-discount-tax-compensation-in-sales-total-calculations"> ACSD-61200: De onjuiste compensatie van de kortingenbelasting in verkoop totale berekeningen:</a> ACSD-61200 het flard bepaalt de kwestie waar het Bedrag van de Compensatie van de Belastingkorting van de Korting van de Korting en het Belastingbedrag van de Schrapping van de Schrapping van het Totale Bedrag en het Totale Ware Berekening ontbreken, resulterend in discrepanties, die tot discrepanties tussen gegevens van de opdracht gegevens van de gegevens van de gegevens van de gegevens van de gegevens van de opdracht van de opdracht van de. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.54 is geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61199-cms-page-hierarchy-tab-doesnt-display-proper-tree-structure"> ACSD-61199: Het 1&rbrace; lusje van de pagina van CMS toont geen juiste boomstructuur:</a> het markering ACSD-61199 bevestigt de kwestie waar het 3&rbrace; lusje van de pagina van CMS geen juiste boomstructuur toont wanneer het uitgeven van een pagina van CMS met een bestaande Hiërarchie. [!UICONTROL Hierarchy][!UICONTROL Hierarchy] Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.54 is geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-60804-editing-customer-linked-to-deleted-company-causes-error"> ACSD-60804: Het uitgeven van een klant verbonden aan een geschrapt bedrijf resulteert in een fout:</a> ACSD-60804 herstelt de flard waar het uitgeven van een klant verbonden aan een geschrapt bedrijf een fout <em> Vraag aan een lidfunctie getSuperUserId () op ongeldig </em> veroorzaakt. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.53 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61522-email-in-name-fields-sends-invalid-order-confirmations"> ACSD-61522: De e-mailadressen in [!UICONTROL First] en [!UICONTROL Last Name] gebieden verzenden ongeldige orde bevestigingen:</a> ACSD-61522 flardmoeilijke situatie waar het mogelijk is om e-mailadressen in de gebieden van een gastklant in te gaan [!UICONTROL First Name] en [!UICONTROL Last Name], leidend tot ongeldige bericht van de ordbevestiging die wordt verzonden. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.54 is geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-62485-async-operations-all-consumer-stops-working-when-company-is-created"> ACSD-62485: <code>async.operations.all</code> de consument houdt op werkend wanneer het bedrijf wordt gecreeerd:</a> ACSD-62485 herstelt de flard waar de <code>async.operations.all</code> consument ophoudt werkend wanneer een B2B bedrijf wordt gecreeerd. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.54 is geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60684-graphql-product-sorting-by-multiple-fields-does-not-work-as-expected"> ACSD-60684: Het het productsorteren van GraphQL door veelvoudige gebieden werkt niet zoals verwacht:</a> het ACSD-60684 flard moeilijke situatie waar het het productsorteren van GraphQL door veelvoudige gebieden niet werkt wanneer het sorteren in variabelen wordt overgegaan. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.52 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-61553-cart-price-rule-discounts-are-incorrectly-calculated-when-multiple-discounts-with-different-priorities-are-applied"> ACSD-61553: [!UICONTROL Cart Price Rule] wordt verkeerd berekend wanneer de veelvoudige kortingen met verschillende prioriteiten worden toegepast:</a> ACSD-61553 flardmoeilijke moeilijke situatie waar [!UICONTROL Cart Price Rule] verkeerd wordt berekend wanneer de veelvoudige kortingen met verschillende prioriteiten worden toegepast. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.53 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58383-duplicate-credit-memos-from-simultaneous-refund-requests-via-rest-api"> ACSD-58383 Adobe Commerce flard: De dubbele creditmemo's van gelijktijdige terugbetalingsverzoeken via REST API:</a> het flard ACSD-58383 moeilijke situatie waar het uitgeven van een teruggave via REST API met twee identieke verzoeken die gelijktijdig worden uitgevoerd, in dubbele creditmemo's resulteert. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.55 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58471-dynamic-content-fails-load-product-detail-page"> ACSD-58471: De dynamische inhoud slaagt er niet in om op de pagina van het productdetail te laden, toen de bijbehorende regels van de catalogusprijs werden gepland:</a> het flard ACSD-58471 lost de kwestie op waar de dynamische inhoud niet op de pagina van het productdetail laadt, toen de bijbehorende regels van de catalogusprijs werden gepland. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.55 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>5 december 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58735-restricted-admin-cant-view-abandoned-shopping-carts"> ACSD-58735: Beperkte admin kan verlaten winkelwagentjes op klantenrekening voor bijbehorende website niet bekijken:</a> ACSD-58735 flardmoeilijke situatie waar een admin gebruiker met een beperkte rol de winkelwagentjes van verlaten klanten van <strong>[!UICONTROL Commerce Admin]</strong> niet kan bekijken &gt; <strong>[!UICONTROL Reports]</strong> &gt; <strong>[!UICONTROL Abandoned Carts]</strong> &gt; <strong>[!UICONTROL Select Cart]</strong> &gt; <strong>[!UICONTROL Shopping Cart]</strong> tabel. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.55 wordt geïnstalleerd.
    </td>
    <td>Nieuw artikel </td>
    <td>5 december 2024</td>
  </tr>
</table>
