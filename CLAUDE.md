# CLAUDE.md — ultreia-landing

## Contexte
Landing page d'Ultreia Audio (app d'histoires audio pour enfants, marché espagnol).
Prod : https://www.ultreia-audio.com — déployée automatiquement par Vercel à chaque push sur main.

## Règles
INTERDIT de modifier ou supprimer : .well-known/assetlinks.json, .well-known/apple-app-site-association, vercel.json. Ce sont les fichiers de deeplinks de l'app mobile (Android App Links / iOS Universal Links).

Tout push sur main part directement en production. Pour toute modification non triviale : travailler sur une branche, vérifier l'URL de preview Vercel, puis merger.

Site statique single-file : tout le HTML/CSS/JS vit dans index.html. Pas de framework, pas de build step.

Jamais de secrets, clés API ou tokens dans ce repo.

Langue du site : castillan (Espagne). Ton sobre et premium, public parents.

## Stack liée
Hébergement : Vercel (team ultreia-audio, projet ultreia-landing). Domaine : ultreia-audio.com (OVH). App mobile : com.ultreia.app (dev : Mayeul), liens profonds via Branch (ultreia.app.link).
