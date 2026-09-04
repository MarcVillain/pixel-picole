<div align="center">

<img src="assets/logo.svg" width="88" alt="">

# PIXEL *Picole*

**One year, one cell per day, one sticker.**

A generator for printable tracker sheets. Single HTML file, no dependencies.

<img src="assets/classic.png" width="88%" alt="Classic sheet, filled preview">

<img src="assets/4-saisons.png" width="43%" alt="4 Saisons sheet, filled preview">
<img src="assets/spirale.png" width="43%" alt="Spirale sheet, filled preview">

*The sheets print empty. Shown here with the filled preview.*

</div>

---

## The idea

A wall tracker is a logbook, not a goal.

You stick one sticker a day and write nothing down. After a couple of months the
wall starts talking. Fridays stand out. Heavy weeks at work stand out. That trip
in March stands out. Nobody had to record any of it.

Real goals come from there. From a pattern you watched appear and now want to
move.

Three rules hold the project together.

- A cell is information, not a verdict.
- The words matter. The stickers are called CHILL, TCHIN, PARTY. You name what
  happened, the way you would to a friend. Everything is editable so the words on
  your wall are yours.
- Ten seconds a day. A ritual that asks for more stops within weeks.

It works both ways. A grid of days has nothing to do with alcohol. Track what you
want to see shrink, or what you want to see grow.

## The tool

Everything lives in `index.html`. No dependencies, no build, no network, no
account. Open it in a browser, set it up, print. Nothing to install and nothing
to update.

The interface is in French. Every label on the sheet is editable, so translating
your own sheet takes a minute.

## Using it

<img src="assets/app.png" width="100%" alt="The generator interface">

Pick an edition, a start date, a paper size and a sticker shape. The filled
preview draws a plausible year so you can judge the colours before buying
anything. Print at full size, or export SVG.

Settings stay in your browser.

### Editions

| Edition | What you read on it |
| --- | --- |
| **Classic** | The whole year in one grid. Streaks jump out. |
| **4 Saisons** | Weeks grouped by season, with a column to rate each week. |
| **Mensuel** | Twelve small calendars on real weekdays. Shows the weekend effect. |
| **Spirale** | The year as one continuous ribbon. |

### Stickers

The grid is built around stationery stickers, so the cell size has a ceiling
rather than a target. Below it you are free. Above it a sticker floats in its
cell and the grid goes slack. One switch lifts the limits if you use something
else.

Since the cell cannot grow, the paper adapts to the grid. Some editions will not
fit on smaller sheets. The generator says so and offers a size that works.

Round, square and triangle stickers are all supported, and the printed guide can
be a dot, an outline, a filled shape, a cross, or the day number.

### Themes

Pixel Picole is the default. A small selector fills in the title and stickers for
other subjects: screens, series, exercise, sleep, cooking, intimacy, mood. They
are starting points. Change the names, the colours and the notes, add or remove
stickers.

## Publishing

The repo carries a Pages workflow. Enable Pages with GitHub Actions as the
source, then push. Any static host works, and so does sending someone the file.

## Contributing

New editions and layout fixes are the most useful contributions.

- No dependencies and no build step. An idea that needs npm belongs in another
  project.
- The engine works in millimetres. A sheet prints at true scale or it does not
  print.
- Test across start dates. Leap years and mid-month starts are where it breaks.
  Every day of the period must land in exactly one cell.
- Keep the wording kind. No shaming language in labels, themes or the interface.

Code and comments are in French, in numbered sections.

## Adding an edition

An edition is an object passed to `registerDesign()`. It draws into an abstract
canvas in millimetres, from any origin. The engine crops, adds the title, legend
and footer, scatters the decoration, centres it and checks that it fits.

```js
registerDesign({
  id: "trimestres",
  name: "Trimestres",
  cadence: "Trimestriel",
  desc: "Une phrase sur ce que cette édition montre le mieux.",
  prefer: "landscape",
  icon: '<g fill="currentColor">…</g>',
  options: [
    { id: "grid", label: "Encadrer les blocs", type: "switch", def: true }
  ],

  // Optional. Only when the edition frames its own span.
  period(start, o) { return { start, end: addDays(plusOneYear(start), -1) }; },

  build(c, x) {
    x.days.forEach((dt, i) => c.dot(col(i), row(i), { day: i }));
  }
});
```

The context hands you the period, the cell pitch, the sticker radius, a base font
size and your option values. Primitives are `dot`, `txt`, `line`, `rect`, `poly`
and `disc`, and colours are logical names. Tag each cell with its day index and
the filled preview works for free.

The four existing editions cover most of what you would need to copy. A new one
shows up in the picker on its own.

## Licence

Apache 2.0. See [LICENSE](LICENSE) and [NOTICE](NOTICE).

Apache rather than MIT for two reasons. It requires copyright notices to be kept
in copies and derivatives, which matches the footer printed on every sheet. And
it grants no rights over the name, so a fork ships under its own.

---

<div align="center">

© 2026 Pixel Picole

</div>
