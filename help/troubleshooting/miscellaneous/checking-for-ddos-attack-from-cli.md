---
title: Controleren op DDoS-aanval van CLI
description: Dit artikel spreekt over de kwestie van hoe te proberen om voor de Verdeelde Ontkenning van de aanvallen van de Lijn van het Bevel van uw server (CLI) te controleren.
exl-id: dfdef289-cf51-42d7-b3fb-d4d2d3760951
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---

# Controleren op DDoS-aanval van CLI

Dit artikel spreekt over de kwestie van hoe te proberen om voor de Verdeelde Ontkenning van de aanvallen van de Lijn van het Bevel van uw server (CLI) te controleren.

## Betrokken producten en versies

* Adobe Commerce, alle versies
* Magento Open Source, alle versies

## Probleem

Uw website is langzaam, en u hebt geen toegang tot andere hulpmiddelen van de analysetoepassing, buiten uw CLI, om op een potentiële aanval te controleren DDoS. De symptomen van een aanval van DDoS kunnen sterk afhankelijk van uw netwerkconfiguratie, gebruikte software, enz. variëren.

Nochtans, wordt geadviseerd dat u de producten van de analysesoftware gebruikt die specifiek worden ontworpen helpen aanvallen identificeren DDoS.

## Oorzaak

Er zijn meerdere mogelijke oorzaken voor een trage website, zoals een langzaam presterende server, een hoog CPU-gebruik of een verkeerde configuratie in scripts, code of goedkope hardware. Soms kan dit het gevolg zijn van een aanval van de DDoS. Twee van de basishulpmiddelen u voor een aanval moet controleren DDoS zijn uw logboeken van Adobe Commerce en uw CLI.

Nogmaals is het belangrijk om op te merken dat het gebruiken van software die specifiek wordt ontworpen om aanvallen te identificeren DDoS zeer nuttig in uw onderzoek zou zijn.

## Oplossingsstappen

1. Controleer uw Adobe Commerce logboeken om te zien of iets anders naast een aanval DDoS voorkomt. Raadpleeg de volgende artikelen in de documentatie voor ontwikkelaars voor meer informatie:
   * [Locaties voor Adobe Commerce- en Magento Open Source-logbestanden](https://devdocs.magento.com/guides/v2.3/config-guide/cli/logging.html)
   * [Adobe Commerce op locatie voor logbestanden met cloud-infrastructuur](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html)
1. Gebruik uw CLI om uw huidige internetverbindingen te controleren met de `netstat` opdracht: `netstat -na`. Hiermee worden alle actieve verbindingen met de server weergegeven. Hier zou u teveel verbindingen kunnen opmerken die van het zelfde IP adres komen.
1. Om uw gevestigde verbindingsresultaten aan slechts die verder te beperken die op haven 80 (de http haven voor uw website) verbinden, zodat u te vele verbindingen van één IP adres of groep IP adressen kunt sorteren en erkennen, gebruik dit bevel: `netstat -an | grep :80 | sort`. U kunt dezelfde opdracht herhalen voor https op poort 443: `netstat -an | grep :443 | sort`. Een andere optie is het originele bevel tot zowel havens 80 als 443 uit te breiden: `netstat -an | egrep ":80|:443" | sort`.
1. Controleren of er veel actief zijn `SYNC_REC` komt op de server voor, gebruik het bevel:     `netstat -n -p|grep SYN_REC | wc -l`     Dit is gewoonlijk minder dan 5, maar het zou veel hoger voor een aanval kunnen zijn DDoS, hoewel voor sommige servers een hoger aantal een normale voorwaarde zou kunnen zijn.
1. Alle IP-adressen die worden verzonden weergeven `SYNC_REC` statussen, gebruik het bevel: `netstat -n -p | grep SYN_REC | sort -u`.
1. Om van alle unieke IP adressen verder een lijst te maken die verzenden `SYNC_REC` statussen, gebruik het bevel: `netstat -n -p | grep SYN_REC | awk ‘{print $5}’ | awk -F: ‘{print $1}’`.
1. U kunt ook de opdracht `netstat` bevel om het aantal verbindingen te tellen en te berekenen dat elk IP adres aan uw server maakt: `netstat -ntu | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Voor een overzicht van het aantal UDP- of TCP-protocolverbindingen die met uw server zijn verbonden, gebruikt u de opdracht: `netstat -anp |grep ‘tcp|udp’ | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Om gevestigde verbindingen, in plaats van enkel alle verbindingen te controleren, en de verbindingstelling voor elk IP adres te tonen, gebruik het bevel: `netstat -ntu | grep ESTAB | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -nr`.
1. Om verbindingstellingen te tonen die door IP adres aan haven 80 worden vermeld, gebruik het bevel: `netstat -plan|grep :80|awk {‘print $5’}|cut -d: -f 1|sort|uniq -c|sort -nk 1`.

Zorg ervoor u iemand hebt om juiste analyse aan de gegevens te geven u vindt om te bepalen als u in feite een aanval DDoS hebt. Met de `netstat` de bevelen van uw server CLI in deze stappen hierboven zullen u helpen analyseren als u een aanval van DDoS ervaart, maar het gebruiken van de producten van de softwareanalyse die specifiek worden ontworpen om aanvallen te helpen identificeren DDoS, samen met juiste analyse, zijn uw beste hulpmiddelen om bedreigingen te identificeren DDoS.

Als u vindt dat u onder aanval DDoS bent, kunt de stappen u afhangen van uw netwerkconfiguratie en hoe de aanval DDoS voorkomt, maar het algemene advies is uw ISP te contacteren, een nieuw IP adres voor uw server te krijgen, en/of de beroeps van IT te raadplegen die in de behandeling van kwesties DDoS worden gekwalificeerd om op uw bijzondere situatie te analyseren en te adviseren.

## Verwante lezingen in onze ontwikkelaarsdocumentatie:

* [DoS-beveiliging](https://devdocs.magento.com/guides/v2.3/cloud/cdn/cloud-fastly.html#ddos-protection)
* [CLI-opdrachten gebruiken](https://devdocs.magento.com/guides/v2.3/config-guide/deployment/pipeline/example/cli.html)
* [Cloud CLI voor Commerce](https://devdocs.magento.com/guides/v2.3/cloud/reference/cli-ref-topic.html)
