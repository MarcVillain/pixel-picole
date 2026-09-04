<div align="center">

# PIXEL *Picole*

**Un an, une case par jour, une gommette de 8 mm.**
Générateur de planches vierges à imprimer — un seul fichier HTML, zéro dépendance.

<img src="reference/classic.jpg" width="46%" alt="Planche Classic remplie, dessinée à la main">
<img src="reference/4-saisons.jpg" width="46%" alt="Planche 4 Saisons vierge, dessinée à la main">

*Les deux planches d'origine, faites à la main. Le générateur produit les mêmes, à n'importe quelle date et n'importe quel format.*

</div>

---

## L'idée

Un tracker mural n'est pas un objectif. C'est un **carnet de bord**.

On ne se fixe pas « moins de trois verres par semaine » au 1er janvier pour se sentir
nul le 12. On colle simplement une gommette par jour, dix secondes le soir, sans
commentaire. Au bout de deux mois, on recule d'un pas et **le mur parle** : les
vendredis ressortent, les périodes chargées au boulot ressortent, ce voyage de
mars ressort. Personne n'a eu besoin de le noter — la couleur l'a fait.

C'est de là que viennent les vrais objectifs. Pas d'une résolution décidée à
l'avance dans le vide, mais d'un motif qu'on a vu apparaître tout seul et qu'on a
envie de bouger. **Observer d'abord, décider ensuite.**

Trois principes tiennent tout le projet :

- **Constater, pas juger.** Une case est une information, pas une faute. Un mois
  bien rouge est un mois bien rouge : c'est déjà une réponse, ce n'est pas une note.
- **Le vocabulaire compte.** Les pastilles s'appellent CHILL, TCHIN, PARTY — pas
  « échec » ni « rechute ». On nomme ce qui s'est passé, avec les mots qu'on
  emploierait avec un ami. C'est pour ça que tout est modifiable : ce sont *tes*
  mots qui doivent être sur *ton* mur.
- **Dix secondes par jour.** Un rituel qui demande davantage s'arrête au bout de
  trois semaines. Une gommette, c'est tenable un an.

Et ça marche dans les deux sens. Il n'y a rien de spécifiquement alcoolisé dans une
grille de 365 cases : on suit aussi bien ce qu'on veut voir reculer que ce qu'on
veut voir grandir — bouger, dormir, cuisiner, lire, appeler ses proches. Le mur ne
juge pas ce qu'on y met.

## L'outil

Tout tient dans **[`index.html`](index.html)** : un fichier, ~1 500 lignes, aucune
dépendance, aucun build, aucun réseau, aucun compte. On l'ouvre dans un
navigateur, on règle, on imprime. On peut le mettre sur une clé USB, l'envoyer en
pièce jointe, ou le garder dix ans — il marchera toujours.

Ce n'est pas une contrainte qu'on s'est imposée pour la beauté du geste : un objet
qui sert une fois par an doit survivre à ses dépendances. Rien à mettre à jour,
rien à réinstaller, rien qui casse.

## Utiliser

Ouvre `index.html` dans ton navigateur. Puis :

1. **Choisis une édition** — Classic, 4 Saisons, Mensuel ou Spirale.
2. **Pose ta date de début** — n'importe quel jour de l'année, pas seulement le 1er janvier.
3. **Choisis ton papier** — A6 → A1, Letter, Legal, Tabloid, ou sur mesure.
4. **Vérifie les pastilles** — 8 mm de diamètre et 1 mm d'air, c'est le maximum.
5. **Regarde ce que ça donnera** — l'*aperçu rempli* colorie une année plausible.
6. **Imprime à 100 %** (« taille réelle », surtout pas « ajuster à la page »), ou exporte en SVG.

Les réglages restent en mémoire dans le navigateur. Rien ne part ailleurs.

### L'aperçu rempli

Une planche vide ne dit rien de ce qu'elle donnera au mur. L'aperçu la remplit
d'une année crédible : pas un tirage à pile ou face, mais trois échelles de bruit
lissé — l'humeur du jour, la semaine, la saison — plus l'effet vendredi et
week-end. On y voit des séries, des mois calmes, des périodes chargées : de quoi
juger un jeu de couleurs avant d'acheter les gommettes. Le bouton *↻ Autre tirage*
en propose une autre.

