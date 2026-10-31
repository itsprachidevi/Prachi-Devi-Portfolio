# Prachi-Devi-Portfolio

A single-page personal portfolio for a Business & Product Analyst, inspired by [naledi.co.uk](https://naledi.co.uk/). It is one HTML file with no build step and no dependencies, apart from Google Fonts. It supports light and dark mode and works on phones.

## File structure

```
/
├── index.html        ← the whole site (rename portfolio.html to this)
├── README.md         ← this file
├── Prachi.jpeg       ← your photo (optional, add it yourself)
└── Prachi_Devi_Resume.pdf   ← your resume (optional, add it yourself)
```

Everything you edit lives in one place: the `C` config object at the top of the `<script>` block in `index.html`, under the comment `EDIT YOUR CONTENT HERE`. The code below the line `RENDERING (no need to edit)` builds the page from that config.

## Sections

Hero, Define/Build/Measure pillars, About (photo and stats), Selected work, Experience & education, Skills & certifications, Kind words (testimonials), Writing, Contact.

## What to edit

| Config field | What it controls |
|---|---|
| `name`, `headline`, `tagline` | Hero text and browser tab title |
| `email`, `linkedin`, `github` | Contact form target and footer links |
| `resume` | Resume button. Hidden while empty, for example `"Prachi_Devi_Resume.pdf"` |
| `photo` | About photo, for example `"Prachi.jpeg"`. A dashed placeholder shows while empty |
| `pillars` | The three intro blocks under the hero |
| `about` | About paragraphs (a list of strings) |
| `stats` | The four headline numbers, as `["value", "label"]` pairs |
| `work` | Project cards: `[title, tag, description, result, optionalLink]` |
| `jobs` | Experience and education timeline entries |
| `skills` | Skill groups. Separate chips with `\|` |
| `testimonials` | Quotes, see below |
| `posts` | Writing cards, see below |

### Testimonials

```js
testimonials:[
  {text:"…", who:"Name", role:"Title, Company", date:"Sep 2026"},
  {text:"…", who:"Name", role:"Title, Company", date:"Mar 2026"}
],
```

- Square brackets wrap the whole list, curly braces wrap each person, and commas go between people.
- `date` is optional.
- List newest first. The page shows them in the order you write them.
- Avoid straight `"` quotes inside the text. Use `’` and `“ ”` instead.
- Leave the list as `testimonials:[]` to show the placeholder.
- Get the sender's permission, and remove anything confidential before publishing.

### Writing

```js
posts:[
  {title:"…", blurb:"…", url:"https://…"}
]
```

### Case-study links

Add a fifth item to any `work` entry to show a "Case study →" link on that card:

```js
["NERVE","Airtel · AI risk engine","Description…","Result…","https://link-to-case-study"]
```

## Rendering code to match the testimonials list

The "Kind words" section in the rendering code must loop over `C.testimonials` and show the date:

```js
<section><div class="w"><h2>Kind words</h2>${C.testimonials.length?C.testimonials.map(t=>`<blockquote>“${t.text}”</blockquote><p style="color:var(--mut);margin:8px 0 32px">${t.who}, ${t.role}${t.date?` · ${t.date}`:""}</p>`).join(""):ph("Add testimonials (set <code>testimonials</code> in the config)")}</div></section>
```

## Run locally

Open `index.html` in any browser. There is nothing to install.

## Deploy to GitHub Pages

1. Put `index.html` (and your photo and resume) in your repository.
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, then select your main branch and the `/ (root)` folder.
4. Save. Your site goes live at `https://<username>.github.io/<repo>/` after a minute or two.

## Contact form

A static site can't send email itself, so the Send button opens the visitor's email app with the message pre-filled, addressed to the `email` in the config. For a form that sends directly, use a service such as Formspree or Web3Forms and point the form at it.

## Before you publish: checklist

- [ ] Confirm `email` and `linkedin` (your old site and resume used different ones)
- [ ] Confirm the ARC figures (approval time, FTE saved), the CMS Approvals projection and the number of Ace Awards, so they match your resume and LinkedIn
- [ ] Add `photo` and `resume`
- [ ] Add testimonials, with sender permission and Airtel confidentiality checked
- [ ] Add `posts`, or ignore the placeholder if you aren't writing yet
- [ ] Check which project names, tools and numbers you can share publicly
- [ ] Open the site on your phone and in dark mode
- [ ] Use the same numbers and wording as your resume and LinkedIn

## Fonts and colours

- Fonts: Fraunces for headings and Inter for body text, loaded from Google Fonts.
- Colours: edit the variables at the top of the `<style>` block (`--bg`, `--fg`, `--acc` and so on). There is one set for light mode and one for dark mode.
