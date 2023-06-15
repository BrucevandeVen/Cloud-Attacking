# Welke hackmethodes zijn toepasbaar om cloud omgevingen te hacken?

## Inleiding (Brainstorm)
Ik ga manieren van [Beau Bullock](https://www.linkedin.com/in/beaubullock/) gebruiken om een of meerdere cloud test omgevingen op te zetten voor Microsoft Azure en Amazon Web Services. Hierbij onderzoek ik hoe deze cloud services en technologiën werken. Na deze omgeving opgezet te hebben ga ik cloud hack methodes gebruiken om deze te exploiten.

## DOT Framework
Voor het beantwoorden van deze vraag heb ik deze DOT Framework methodes gebruikt:  
![image](https://github.com/BrucevandeVen/Cloud-Exploits/assets/58031089/65553b18-3771-445c-b5a5-295cf8435047)


## Inhoudsopgave
- 1. Breaching the Cloud
- 2. Opzet
- Azure
- AWS
- Terraform
- Goats
- 3. Red Teaming
- Privilege Escalation
- SSRF
- 4. Bevindingen scenario's

## 1. Breaching the Cloud (Community Research & Available Product Analysis)
[Breaching the Cloud](https://btc.breakforge.io/) is een website die ondersteuning bied voor het opzetten van een test cloud omgeving. Deze website is opgezet door [Beau Bullock](https://www.linkedin.com/in/beaubullock/), een Cyber Security expert die zich ook in zet voor de uitbreiding van de kenniseconomie. Op de website staat stap voor stap beschreven wat er nodig is om een test cloud omgeving op te zetten, ook is er een VM waar alle benodigde tools al voor geïnstalleerd zijn.

## 2. Opzet (Document Analysis)
De benodigdheden voor de cloud test omgeving zijn:  
- Azure Account  
Het moet een Global Access account zijn, dus dit kan niet met mijn school account.
- Amazon Web Services
- Linux VM  
Ik ga VMware gebruiken om mijn VM's te gebruiken. Ik kan kiezen tussen mijn eigen Kali Linux VM of de [VM van Breaching the Cloud](https://btc.breakforge.io/2-Linux-VM-Setup-87fca913978c409e9d21b61878ef28b5). Als ik mijn eigen Kali VM gebruik moet ik de AWS CLI en Terraform installeren.

### Azure (Document Analysis)
Ik heb een Azure account aangemaakt met mijn privé e-mail adres, omdat het niet mogelijk is Azure AD (Active Directory) te openen/bewerken op het Fontys account omdat deze door de Fontys wordt beheerd.  
![image](https://user-images.githubusercontent.com/58031089/233789375-d6d62fc9-0ea9-4368-adb9-5feef719723b.png)  
Dit is een screenshot van de Azure Portal wanneer ik de Azure AD probeer te openen als ik ingelogd ben met mijn Fontys account.  
Hierdoor ben ik genoodzaakt mijn eigen credit card te gebruiken.

### AWS (Document Analysis)
Na een AWS account aangemaakt te hebben met mijn privé e-mail, heb ik een Admin account toegevoegd aan de IAM users zodat ik via terraform de rechten heb cloud omgevingen te bouwen in mijn AWS account.  
Vanwege dezelfde reden als bij Azure, heb ik bij AWS ook mijn eigen credit card gebruikt.

### Terraform (Prototyping)
Terraform is een dienst die wordt aangeboden door HashiCorp, een bedrijf dat gespecialiseerd is in Cloud infrastructuurautomatisering. Terraform een platform waarmee je de infrastructuur van je applicaties kunt beheren en automatiseren.  
Als je een applicaties in de cloud wilt implementeren, moet je verschillende resources, zoals servers, netwerken en databases, handmatig configureren. Terraform  maakt dit proces makkelijker door je te helpen bij het definiëren van je infrastructuur in code, met behulp van een taal genaamd Terraform. Met Terraform kun je je infrastructuurconfiguraties beheren en wordt het dus eenvoudiger complexere cloud omgevingen op te zetten. Het biedt ook functies zoals samenwerking tussen teamleden, versiebeheer en het bijhouden van wijzigingen. Wanneer je een wijziging aanbrengt in je infrastructuurconfiguratie, kan Terraform de wijziging automatisch doorvoeren, zodat je niet handmatig elke resource hoeft te configureren.  
Ik gebruik Terraform om de vulnerable cloud omgevingen te beheren zodat ik hackmethodes kan testen op de omgevingen.

### (Cloud) Goats (Prototyping & Document Analysis)
(Cloud) Goats zijn vulnerable cloud omgevingen die opgezet zijn met een cloud infrastructuurautomatiserings tool zoals Terraform. Deze omgevingen zijn ontworpen om te hacken en bestaan meerendeels uit configuratie fouten. Voorbeelden van AWS Cloud Goats en hoe je deze zelf op zet zijn te vinden op [RhinoSecurityLabs/cloudgoat](https://github.com/RhinoSecurityLabs/cloudgoat).

## 3. Red Teaming (Document Analysis)
![image](https://github.com/BrucevandeVen/Cloud-Exploits/assets/58031089/5edaa4f6-0150-4502-9de8-5b7798cddf3a)  
Om de Cloud omgevingen aan te vallen heb ik dit framework gevolgd van [BDO](https://www.bdo.ae/en-gb/services/advisory/technology-advisory-services/cybersecurity-services-en/red-teaming). Echter, aangezien ik niet veel ervaring heb met het exploiten van Cloud omgevingen, heb ik waar nodig was de Cheat Sheets van de Goats gebruikt om het proces te leren.  

### Privilege Escalation (Prototyping)
Het is mogelijk via verschillende methodes een minder bevoegde gebruiker, meer rechten te geven als er misconfiguratie heeft plaatsgevonden. Als een AWS Cloud omgeveving bijvoorbeeld een Lambda functie heeft die rollen kan bepalen voor gebruikers en deze niet goed is geconfigureerd, kan een gebruiker met minder rechten via deze functie meer rechten krijgen.  
![image](https://github.com/BrucevandeVen/Cloud-Exploits/assets/58031089/09015bae-6e5c-4696-94a4-606e2b56f3d5)  
Hierboven een voorbeeld van hoe de exploitatie flow er uit zou zien bij zo'n dergelijke misconfiguratie.  
Als de gebruiker eenmaal meer rechten heeft verkregen kunnen er een aantal configuraties en soms ook gevoelige data ingezien of zelfs aangepast worden.  
  
Ik ben dieper op de scenario's ingegaan door ze zelf te exploiten en mijn Red Teaming vaardigheden toe te passen. Bij het scenario "ecs_takeover" heb ik gevonden dat er misconfiguraties zijn gebruikt om de omgeving vulnerable te maken dit is bij andere scenario's ook het geval. Hieronder een aantal voorbeelden:  
![image](https://github.com/BrucevandeVen/Cloud-Exploits/assets/58031089/3edff46f-ab1a-4f05-af10-3569e42480ca)  
In de afbeelding hierboven is te zien dat er een IAM gebruiker de rechten heeft om van policy versie te veranderen (huidige versie is 1), dit kan al een misconfiguratie zijn aangezien de policy aan deze gebruiker is toegewezen met alleen "Read" rechten. De andere policy versies bevatten andere rechten:  
- V2  
Deze policy version heeft alleen het recht om “iam:Get” uit te voeren op resources die binnen een bepaalde tijd aangemaakt zijn. V2 geeft dus bijna geen rechten en minder rechten dan V1 (waar we nu in zitten).  
- V3  
V3 heeft heel veel rechten, alle acties op alle resources zijn toegestaan.  
- V4  
Bij V4 lijkt er veel te mogen, maar door Effect “Deny” en de IP adres beperkingen zal het voor ons niet beter zijn dan de huidige V1 policy.  
- V5  
De V5 policy version geeft ons het recht een aantal waardes uit te lezen omtrent S3 buckets. Dit heeft niet veel meerwaarde aangezien we alleen kunnen lezen.  
  
Kortom, de gebruiker kan zijn policy versie veranderen naar V3 en dan zichzelf administrator rechten geven en de gehele Cloud-omgeving tot zijn macht krijgen, waar ook gevoelige data in kan staan of dure resources aanmaken zodat de originele eigenaar geld verliest.  
Er kunnen hier dus 2 misconfiguraties aanwezig zijn:  
1. De IAM user hoort geen rechten te hebben om van policy versie te wisselen in policy versie V1
2. Policy versie 3 hoort niet te bestaan i.v.m. te veel rechten. 

### SSRF (Prototyping)
SSRF exploits zijn mogelijk als er een vulnerable web applicatie is gedeployed in de Cloud omgeving.  
![image](https://github.com/BrucevandeVen/Cloud-Exploits/assets/58031089/8477964b-d800-413f-885e-0f12606ebabf)  
Na het exploiten van een Cloud omgeving en het uitvoeren van privilege escaltion, komen er meer methodes vrij die helpen bij het verkrijgen van data voor onbevoegden.  
![image](https://github.com/BrucevandeVen/Cloud-Exploits/assets/58031089/7195a072-5397-47b8-a4d0-5b9baaeb5a55)  
Hierboven een voorbeeld van hoe een dergelijk scenario er uit zou kunnen zien.

## 4. Bevindingen scenario's (Root Cause Analysis)
Door de scenario's te onderzoeken en zelf hands-on te exploiten, heb ik bevonden dat de scenario's vooral misconfiguraties bevatten en geen gebruik maken van andere technieken, omdat een Cloud omgeving constant wordt ge-update zal een dergelijke vulnerability niet lang bruikbaar zijn in een scenario die daarvoor ontworopen is. 






