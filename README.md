# CarthageSSO — sso-carthage (challenge7)

| | |
|---|---|
| **Catégorie** | Web / Auth |
| **Difficulté** | Moyen |
| **Points** | 350 |
| **Topics** | OAuth → Broken Authentication → Session Management → IDOR |
| **Port** | 8007 (`http://localhost:8007` — utilise impérativement ce hostname) |
| **Flag** | `UNIALONE{...}` |

## Lancement

```bash
cd /home/omar/ctf/challenge7/sso-carthage/ctf
docker compose up -d
```

## Scénario

**CarthageSSO** est le fournisseur d'identité maison de Carthage Systems (v0).
Le **portail de facturation** s'y connecte via un flux OAuth **implicite**.
Un compte de test t'est fourni sur le fournisseur : `employe1@carthage.tn` /
`employe2026`.

Une « page d'attaquant » est simulée à `http://localhost:8007/attacker` : tout
token présent dans le fragment d'une URL y est archivé publiquement
(`/attacker/log`).

Objectif : lire la **facture #482**, classée confidentielle (direction).

## Format du flag

```
UNIALONE{...}
```

## Notes

- La v0 du SSO a plusieurs dettes techniques assumées : email non vérifié à
  l'inscription, validation de `redirect_uri` par simple préfixe, `state` non
  vérifié par le client, clé de signature de session client faible.
- Explore d'abord le flux complet : inscription → connexion SSO → portail.
# chatahni-tarbahni
