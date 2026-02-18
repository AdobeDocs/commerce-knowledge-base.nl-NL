---
title: Test snel op productie als een actieve site hetzelfde domein gebruikt
description: Als u een live site hebt die wordt uitgevoerd op uw productiedomein ("example.com") en u uw nieuwe winkel op Adobe Commerce moet testen in de productieomgeving van de cloud-infrastructuur met Fastly CDN ingeschakeld, raden we u aan het subdomein te gebruiken (zoals "prod.example.com") en deze eerder aan Fastly toe te voegen voor testactiviteiten voorafgaand aan de introductie. In dit artikel worden de details besproken en worden nuttige koppelingen naar de gerelateerde Adobe Commerce-documentatiebronnen weergegeven.
exl-id: bc9d11c8-ce47-461d-b5b8-c03494bc4ceb
feature: Cache
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# Test snel op productie als een actieve site hetzelfde domein gebruikt

Als u een live site hebt die wordt uitgevoerd op uw productiedomein (`example.com`) en u uw nieuwe winkel op Adobe Commerce moet testen op de productieomgeving van de cloud-infrastructuur met snelwerkende CDN, raden we u aan het subdomein (zoals `prod.example.com` ) te gebruiken en deze eerder aan Fastly toe te voegen voor testactiviteiten die worden uitgevoerd voordat u de toepassing start. In dit artikel worden de details besproken en worden nuttige koppelingen naar de gerelateerde Adobe Commerce-documentatiebronnen weergegeven.

## Probleem

De huidige winkel waarin het productiedomein `example.com` wordt gebruikt, is actief. U moet echter wel uw nieuwe winkel testen, die met Adobe Commerce is gebouwd op cloudinfrastructuur en die is geïmplementeerd in de productieomgeving, met de snelst service voor volledige paginacache ingeschakeld.

Het probleem is dat de productieomgeving van uw Adobe Commerce op het project van de wolkeninfrastructuur het zelfde levende domein (`example.com`) gebruikt, en u kunt niet uw nieuwe plaats aan dit domein schakelen, gelijktijdig hebbend uw huidige levende opslag die - op het zelfde domein loopt.

### Waarom Fastly gebruiken voor het testen op de productieomgeving?

In theorie kunt u het gebruik van de snelste CDN overslaan en uw Adobe Commerce testen op de cloudinfrastructuur in de productieomgeving zonder dat de volledige paginacache is ingeschakeld.

Als cache van volledige pagina is ingeschakeld, werkt de winkel echter anders. U kent nooit de werkelijke live prestaties van uw site als u deze nog niet met CDN hebt getest voordat u de site start. Het testen van je winkel op Production met Fastly CDN ingeschakeld is de officiële Adobe Commerce aanbeveling.

## Oplossing: subdomein van de gebruiksproductie

Gebruik het eerste-niveau subdomain (`prod.example.com`) voor uw nieuwe Adobe Commerce op de opslag van de wolkeninfrastructuur op het milieu van de Productie terwijl het houden van de huidige levende plaats op het basisdomein (`example.com`).

Wanneer u uw Adobe Commerce-project voor cloudinfrastructuur wilt plannen, kunt u een dergelijk subdomein voor productie opgeven en het team voor cloudinfrastructuur verzoeken het subdomein naar de snelservice te verwijzen.

Voer de volgende stappen uit om het subdomein in uw Adobe Commerce te verwerken voor een infrastructuurproject in de cloud:

* [ voorlegt een steunkaartje ](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) verzoekend om subdomain aan de Fastly dienst/Nginx configuratie (voor Adobe Commerce op de architectuur van het de planplan van de wolkeninfrastructuur Pro) toe te voegen.
* Vorm de overeenkomstige DNS montages op uw kant.

Nadat u de stappen voor subdomeinconfiguratie hebt uitgevoerd, moet u ook de volgende stappen uitvoeren om uw productiedomein voor het SSL-certificaat te valideren:

* Upload het DNS TXT-record voor SSL-validatie van uw productiedomein.
* [ legt een steunkaartje ](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) voor het verzoeken om het productiedomein voor het SSL certificaat te bevestigen.

Door het subdomein te gebruiken, kunt u in de toekomst een &quot;zachte opstart&quot; van uw winkel uitvoeren, aangezien voor een dergelijke opstart alleen de bijbehorende DNS-instellingen hoeven te worden bijgewerkt.

## Gerelateerde documentatie

In onze kennisbasis voor ondersteuning:

* [ vorm snel DNS montages op het Opvoeren en de milieu&#39;s van de Productie ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/configure-fastly-dns-settings-on-staging-and-production-environments.html)
* [ Opstelling snel voor het plan van de Aanzet op wolk ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/set-up-fastly-for-starter-plan-on-cloud.html)
* [ Potentiële blokkers voor lancering op Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/blockers-launching-on-magento-commerce-cloud.html)

In onze documentatie voor ontwikkelaars:

* [ Snelle Overzicht ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [ ga levende checklist: DNS configuraties voor Fastly ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html)