C'est un aperçu écran : il ne s'imprime pas et n'est pas exporté.

### Les quatre éditions

| Édition | Ce qu'on y lit | Format conseillé |
| --- | --- | --- |
| **Classic** | 12 lignes de mois × 31 colonnes. L'année entière d'un coup d'œil, les séries sautent aux yeux. | A3 paysage |
| **4 Saisons** | Blocs de semaines ISO, lundi → dimanche, plus une colonne ★ pour noter la semaine. Le meilleur pour les rythmes hebdo. | A3 portrait |
| **Mensuel** | 12 mini-calendriers alignés sur les vrais jours de la semaine. Révèle l'effet week-end. | A3 portrait |
| **Spirale** | Les 365 jours en un seul ruban, sans coupure de mois. Très graphique au mur. | A3 portrait |

### La contrainte des 8 mm

Une gommette de 8 mm avec 1 mm d'air impose un **entraxe de 9 mm** entre deux
centres. C'est un **plafond**, pas un objectif : au-delà, la gommette flotte dans
sa case et la grille se délave. Les curseurs s'arrêtent donc à 8 et à 1.

En dessous, tout est permis — gommettes de 6 mm, ou remplissage au crayon de
couleur, qui marche très bien. Le bandeau sous les curseurs affiche en permanence
l'entraxe réel et rappelle où on en est par rapport au plafond.

Si tu utilises d'autres gommettes, *J'utilise d'autres gommettes* relève les deux
plafonds. C'est volontairement rangé derrière un interrupteur : la valeur par
défaut est celle qui donne une belle planche.

Conséquence directe : **c'est le papier qui s'adapte à la grille**, pas l'inverse.
Une grille Classic, c'est `31 × 9 ≈ 280 mm` de large, donc **elle ne rentre pas sur
un A4**. Le générateur le dit franchement plutôt que de rétrécir en douce, et
propose en un clic le format qui convient — le plus petit qui passe quand il reste
trop de blanc, le format au-dessus quand ça déborde.

### Le décor

Le mot principal du titre est **composé de carrés** — une police pixel 5 × 7
dessinée dans le fichier, accents compris. Aucune police à charger : le titre est
identique à l'écran, à l'impression et dans le SVG exporté.

Les carrés semés autour de la planche sont les mêmes, en 3 mm. Ils ne tombent pas
au hasard : ils se posent sur une grille invisible au pas du pixel, en petites
grappes façon tetromino, dans des zones symétriques — de part et d'autre du titre,
aux quatre coins, sur les deux flancs. D'où un semis qui paraît libre mais reste
équilibré, et qui ne mord jamais sur la grille, le titre ou la légende. Les deux
sont désactivables.

### Thèmes

Le générateur s'appelle Pixel Picole et c'est sa configuration par défaut. Mais la
grille se moque de ce qu'on y met : un sélecteur discret, en bas du panneau
Pastilles, pré-remplit le titre et les pastilles pour d'autres sujets — écrans,
séries, activité physique, sommeil, cuisine maison, intimité, humeur.

Ce ne sont que des points de départ. Le vrai réglage, c'est celui d'après : change
les noms, les couleurs, les descriptions, ajoute ou retire des pastilles. Une
planche à toi vaut mieux qu'une planche bien nommée.

## Publier sa propre version

Le générateur est un fichier statique : n'importe quel hébergeur fait l'affaire.

**GitHub Pages, en trois clics.** Le dépôt contient déjà
[`.github/workflows/pages.yml`](.github/workflows/pages.yml). Va dans
**Settings → Pages**, choisis **Source : GitHub Actions**, et pousse sur la branche
par défaut. Le site sort sur `https://<compte>.github.io/pixel-picole/`, et se
remet à jour à chaque push.

**Sans rien installer.** *Settings → Pages → Source : Deploy from a branch*,
branche `main`, dossier `/ (root)` : `index.html` est servi tel quel.

**Ailleurs.** Netlify, Vercel, Cloudflare Pages, un dossier sur un serveur, une clé
USB : glisse `index.html`, il n'y a rien à construire. C'est aussi la manière la
plus simple de partager l'outil — envoyer le fichier suffit.

## Contribuer

