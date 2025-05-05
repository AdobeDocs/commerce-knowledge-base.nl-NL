---
title: Controleren op DDoS-aanval van CLI
description: Dit artikel spreekt over de kwestie van hoe te proberen om voor de Verdeelde Ontkenning van de aanvallen van de Lijn van het Bevel van uw server (CLI) te controleren.
exl-id: dfdef289-cf51-42d7-b3fb-d4d2d3760951
feature: Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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
   * [ Adobe Commerce en Magento Open Source logboeken plaatsen ](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cli/enable-logging)
   * [ Adobe Commerce op de logboekplaatsen van de wolkeninfrastructuur ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/test/log-locations)
1. Gebruik de CLI om al uw huidige internetverbindingen te controleren met de opdracht `netstat` : `netstat -na` . Hiermee worden alle actieve verbindingen met de server weergegeven. Hier zou u teveel verbindingen kunnen opmerken die van het zelfde IP adres komen.
1. Gebruik de volgende opdracht om uw bestaande verbindingen verder te beperken tot verbindingen die alleen tot verbinding maken met poort 80 (de http-poort voor uw website), zodat u te veel verbindingen van één IP-adres of groep IP-adressen kunt sorteren en herkennen. `netstat -an | grep :80 | sort` U kunt dezelfde opdracht herhalen voor https op poort 443: `netstat -an | grep :443 | sort` . Een andere mogelijkheid is om de oorspronkelijke opdracht uit te breiden naar zowel poort 80 als poort 443: `netstat -an | egrep ":80|:443" | sort` .
1. Als u wilt zien of er veel actieve `SYNC_REC` op de server voorkomen, gebruikt u de opdracht:     `netstat -n -p|grep SYN_REC | wc -l`     Dit is gewoonlijk minder dan 5, maar het zou veel hoger voor een aanval kunnen zijn DDoS, hoewel voor sommige servers een hoger aantal een normale voorwaarde zou kunnen zijn.
1. Als u alle IP-adressen wilt weergeven die `SYNC_REC` statussen verzenden, gebruikt u de opdracht: `netstat -n -p | grep SYN_REC | sort -u` .
1. Als u alle unieke IP-adressen met `SYNC_REC` statussen wilt weergeven, gebruikt u de opdracht: `netstat -n -p | grep SYN_REC | awk ‘{print $5}’ | awk -F: ‘{print $1}’` .
1. U kunt ook de opdracht `netstat` gebruiken om het aantal verbindingen te tellen en te berekenen dat door elk IP-adres aan uw server wordt gemaakt: `netstat -ntu | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n` .
1. Voor het weergeven van het aantal UDP- of TCP-protocolverbindingen die zijn verbonden met uw server, gebruikt u de opdracht: `netstat -anp |grep ‘tcp|udp’ | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Gebruik de opdracht: `netstat -ntu | grep ESTAB | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -nr` om gevestigde verbindingen te controleren in plaats van alleen alle verbindingen en het aantal verbindingen voor elk IP-adres weer te geven.
1. Om verbindingstellingen te tonen die door IP adres aan haven 80 worden vermeld, gebruik het bevel: `netstat -plan|grep :80|awk {‘print $5’}|cut -d: -f 1|sort|uniq -c|sort -nk 1`.

Zorg ervoor u iemand hebt om juiste analyse aan de gegevens te geven u vindt om te bepalen als u in feite een aanval DDoS hebt. Het gebruiken van `netstat` bevelen van uw server CLI in deze stappen hierboven zal u helpen analyseren als u een aanval van DDoS ervaart, maar het gebruiken van de producten van de softwareanalyse die specifiek worden ontworpen om aanvallen te helpen identificeren DDoS, samen met juiste analyse, zijn uw beste hulpmiddelen om bedreigingen te identificeren DDoS.

Als u vindt dat u onder aanval DDoS bent, kunt de stappen u afhangen van uw netwerkconfiguratie en hoe de aanval DDoS voorkomt, maar het algemene advies is uw ISP te contacteren, een nieuw IP adres voor uw server te krijgen, en/of de beroeps van IT te raadplegen die in de behandeling van kwesties DDoS worden gekwalificeerd om op uw bijzondere situatie te analyseren en te adviseren.

## Verwante lezingen in onze ontwikkelaarsdocumentatie:

* [ bescherming DDoS ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/cdn/fastly#ddos-protection)
* [ Gebruikend CLI bevelen ](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli)
* [ CLI van de Wolk voor Commerce ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview)
