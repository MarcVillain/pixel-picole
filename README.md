# Pixel Picole

Générateur de planches vierges pour trackers annuels à stickers, d'après les
planches dessinées à la main dans [`reference/`](reference).

Tout tient dans **un seul fichier**, [`index.html`](index.html) : pas de build,
pas de dépendance, pas de réseau. On l'ouvre dans un navigateur, on règle, on
imprime.

| Original | Généré |
| --- | --- |
| ![Classic](reference/classic.jpg) | 12 mois × 31 jours |
| ![4 Saisons](reference/4-saisons.jpg) | 4 blocs de semaines ISO |

## Utilisation

Ouvrir `index.html`. On choisit :

- **l'édition** — Classic, 4 Saisons, Mensuel ou Spirale ;
- **la date de début** — la planche couvre un an à partir de là ;
- **le format papier** — A6 → A1, Letter/Legal/Tabloid, ou sur mesure ;
- **le sticker** — diamètre (8 mm par défaut) et espace minimum (1 mm).

Puis **Imprimer / PDF** (à l'échelle 100 %, surtout pas « ajuster à la page »)
ou **SVG** pour un fichier vectoriel aux cotes exactes.

Les réglages sont mémorisés dans le navigateur.

### Quand ça ne rentre pas

Un sticker de 8 mm espacé de 1 mm impose un entraxe de 9 mm. Une grille Classic
demande donc `31 × 9 ≈ 280 mm` de large : elle ne tient pas sur un A4. Le
générateur le dit et propose en un clic la taille de sticker qui passe, ou le
format juste au-dessus. À l'inverse, quand il reste de la place il propose
d'agrandir les stickers pour remplir la feuille.

Les repères imprimés sont au choix un point discret, un cercle à la taille
exacte du sticker (gabarit), une croix, ou un disque plein à colorier au crayon.

### Ce que couvre exactement une planche

- **Classic** et **Spirale** : un an pile à partir de la date choisie.
- **Mensuel** : 12 mois entiers, calés sur le 1er du mois de départ.
- **4 Saisons** : la planche est indexée par numéro de semaine ISO, donc elle
  contient `7 × (nombre de numéros de semaine distincts)` cases, soit 364 ou
  371. Quand il y a la place, on coupe à un an pile et les cases en trop
  restent vides — ce sont elles qui dessinent le décrochage du cadre, comme sur
  la planche d'origine. La semaine de « couture » sert deux fois : le début de
  l'année à droite, la fin à gauche.

La période réellement couverte est toujours affichée sous la date de début.

## Ajouter une édition

Une édition est un objet passé à `registerDesign()`, dans la section 4 du
script. Elle dessine dans un `Canvas` abstrait en millimètres, avec une origine
libre : le moteur recadre, ajoute le titre et la légende, centre le tout sur la
feuille et vérifie que ça rentre.

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
    // x.R                        rayon du sticker
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

Primitives disponibles sur `c` : `dot`, `txt`, `line`, `rect`, `poly`, `disc`.
Les couleurs sont des noms logiques (`ink`, `mute`, `faint`, ou `c0`…`c3` pour
les entrées de légende). Deux aides maison : `steppedOutline(rows)` pour les
contours en escalier, et `isoWeek(date)` pour les semaines ISO.

L'édition apparaît automatiquement dans les vignettes, avec ses options et sa
description.
