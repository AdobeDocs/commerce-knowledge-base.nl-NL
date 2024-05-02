---
title: Test snel op productie als een actieve site hetzelfde domein gebruikt
description: Als u een live site hebt die wordt uitgevoerd op uw productiedomein ("example.com") en u uw nieuwe winkel op Adobe Commerce moet testen in de productieomgeving van de cloud-infrastructuur met Fastly CDN ingeschakeld, raden we u aan het subdomein te gebruiken (zoals "prod.example.com") en deze eerder aan Fastly toe te voegen voor testactiviteiten voorafgaand aan de introductie. In dit artikel worden de details besproken en worden nuttige koppelingen naar de gerelateerde Adobe Commerce-documentatiebronnen weergegeven.
exl-id: bc9d11c8-ce47-461d-b5b8-c03494bc4ceb
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Test snel op productie als een actieve site hetzelfde domein gebruikt

Als u een live site in gebruik hebt op uw productiedomein (`example.com`) en u moet uw nieuwe opslag op Adobe Commerce op de milieu van de Productie van de wolkeninfrastructuur testen met Fastly CDN toegelaten, adviseren wij gebruikend subdomain (als `prod.example.com`), na deze eerder aan Fastly toe te voegen, voor eventuele testactiviteiten voorafgaand aan de lancering. In dit artikel worden de details besproken en worden nuttige koppelingen naar de gerelateerde Adobe Commerce-documentatiebronnen weergegeven.

## Probleem

Je huidige winkel die de `example.com` productiedomein is actief en actief. U moet echter wel uw nieuwe winkel testen, die met Adobe Commerce is gebouwd op cloudinfrastructuur en die is geïmplementeerd in de productieomgeving, met de snelst service voor volledige paginacache ingeschakeld.

Het probleem is dat de productieomgeving van uw Adobe Commerce voor het infrastructuurproject in de cloud hetzelfde live domein gebruikt (`example.com`) en u kunt niet van de nieuwe site naar dit domein overschakelen terwijl de huidige live winkel op hetzelfde domein wordt uitgevoerd.

### Waarom Fastly gebruiken voor het testen op de productieomgeving?

In theorie kunt u het gebruik van de snelste CDN overslaan en uw Adobe Commerce testen op de cloudinfrastructuur in de productieomgeving zonder dat de volledige paginacache is ingeschakeld.

Als cache van volledige pagina is ingeschakeld, werkt de winkel echter anders. U kent nooit de werkelijke live prestaties van uw site als u deze nog niet met CDN hebt getest voordat u de site start. Het testen van je winkel op Production met Fastly CDN ingeschakeld is de officiële Adobe Commerce aanbeveling.

## Oplossing: subdomein van de gebruiksproductie

Het eerste subdomein gebruiken (`prod.example.com`) voor uw nieuwe Adobe Commerce over de cloud Infrastructure Store op de Production-omgeving en de huidige live site op het basisdomein te houden (`example.com`).

Wanneer u uw Adobe Commerce-project voor cloudinfrastructuur wilt plannen, kunt u een dergelijk subdomein voor productie opgeven en het team voor cloudinfrastructuur verzoeken het subdomein naar de snelservice te verwijzen.

Voer de volgende stappen uit om het subdomein in uw Adobe Commerce te verwerken voor een infrastructuurproject in de cloud:

* [Een ondersteuningsticket verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) het aanvragen om het subdomein toe te voegen aan de Fastly-service/Nginx-configuratie (voor Adobe Commerce op de Pro-planarchitectuur van de cloud-infrastructuur).
* Vorm de overeenkomstige DNS montages op uw kant.

Nadat u de stappen voor subdomeinconfiguratie hebt uitgevoerd, moet u ook de volgende stappen uitvoeren om uw productiedomein voor het SSL-certificaat te valideren:

* Upload het DNS TXT-record voor SSL-validatie van uw productiedomein.
* [Een ondersteuningsticket verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) vragen om het productiedomein voor het SSL-certificaat te valideren.

Door het subdomein te gebruiken, kunt u in de toekomst een &quot;zachte opstart&quot; van uw winkel uitvoeren, aangezien voor een dergelijke opstart alleen de bijbehorende DNS-instellingen hoeven te worden bijgewerkt.

## Gerelateerde documentatie

In onze kennisbasis voor ondersteuning:

* [Vorm de Snelle montages DNS op het Opvoeren en de milieu&#39;s van de Productie](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/configure-fastly-dns-settings-on-staging-and-production-environments.html)
* [Snelheid instellen voor starterabonnement in cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/set-up-fastly-for-starter-plan-on-cloud.html)
* [Potentiële blokkeerders voor lancering op Adobe Commerce op wolkeninfrastructuur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/blockers-launching-on-magento-commerce-cloud.html)

In onze documentatie voor ontwikkelaars:

* [Snelle overzicht](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [Live checklist: DNS-configuraties voor snel](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html)
