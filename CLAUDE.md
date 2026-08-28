# CLAUDE.md — ultreia-landing

## Contexte
Landing page d'Ultreia Audio (app d'histoires audio pour enfants, marché espagnol).
Prod : https://www.ultreia-audio.com — déployée automatiquement par Vercel à chaque push sur main.

## Règles
INTERDIT de modifier ou supprimer : .well-known/assetlinks.json, .well-known/apple-app-site-association, vercel.json. Ce sont les fichiers de deeplinks de l'app mobile (Android App Links / iOS Universal Links).

Tout push sur main part directement en production. Pour toute modification non triviale : travailler sur une branche, vérifier l'URL de preview Vercel, puis merger.

Site statique multi-pages, une page par dossier. Pas de framework, pas de build step.

    index.html              ->  /
    privacy/index.html      ->  /privacy
    terms-of-use/index.html ->  /terms-of-use

Chaque page est un fichier HTML autonome et complet (tout le CSS/JS/polices/images embarqués) : aucune ressource partagée entre les pages, une modification de style doit être répercutée page par page.

Ces fichiers sont des exports Claude Design (`<x-dc>`) empaquetés : le HTML réel de la page est une chaîne JSON dans `<script type="__bundler/template">`, et les polices, images et scripts sont en base64 (parfois gzip) dans `<script type="__bundler/manifest">`. Pour éditer une page : décoder le JSON du template, modifier, puis ré-encoder avec `json.dumps(..., ensure_ascii=False)` suivi de `.replace('</', '<\\u002F')`. Ne jamais éditer le template à la main dans le fichier. Le plus propre reste de réexporter la page depuis Claude Design.

Ce repo est PUBLIC. Jamais de secrets, clés API, tokens, ni documentation d'API interne (contrats OpenAPI, specs backend) dans ce repo.

Langue du site : castillan (Espagne). Ton sobre et premium, public parents.

## Stack liée
Hébergement : Vercel (team ultreia-audio, projet ultreia-landing). Domaine : ultreia-audio.com (OVH). App mobile : com.ultreia.app (dev : Mayeul), liens profonds via Branch (ultreia.app.link).