Les contributions sont bienvenues — surtout les nouvelles éditions et les
retouches de mise en page.

- **Une modification = une intention.** Le fichier est unique, donc les diffs
  parlent : garde-les lisibles.
- **Pas de dépendance, pas d'outil de build.** Si une idée nécessite npm, c'est
  qu'elle appartient à un autre projet.
- **Le millimètre fait foi.** Tout le moteur raisonne en mm. Une planche doit
  s'imprimer à l'échelle 1:1 ou ne pas s'imprimer.
- **Vérifie sur plusieurs dates.** Années bissextiles, semaines 53, départs en
  milieu de mois : c'est là que ça casse. Chaque jour de la période doit tomber
  dans exactement une case, sans doublon ni orphelin.
- **Le ton reste bienveillant.** Pas de vocabulaire culpabilisant dans les
  libellés, les thèmes ou l'interface.

Le code est commenté en français et découpé en sections numérotées : dates,
primitives de dessin, rendu SVG, éditions, thèmes, formats, composition, interface.

## Ajouter une édition

Une édition est un objet passé à `registerDesign()` (section 4 du script). Elle
dessine dans un `Canvas` abstrait en millimètres, avec une origine libre : le
moteur recadre, ajoute le titre, la légende et le pied de planche, sème le décor,
centre le tout et vérifie que ça rentre.

```js
registerDesign({
  id: "trimestres",              // clé unique (sert aussi à sauver les options)
  name: "Trimestres",
  cadence: "Trimestriel",        // badge de la vignette
  desc: "Une phrase : à quoi cette édition sert le mieux.",
  prefer: "landscape",           // orientation appliquée à la sélection
  icon: '<g fill="currentColor"><circle cx="10" cy="15" r="2"/></g>', // viewBox 0 0 60 30
  options: [
    { id: "grid", label: "Encadrer les blocs", type: "switch", def: true },
    { id: "cols", label: "Colonnes", type: "select", def: "2",
      choices: [["2", "2"], ["4", "4"]] }
  ],

  // Facultatif : cadrage propre à l'édition. Sans lui, un an pile.
  period(start, o) {
    return { start, end: addDays(plusOneYear(start), -1), note: null };
  },

  build(c, x) {
    // x.start / x.end / x.days   la période (Date UTC)
    // x.inPeriod(dt)             ce jour est-il dedans ?
    // x.pitch                    entraxe = diamètre + espacement
    // x.R                        rayon de la pastille
    // x.fs                       taille de police de base
    // x.mark                     style de repère courant
    // x.landscape                la feuille est-elle en paysage ?
    // x.o                        valeurs des options ci-dessus
    x.days.forEach((dt, i) => {
      c.dot((i % 20) * x.pitch, Math.floor(i / 20) * x.pitch);
    });
    c.txt(0, -x.fs, "2026", { size: x.fs, weight: 700, fill: "mute" });
  }
});
```

Primitives sur `c` : `dot`, `txt`, `line`, `rect`, `poly`, `disc`. Les couleurs
sont des noms logiques — `ink`, `mute`, `faint`, `paper`, et `c0`…`cN` pour les
pastilles. Deux aides maison : `steppedOutline(rows)` pour les contours en
escalier, et `isoWeek(date)` pour les semaines ISO. Les vignettes de saison
(`SEASON_MARKS`) montrent comment dessiner une icône en vectoriel plutôt que de
dépendre d'une police de symboles.

L'édition apparaît ensuite toute seule dans les vignettes, avec ses options et sa
description.

### Ce que couvre exactement une planche

- **Classic** et **Spirale** : un an pile à partir de la date choisie.
- **Mensuel** : 12 mois entiers, calés sur le 1er du mois de départ.
- **4 Saisons** : la planche est indexée par numéro de semaine ISO, donc elle
  contient `7 × (nombre de numéros de semaine distincts)` cases — 364 ou 371,
  jamais 365 pile. Quand il y a la place on coupe à un an et les cases en trop
  restent vides : ce sont elles qui dessinent le décrochage du cadre, exactement
  comme sur la planche d'origine. La semaine de couture sert deux fois — le début
  de l'année à droite du décrochage, la fin à gauche.

La période réellement couverte est toujours affichée sous la date de début.

---

<div align="center">

© Pixel Picole

</div>
