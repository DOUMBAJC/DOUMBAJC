## Jean Calvain Doumba

Ingénieur full-stack et fondateur de **DaDa** · Garoua, Cameroun

Je conçois des systèmes où l'argent circule par Mobile Money : paiements asynchrones, séquestre, réconciliation, et des apps qui continuent de fonctionner quand le réseau tombe.

---

### DaDa — le loyer en séquestre

Au Cameroun, le locataire avance souvent plusieurs mois de loyer, à un démarcheur ou à un bailleur, sans recours si le logement ne correspond pas. DaDa place ce paiement en séquestre : après avoir payé, le locataire a 72 h pour vérifier le logement avant que l'argent ne soit libéré. DaDa s'adresse d'abord aux agents immobiliers : leur commission est prélevée à la source, sur le séquestre.

```
paiement MoMo
 └▶ collecte par le prestataire de paiement
     └▶ séquestre 72 h
         ├─ confirmé, ou silence ─▶ versement (bailleur, agent)
         └─ litige ───────────────▶ médiation, compteur gelé
```

**Les décisions qui comptent**

- **DaDa ne détient jamais les fonds.** Le prestataire collecte et reverse ; l'application ne stocke qu'une référence, jamais un solde. Le séquestre vit dans le code, comme une machine à états : chaque état a sa table de transitions, et une transition interdite répond 409.
- **Le module de paiement est isolé** : schéma PostgreSQL et rôle SQL dédiés, une seule interface pour y entrer. Changer de prestataire revient à écrire un adaptateur.
- **Un webhook se vérifie avant de s'appliquer** : signature (RFC 9421), puis idempotence sur l'identifiant d'événement, puis transition. Un événement perdu est rattrapé par réconciliation depuis le grand livre.
- **L'agent terrain travaille hors ligne.** Photos géolocalisées et fiches attendent dans une file durable et remontent au retour du réseau.
- **Aucun jeton n'atteint le navigateur.** Le BFF du site garde les jetons en cookies `httpOnly`, et chaque requête est signée par une clé d'appareil non exportable.

**Stack** — Laravel 13 (monolithe modulaire, 8 modules) · PostgreSQL + PostGIS · Redis · Next.js 16 · React Native / Expo  
**Qualité** — plus de 2 500 tests Pest, CI sur les trois dépôts, conformité à la loi camerounaise 2024/017 sur les données personnelles  
**Statut** — pré-lancement. Le code est privé ; je présente volontiers l'architecture en visio.

<!-- À décommenter quand calvino-framework a un vrai README, des tests et une CI :
### Aussi

[**calvino**](https://github.com/DOUMBAJC/calvino-framework) — mini-framework PHP écrit de zéro : routeur, query builder, migrations, CLI.
-->

---

<!-- calvinopro.com ne répondait pas le 2026-10-04 : remettre le lien quand le site répond. -->
[LinkedIn](https://www.linkedin.com/in/jean-calvain-doumba) · [Telegram](https://t.me/calvino_pro) · [Email](mailto:jeancalvaindoumba07@gmail.com)
