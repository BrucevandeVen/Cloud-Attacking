# Welke hackmethodes zijn toepasbaar om cloud omgevingen te hacken?

## Inleiding
Ik ga manieren van [Beau Bullock](https://www.linkedin.com/in/beaubullock/) gebruiken om een of meerdere cloud test omgevingen op te zetten voor Microsoft Azure en Amazon Web Services. Hierbij onderzoek ik hoe deze cloud services en technologiën werken. Na deze omgeving opgezet te hebben ga ik cloud hack methodes gebruiken om deze te exploiten.

## Inhoudsopgave
- Breaching the Cloud
- Opzet
- Azure
- AWS
- Terraform
- Goats

## Breaching the Cloud
[Breaching the Cloud](https://btc.breakforge.io/) is een website die ondersteuning bied voor het opzetten van een test cloud omgeving. Deze website is opgezet door [Beau Bullock](https://www.linkedin.com/in/beaubullock/), een Cyber Security expert die zich ook in zet voor de uitbreiding van de kenniseconomie. Op de website staat stap voor stap beschreven wat er nodig is om een test cloud omgeving op te zetten, ook is er een VM waar alle benodigde tools al voor geïnstalleerd zijn.

## Opzet
De benodigdheden voor de cloud test omgeving zijn:  
- Azure Account  
Het moet een Global Access account zijn, dus dit kan niet met mijn school account.
- Amazon Web Services
- Linux VM  
Ik ga VMware gebruiken om mijn VM's te gebruiken. Ik kan kiezen tussen mijn eigen Kali Linux VM of de [VM van Breaching the Cloud](https://btc.breakforge.io/2-Linux-VM-Setup-87fca913978c409e9d21b61878ef28b5). Als ik mijn eigen Kali VM gebruik moet ik de AWS CLI en Terraform installeren.

### Azure
Ik heb een Azure account aangemaakt met mijn privé e-mail adres, omdat het niet mogelijk is Azure AD (Active Directory) te openen/bewerken op het Fontys account omdat deze door de Fontys wordt beheerd.  
![image](https://user-images.githubusercontent.com/58031089/233789375-d6d62fc9-0ea9-4368-adb9-5feef719723b.png)  
Dit is een screenshot van de Azure Portal wanneer ik de Azure AD probeer te openen als ik ingelogd ben met mijn Fontys account.

### AWS
Na een AWS account aangemaakt te hebben, heb ik een Admin account toegevoegd aan de IAM users zodat ik via terraform de rechten heb cloud omgevingen te bouwen in mijn AWS account. Bij AWS zijn er geen restricties door Fontys.

### Terraform
Terraform is een dienst die wordt aangeboden door HashiCorp, een bedrijf dat gespecialiseerd is in Cloud infrastructuurautomatisering. Terraform een platform waarmee je de infrastructuur van je applicaties kunt beheren en automatiseren.  
Als je een applicaties in de cloud wilt implementeren, moet je verschillende resources, zoals servers, netwerken en databases, handmatig configureren. Terraform  maakt dit proces makkelijker door je te helpen bij het definiëren van je infrastructuur in code, met behulp van een taal genaamd Terraform. Met Terraform kun je je infrastructuurconfiguraties beheren en wordt het dus eenvoudiger complexere cloud omgevingen op te zetten. Het biedt ook functies zoals samenwerking tussen teamleden, versiebeheer en het bijhouden van wijzigingen. Wanneer je een wijziging aanbrengt in je infrastructuurconfiguratie, kan Terraform de wijziging automatisch doorvoeren, zodat je niet handmatig elke resource hoeft te configureren.  
Ik gebruik Terraform om de vulnerable cloud omgevingen te beheren zodat ik hackmethodes kan testen op de omgevingen.



