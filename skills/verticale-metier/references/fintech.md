# Verticale — Fintech

Mis à jour : 26/09/2026
Périmètre : crowdfunding (prêt, obligations, equity), investissement, paiement, épargne.

> Points réglementaires = état des connaissances à la date ci-dessus, à faire confirmer par
> le client ou son juriste. Capsens signale, le client décide.

## Vocabulaire

| Terme | Sens |
|-------|------|
| PSFP | Prestataire de services de financement participatif — statut européen (règlement ECSP) |
| ECSP | Règlement européen sur le financement participatif |
| PSP | Prestataire de services de paiement (ex : Lemonway, Mangopay, Treezor) |
| Agent PSP | Plateforme qui opère sous l'agrément d'un PSP |
| Wallet | Compte de monnaie électronique ouvert chez le PSP (investisseur, projet, séquestre) |
| Séquestre (escrow) | Wallet où les fonds sont bloqués jusqu'à une condition (fin de rétractation, levée atteinte, jalon validé) |
| Cantonnement | Séparation obligatoire des fonds clients et des fonds propres de la plateforme |
| KYC / KYB | Vérification d'identité d'une personne physique / d'une personne morale (dont UBO) |
| UBO | Bénéficiaire effectif d'une personne morale |
| LCB-FT | Lutte contre le blanchiment et le financement du terrorisme |
| QA / test d'adéquation | Questionnaire de connaissances et d'expérience de l'investisseur |
| Investisseur averti / non averti | Catégorie ECSP qui conditionne les protections (test, simulation, rétractation) |
| KIIS | Fiche d'informations clés sur l'investissement (ECSP) |
| Bulletin de souscription | Document signé par l'investisseur pour chaque souscription |
| SPV | Société ad hoc portant un actif ou un projet |
| Tout-ou-rien | La collecte n'aboutit que si l'objectif est atteint, sinon remboursement intégral |
| Rétractation | Délai pendant lequel l'investisseur peut annuler sa souscription sans frais |
| SCA / 3DS | Authentification forte du payeur |
| VoP | Vérification du nom du bénéficiaire avant virement |

## Règles récurrentes (à vérifier avec le client)

### Statut réglementaire — toujours en premier
- Identifier le statut de la plateforme (PSFP, agent PSP, marque blanche sous l'agrément d'un
  tiers…) avant toute conception : il conditionne produits, parcours et plafonds.
- Un produit qui ressemble à un placement collectif géré (plusieurs actifs, gestion
  discrétionnaire) peut relever d'un autre régime (FIA) → à signaler.

### Investisseurs
- Non averti : test de connaissances, simulation de capacité à supporter les pertes, délai de
  rétractation (4 jours sous ECSP), remise du KIIS avant souscription.
- Plafond ECSP par projet sur 12 mois glissants (5 M€ à date) ; au-delà, autre régime.
- Avertissement sur le risque de perte en capital et l'illiquidité visible dans le parcours.
- Toute modification du questionnaire d'adéquation passe par le juriste du client.

### Flux d'argent
- Souscription = transfert vers un wallet de séquestre ; versement au projet après la fin de
  rétractation ou l'atteinte de l'objectif ; remboursement sinon.
- Les remboursements vers l'investisseur vont sur son wallet ; le retrait vers IBAN est un acte
  distinct, limité au solde disponible.
- Réconciliation au centime entre la plateforme et le PSP.
- Aucun montant calculé côté front ; la plateforme n'est jamais la source de vérité du solde.
- Soldes bloqués (cashback, parrainage réinvestissables uniquement) affichés séparément du disponible.

### KYC / KYB
- KYC délégué au PSP ; la capture d'identité passe par le parcours du PSP (souvent en webview,
  y compris sur mobile).
- Niveaux de KYC : un niveau allégé peut suffire pour déposer, le niveau renforcé est requis
  pour retirer.
- Personnes morales : KYB avec justificatifs UBO, souvent validé manuellement en back-office.
- Changement de PSP : en général pas de re-KYC complet, mais transfert réel des fonds, gel et
  réconciliation → à confirmer avec les deux PSP.

### Données et accès
- Cloisonnement strict : un utilisateur (ou une marque, en marque blanche) ne voit et n'exporte
  que ses propres données.
- Données personnelles vers des outils tiers hors UE (push, analytics, CRM) : identifiants
  pseudonymes uniquement, à faire valider par le DPO du client.
- Actions destructrices ou irréversibles (archivage, prorogation, annulation) réservées à l'admin,
  avec garde-fou et trace.

### Communication
- Emails transactionnels obligatoires en V1 dès qu'il y a un flux d'argent (confirmation de
  souscription, rétractation, remboursement, KYC) ; un échec d'envoi ne bloque pas l'action.
- Pas de dark pattern sur un produit régulé : signature jamais gamifiée, comptes à rebours
  factuels, pas de pression à l'investissement.

## Questions à poser en workshop

- Quel est votre statut réglementaire exact, et sous l'agrément de qui ?
- Quel PSP, et quels types de wallets existent déjà ?
- Quels produits : prêt, obligations, equity, royalties ? Tout-ou-rien ou pas ?
- Comment les investisseurs sont-ils catégorisés (averti / non averti) aujourd'hui ?
- Qui valide le KYB, et en combien de temps ?
- Que se passe-t-il si l'objectif de collecte n'est pas atteint ?
- Y a-t-il un marché secondaire prévu ? Sinon, comment l'illiquidité est-elle expliquée ?
- Qui côté client valide les textes réglementaires (juriste, conformité) ?

## Risques types (pré-mortem)

Pour chaque risque retenu : **scénario de casse → probabilité (H/M/B) → impact → comportement
attendu à écrire dans les cas limites du brief**. Retenir les 3 à 5 plus probables.

### Flux d'argent
- Notification PSP manquée, dupliquée ou hors ordre → état incohérent wallet vs plateforme
- Solde insuffisant au moment d'un débit ou d'une réservation
- Remboursement fait côté PSP sans trace côté plateforme
- Création de wallet en échec, cas multi-wallets
- Montants qui ne tombent pas juste (arrondis, centimes)

### KYC / conformité
- Statut KYC intermédiaire (en attente) non géré dans le parcours
- KYC rejeté ou incomplet → utilisateur bloqué sans issue claire
- Plafonds ou test investisseur non averti non appliqués

### États et concurrence
- Double soumission (double clic) → opération en double
- Délai dépassé côté PSP → opération en attente jamais reprise
- Annulation par l'utilisateur qui laisse un état orphelin

### Humain et back-office
- Email transactionnel non reçu (confirmation, rétractation)
- Action admin destructrice sans garde-fou
- Code de parrainage utilisé hors du contexte prévu

### Externe et migrations
- Indisponibilité du PSP ou d'un service tiers → souscriptions bloquées
- Changement d'API d'un tiers non anticipé
- Migration (PSP, montée de version) → régression le jour J
