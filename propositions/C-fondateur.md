## Jean Calvain Doumba

Fondateur et CTO de **DaDa** · Garoua, Cameroun

Je construis DaDa, une infrastructure de confiance pour la location au Cameroun : le loyer passe en séquestre via Mobile Money, et chacun est payé selon ce qu'il a signé.

### Le problème

La location camerounaise passe par les démarcheurs. Le ministère de l'Habitat ne recensait que 61 agents immobiliers agréés en 2020 ; la grande majorité exerce sans carte, payée en cash, et se fait souvent court-circuiter par le bailleur une fois le locataire trouvé. Le locataire, lui, avance plusieurs mois de loyer sans aucun recours.

### Ce que DaDa change

- **L'agent** signe un mandat avec le bailleur. Sa commission est prélevée à la source, sur le séquestre.
- **Le locataire** paie par Mobile Money et dispose de 72 h pour vérifier le logement avant que l'argent ne soit libéré. Il ne paie aucun frais.
- **Le bailleur** reçoit un loyer tracé, avec quittance, et peut confier à DaDa la collecte des mois suivants.

### Comment je construis

- L'argent d'abord : la machine à états, puis l'isolation du module de paiement, et l'appel au prestataire en dernier.
- Le prestataire de paiement est la seule source de vérité sur l'argent. L'application ne décide jamais seule d'un statut.
- Pensé pour un Android d'entrée de gamme, en plein soleil, sur un réseau qui coupe.
- Trois applications (API Laravel, site Next.js, mobile Expo), plus de 2 500 tests, une CI sur chaque dépôt.

### Me parler

<!-- Adapter à ce que tu cherches vraiment ; une liste vague se lit comme un appel à tout le monde. -->
Agents et agences immobilières, ingénieurs que les paiements Mobile Money intéressent, partenaires de paiement : écris-moi.

<!-- calvinopro.com ne répondait pas le 2026-10-04 : remettre le lien quand le site répond. -->
[LinkedIn](https://www.linkedin.com/in/jean-calvain-doumba) · [Telegram](https://t.me/calvino_pro) · [Email](mailto:jeancalvaindoumba07@gmail.com)

`Calvino Pro 👌`
