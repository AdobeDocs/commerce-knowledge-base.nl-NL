---
source-git-commit: 88a2b8fe11d718f33c26bbc6f407c55d9f1fd189
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---
# Handleiding KB-labels

Dit document bevat richtlijnen voor het toevoegen van labels aan artikelen in de Adobe Commerce Support Knowledge Base.
De etiketten (ook genoemd markeringen) verbeteren het zoeken ervaring in de [&#x200B; Kennisbank van de Steun van Adobe Commerce &#x200B;](https://support.magento.com/hc/en-us).
Labels worden toegevoegd in het veld &quot;labels&quot; in de metagegevenssectie van een artikelbestand, gescheiden door komma&#39;s, zonder ruimte tussen een komma en het volgende label.
Zie [../../.github/CONTRIBUTING.md#metadata ] voor meer informatie.

## Algemene bepalingen

Voeg voor elk artikel de volgende labeltypen toe:

* Label(s) voor product(en). (vereist)
* Label(s) voor betrokken versies. (vereist, behalve artikelen voor algemene ondersteuning)
* Label voor inhoudstype. (vereist)
* Labels voor belangrijke technische componenten.(indien van toepassing)
* Labels voor proces/functionaliteit die problemen oplost/wordt beschreven. (indien van toepassing)
* Labels voor de uitgifte die wordt vastgesteld/beschreven. (indien van toepassing)

Zie de secties hieronder voor gedetailleerde aanbevelingen over hoe te om etiketten voor elk van deze etikettypes te bepalen.

## Etiketten voor producten

<table>
<tbody>
  <tr>
    <th>Productnaam</th>
    <th>Label</th>
  </tr>
  <tr>
    <td>Adobe Commerce (alle implementatiemethoden) </td>
    <td>
    "Adobe Commerce,cloudinfrastructuur,op locatie"
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce over cloudinfrastructuur</td>
    <td>
      "Adobe Commerce,cloudinfrastructuur"
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce ter plaatse</td>
    <td>"Adobe Commerce,ter plaatse"</td>
  </tr>
  <tr>
    <td>Magento Business Intelligence (MBI)</td>
    <td>
        "Magento Business Intelligence,MBI"
    </td>
  </tr>
   <tr>
    <td>Magento Open Source</td>
    <td>
        "Magento Open Source"
    </td>
  </tr>
  <tr>
    <td>B2B voor Adobe Commerce</td>
    <td>"B2B"</td>
  </tr>
  <tr>
    <td>PWA voor Adobe Commerce</td>
    <td>"PWA"</td>
  </tr>
  <tr>
    <td>Venia storefront</td>
    <td>"Venia"</td>
  </tr>
  <tr>
    <td>Kwaliteitspatches, QPT</td>
    <td>"Kwaliteitspatches, QPT-patches"</td>
  </tr>
  </tbody>
</table>

## Labels voor productversies

* Voeg een apart label toe voor elke versie van Adobe Commerce. Voorbeeld: &quot;2.3.7&quot;
* Voeg geen labels voor intervallen toe.
Indien 2.3.0-2.3.5 aangetast, voeg dan toe: &quot;2.3.0,2.3.1,2.3.2,2.3.2-p2,2.3.3,2.3.3-p1,2.3.4,2.3.4-p2,2.3.5-p1,2.3.5-p2&quot;
NIET &quot;2.3.0-2.3.5&quot;
* Voeg geen labels met .x toe. Voorbeeld: &quot;2.3.x&quot;

## Labels voor inhoudstype (op basis van categorie)

<table>
  <tbody>
    <tr>
      <th>Categorie</th>
      <th>Label</th>
    </tr>
    <tr>
      <td>Aanbevolen procedures</td>
      <td>"best practices" (niet "best practices" of "best practices")</td>
    </tr>
    <tr>
      <td>
        Problemen oplossen
      </td>
      <td>
      "problemen oplossen"
      </td>
    </tr>
    <tr>
      <td>Procedure</td>
      <td>"hoe kan ik"</td>
    </tr>
    <tr>
      <td>Veelgestelde vragen</td>
      <td >"Veelgestelde vragen"</td>
    </tr>
  </tbody>
</table>

## Labels voor belangrijke technische componenten

* Gebruik hoofdletters volgens de officiële naamgeving van het onderdeel.
* Gebruik geen synoniemen, één label voor één component.
* U kunt de voorkeur geven aan één woordlabel, maar als de componentnaam meerdere woorden bevat, kunt u het beste verschillende woorden gebruiken. Voeg geen probleembeschrijvingen toe. Dat wil zeggen: &quot;Elasticsearch&quot; in plaats van &quot;problemen met de Elasticsearch&quot;.
* Als de inhoud alleen relevant is voor een bepaalde versie van de component, voegt u een label met naam + versie toe.\
  Voorbeeld: &quot;Elasticsearch 5&quot;. Als dit relevant is voor meerdere specifieke versies, voegt u verschillende labels van dit type toe. Voorbeeld: &quot;Elasticsearch 5&quot;, &quot;Elasticsearch 6&quot;. Gebruik, indien van toepassing, &quot;x&quot; voor meerdere versies. Voorbeeld: &quot;Elasticsearch 2.x&quot;

Voorbeelden:

* Elasticsearch
* &quot;New Relic&quot;
* &quot;Wizard Web Setup&quot;

## Labels voor proces/functionaliteit die wordt opgelost/beschreven

* Gebruik kleine letters, met uitzondering van correcte cijfers.
* Gebruik geen synoniemen, één label voor één entiteit.
* Eén woordlabel verdient de voorkeur. Voeg geen beschrijving van het probleem toe. Dat wil zeggen: &quot;database&quot; in plaats van &quot;database vastloopt&quot;.

Voorbeelden: 

* &quot;database&quot;
* &quot;cron&quot;
* &quot;implementatie&quot;
* &quot;massaupdate&quot;

## Labels voor de afgifte die wordt vastgesteld/beschreven

* Gebruik kleine letters, met uitzondering van eigenlijke getallen.
* Gebruik geen synoniemen, één label voor één entiteit.
* Eén woordlabel verdient de voorkeur. Zet geen foutbericht om in een label.

Voorbeelden:

* &quot;site down&quot;
* &quot;500 error&quot;
* &quot;geplakt brein&quot;
