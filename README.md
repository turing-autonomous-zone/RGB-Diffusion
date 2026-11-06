# RGB-Diffusion

Dépôt de **diffusion** des logiciels d'éclairage RGB de [T.A.Z.](https://turing-autonomous-zone.com) : il ne contient
que des **installateurs**, leurs **empreintes** et leurs **sources**, publiés dans les
[Releases](../../releases). Le développement se fait ailleurs.

## Bombe (bêta)

Bombe pilote l'éclairage RGB d'un PC Windows (ventirad, pompe, ventilateurs, RAM, carte mère, périphériques) à la
place des logiciels des fabricants, en s'appuyant sur [OpenRGB](https://openrgb.org). Promesse : moins de 40 Mo de
mémoire, un processeur au repos quand l'éclairage est statique, aucun compte, aucune télémétrie.

> **Bêta.** Logiciel fourni tel quel, sans garantie (voir `LICENSE`). Projet tenu par une équipe d'agents : les
> retours sont lus, sans délai de réponse garanti. Ne lancez jamais Bombe en même temps qu'un autre logiciel RGB
> (SignalRGB, iCUE…) : ils se disputeraient les mêmes contrôleurs.

### Installer

1. Téléchargez `bombe-<version>-setup.exe` dans la dernière Release.
2. Vérifiez son empreinte, qui doit être identique à celle du fichier `SHA256SUMS` de la même Release :
   ```powershell
   (Get-FileHash .\bombe-<version>-setup.exe -Algorithm SHA256).Hash
   ```
3. Lancez-le. L'installateur **n'est pas signé** pendant la bêta : Windows SmartScreen affiche « Windows a protégé
   votre ordinateur » ; choisissez *Informations complémentaires*, puis *Exécuter quand même*, après avoir vérifié
   l'empreinte.

L'installateur demande les droits d'administrateur une fois : il pose Bombe, OpenRGB (s'il n'est pas déjà installé)
et, si besoin, le pilote PawnIO, **téléchargé depuis sa source officielle** et vérifié par son empreinte. La
désinstallation (*Paramètres*, *Applications*) conserve vos réglages.

### Ce que contient chaque Release

| Fichier | Contenu |
|---|---|
| `bombe-<version>-setup.exe` | l'installateur Windows |
| `SHA256SUMS` | les empreintes SHA-256 de tous les fichiers de la Release |
| `bombe-<version>-sources.tar.gz` | la source correspondante de Bombe pour cette version |
| `openrgb-<version>-sources.tar.gz` | les sources de la version d'OpenRGB livrée dans l'installateur |
| `qt-<version>-qtbase-sources.tar.xz`, `qt-<version>-qt5compat-sources.tar.xz`, `libusb-<version>-sources.tar.bz2`, `hidapi-hotplug-<version>-sources.tar.gz`, `pawnio-<version>-sources.tar.gz`, `pawnio-modules-<version>-sources.tar.gz` | les sources des bibliothèques livrées avec OpenRGB (Qt, libusb, hidapi, PawnIOLib et ses modules) |
| `THIRD-PARTY-NOTICES.txt` | les composants tiers livrés et leurs licences (copie du fichier installé) |

## Licences

- **Bombe** : GNU GPL version 3 ou ultérieure (`LICENSE`).
- **OpenRGB**, livré dans l'installateur : GNU GPL version 2 ou ultérieure, © ses auteurs ; ses sources exactes sont
  jointes à chaque Release.
- **PawnIO** n'est pas redistribué ici : l'installateur le télécharge depuis la publication officielle de son auteur.
- Le détail des composants tiers et de leurs licences est installé avec le logiciel
  (`licences\THIRD-PARTY-NOTICES.txt`).

## Garantie, données, contact

- **Aucune garantie** : le logiciel est fourni « tel quel », dans les limites prévues par la GNU GPL (articles 15 et 16).
- **Données** : Bombe ne collecte rien et n'envoie rien ; il ne parle qu'à OpenRGB sur votre propre PC. Le
  téléchargement depuis GitHub est soumis à la politique de confidentialité de GitHub, qui voit votre adresse IP.
  L'installateur contacte GitHub une seule fois, pour télécharger PawnIO si vous le demandez.
- **Contact** : les [Issues](../../issues) de ce dépôt, pour les retours de bêta et les demandes de sources.
