# 🛠️ Admin & maintenance — GuillaumEvent

L'installation est **terminée**. Ce document récapitule comment gérer le site au quotidien.

## ⚙️ Mise en place (déjà faite — pour mémoire)
- Dépôt GitHub : **guillaume-KLN/GuillaumEvent**
- Hébergement : **Netlify** (déploiement auto depuis `main`), domaine **dj-gv.fr** (OVH, DNS Netlify, HTTPS)
- Admin : **Decap CMS** sur `/admin/`, connexion **GitHub** via les fonctions Netlify `netlify/functions/auth.js` + `callback.js`
- Variables d'environnement Netlify : `GITHUB_CLIENT_ID`, `GITHUB_CLIENT_SECRET` (app OAuth GitHub « GuillaumEvent Admin »)

## 🖼️ Gérer le contenu (sans toucher au code)
Va sur **https://dj-gv.fr/admin/** → connexion GitHub. Trois sections :

| Section | Ce que tu gères |
|---|---|
| **Galerie photos** | Photos de la page Photos (image, légende, taille). Affichage en mosaïque auto (proportions conservées). |
| **Visuels du site** | Ta photo « Qui suis-je » + le visuel matériel/setup. |
| **Partenaires** | Logos par catégorie : Wedding planners, Lieux, Traiteurs, Photographes. |

→ Ajoute / modifie → **Publish**. Le site se met à jour tout seul en ~1 min.

## 🔄 Quand le code change (modifs faites en dehors de l'admin)
Comme le site vit sur GitHub, il faut **renvoyer les fichiers modifiés** (GitHub → *Add file → Upload files*), puis Netlify redéploie automatiquement.
- ⚠️ **Ne jamais réuploader le dossier `data/`** : il contient le contenu géré par l'admin (photos, partenaires).

## 🌐 Domaine
Le site est sur **dj-gv.fr**. Pour passer à **guillaumevent.fr** plus tard : acheter le domaine, le relier à Netlify, puis mettre à jour `canonical` / Open Graph / données structurées + redirection — voir avec l'assistant.

## ❓ Dépannage rapide
- **Login admin en boucle** : vérifier les 2 variables d'environnement Netlify + l'URL de callback de l'app GitHub (`https://dj-gv.fr/.netlify/functions/callback`).
- **Une modif n'apparaît pas** : attendre 1-2 min (redéploiement) puis `Ctrl`+`F5`.
- **Netlify ne déploie plus** : Site configuration → Build & deploy → vérifier le lien au dépôt `guillaume-KLN/GuillaumEvent`.
