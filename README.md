# git digestif

<p align="center">
  <img src="images/git-digestif.png" alt="git digestif" width="200">
</p>

<h3 align="center">
  <a href="https://git-digestif.github.io/">git-digestif.github.io</a>
</h3>

The [Git mailing list](https://lore.kernel.org/git/) is where all of
Git's development happens, but keeping up with dozens of threads a day
is a tall order.  **git digestif** serves you a short, AI-generated
summary of each day's discussion so you can stay informed in a couple of
minutes instead of an hour.

Pick a date, read the highlights, move on with your day.

## What you get

**Daily, weekly, and monthly digests** covering notable threads, brief
mentions, and topics to keep an eye on.

**Instant access** in the browser, no install, no account required.
Just open [git-digestif.github.io](https://git-digestif.github.io/) and
scroll to the date you are interested in.

**Deep links** you can bookmark or share. Every digest has its own URL
(e.g. `#2026/03/11/digest.human`).

**Prev / Next buttons** to step through consecutive days without
having to fiddle with the date picker.

**Works on phones and tablets** with a responsive layout that adapts to
narrow screens.

## Date picker

Three drum rollers for year, month, and day let you jump to any
published digest.  They respond to mouse wheel, touch swipe, and
click-drag.

## GitHub API rate limits

The viewer talks to the GitHub REST API, which allows 60 unauthenticated
requests per hour per IP address.  If you (or others on your network)
hit that limit, the viewer will ask for a
[fine-grained personal access token](https://github.com/settings/personal-access-tokens/new).
No special permissions are needed for public repositories.  An opt-in
checkbox lets you store the token in your browser so you do not have to
re-enter it.

## Technical details

The entire application is a single `index.html` with inline CSS and
JavaScript.  There is no build step and no framework.

Digests are stored as Markdown files in
[git-digestif/lore-git-md](https://github.com/git-digestif/lore-git-md).
The viewer discovers available dates through the GitHub Trees API and
fetches individual files as raw blobs.  Tree responses are cached in
memory, except for the latest month which is always re-fetched so new
digests appear immediately.  Markdown is rendered client-side with
[marked](https://github.com/markedjs/marked).

Because the source Markdown formatting varies across digests (some use
`## Heading`, others use bare `**bold**` lines), a post-render pass
walks the DOM and promotes known section names to proper headings so
every digest looks uniform.

## License

MIT
