# NextLance — Site légal (CGU, Privacy, Mentions, Support)

Site statique hébergé sur Vercel pour fournir les URLs publiques exigées par Apple App Store et Google Play.

## Structure

```
legal-website/
├── index.html      Landing
├── cgu.html        Conditions Générales d'Utilisation et de Vente
├── privacy.html    Politique de confidentialité (RGPD)
├── legal.html      Mentions légales
├── support.html    Page contact / support
├── style.css       CSS partagé
├── vercel.json     Headers de sécurité + clean URLs
└── README.md       Ce fichier
```

## Déploiement Vercel (1ʳᵉ fois)

```bash
cd legal-website
npx vercel --prod
```

Vercel va :
1. Te demander de te connecter (GitHub / email)
2. Créer un nouveau projet `legal-website`
3. Déployer sur `https://legal-website-<hash>.vercel.app`

## Brancher le sous-domaine `arintegration.fr`

Dans Vercel Dashboard → Project → Settings → **Domains** :

1. Ajouter `arintegration.fr` (si tu veux un site sur le domaine racine) OU
   `nextlance.arintegration.fr` (sous-domaine recommandé pour ne pas écraser ton site principal s'il existe)

2. Vercel te demande d'ajouter un **CNAME** dans Cloudflare :
   - Type : CNAME
   - Nom : `nextlance` (ou `@` pour la racine)
   - Cible : `cname.vercel-dns.com`
   - **Désactiver le proxy Cloudflare** (le nuage doit être gris, pas orange) sinon Vercel ne peut pas valider

3. Une fois validé, ton site est accessible sur `https://nextlance.arintegration.fr`

## URLs à fournir aux stores

Une fois déployé sur `nextlance.arintegration.fr` :

| Store | Champ | URL |
|---|---|---|
| Apple | Privacy Policy URL | `https://nextlance.arintegration.fr/privacy` |
| Apple | Marketing URL | `https://nextlance.arintegration.fr` |
| Apple | Support URL | `https://nextlance.arintegration.fr/support` |
| Google Play | Privacy Policy | `https://nextlance.arintegration.fr/privacy` |
| Google Play | Website | `https://nextlance.arintegration.fr` |

## Mise à jour

Quand tu modifies un fichier, redéploie :
```bash
cd legal-website
npx vercel --prod
```

Ou commit + push sur GitHub si tu connectes le repo à Vercel (auto-deploy).

## ⚠️ À mettre à jour à chaque évolution

- Numéro de version + date dans chaque page (pied de bloc `<p class="updated">`)
- Liste des sous-traitants dans `privacy.html` §5 si tu ajoutes / changes un service tiers
- Tarifs dans `cgu.html` §3 si tu changes les prix
