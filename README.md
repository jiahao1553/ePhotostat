# ID Card Document Maker

> A single-file web app that scans, crops, and packages your ID card (front + back) into a watermarked A4 PDF — entirely in your browser, zero uploads.

---

## Why I built this

Living in Singapore and dealing with Malaysia paperwork (and vice versa), I kept running into the same tedious ask: *"Please provide a copy of your IC / NRIC / passport, front and back."*

The usual flow — photograph both sides, crop in Photos, open Word or some online tool, arrange them on a page, export as PDF — takes way too long for something I do constantly.

I also didn't love the idea of feeding my identity documents into a random online service. These are sensitive. I wanted something that runs entirely on my own device, touches no server, and is just… done.

So I vibe-coded this on a weekend. It turned out to be genuinely fun to build, and now I use it all the time. Sharing it here in case it saves anyone else the same friction.

---

## What it does

- **Camera scan** — point your phone camera at the card; it auto-detects focus, checks that a card fills the frame, and captures automatically
- **Auto-crop** — detects the card edges and trims the background
- **Perspective correction** — drag 4 corner handles to straighten a skewed photo
- **Rotation** — fine-tune tilt with a slider
- **Background removal** — flood-fill removes the desk/table behind the card
- **Gallery upload** — pick existing photos from your library instead
- **Watermark** — stamp custom text (e.g. *FOR BANK USE ONLY*) at an angle across the A4 page so the document can't be reused for other purposes
- **A4 PDF export** — both sides laid out at the actual ISO 7810 card size (85.6 × 54 mm), ready to attach to any form
- **Black & white mode** — for submissions that prefer greyscale
- **Re-edit anytime** — tap the pencil icon on any captured side to go back and adjust

---

## Privacy

**Nothing leaves your device.** There is no backend, no analytics, no CDN for your images. The only external requests are:

- Google Fonts (stylesheet, loaded once)
- jsPDF (JavaScript library, loaded once)

Your photos stay in your browser's memory and are gone the moment you close the tab.

---

## Usage

Because it's a single HTML file, there's nothing to install.

**Option A — open directly**

Download `index.html` and open it in any modern browser. That's it.

**Option B — deploy to Cloudflare Pages / Workers**

A `wrangler.jsonc` is included. Run:

```bash
npx wrangler pages deploy .
```

You get a private URL you can bookmark on your phone.

---

## Tech

- Vanilla HTML + CSS + JavaScript — no framework, no build step
- [jsPDF](https://github.com/parallax/jsPDF) for PDF generation
- Laplacian variance for focus/sharpness detection
- Bilinear perspective warp (32 × 32 affine grid) for straightening
- Edge-seeded flood fill for background removal
- Entirely vibe-coded — Claude did most of the heavy lifting while I steered

---

## Limitations

- Perspective correction is bilinear approximation, not a true homography — works well for typical hand-held shots, may show subtle warping on extreme angles
- Background removal uses corner colour sampling; very low-contrast backgrounds (white card on white table) may not separate cleanly
- PDF is generated client-side; very large images may be slow on low-end devices

---

## Contributing

Issues and PRs welcome. Keep it simple — the goal is a single self-contained file anyone can download and use without reading a manual.

---

## License

MIT
