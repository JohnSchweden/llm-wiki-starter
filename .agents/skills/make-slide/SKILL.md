---
name: make-slide
description: Build one PowerPoint slide (.pptx) from an agreed plan, with no installs. Use it for "build the slide", "make the PowerPoint", "turn the plan into a slide".
---

# Make a slide

A `.pptx` file is a zip of XML files. `template/` holds a tested one-slide deck with placeholders. Fill in the text, zip the folder, open the file. Do not install anything. Do not use Python or python-pptx.

## Before you build

- There must be an agreed plan. No plan yet: write one, save it to `outputs/YYYY-MM-DD-<slug>-plan.md`, and wait for a yes.
- Read `wiki/profile/design-guide.md` for colours.

## Build

1. Copy the template to a work folder next to the output:
   - Mac: `cp -R .agents/skills/make-slide/template outputs/<slug>-pptx`
   - Windows (PowerShell): `Copy-Item -Recurse .agents/skills/make-slide/template outputs/<slug>-pptx`
2. In `outputs/<slug>-pptx/ppt/slides/slide1.xml` replace each placeholder with text from the plan:
   - `{{HEADLINE}}`: the one message, short
   - `{{NUMBER}}`: the big number, 1 to 3 characters
   - `{{CAPTION}}`: what the number means, under 8 words
   - `{{BULLET_1}}`, `{{BULLET_2}}`, `{{BULLET_3}}`: one line each. Fewer bullets: delete the whole `<a:p>…</a:p>` that holds the unused one.
   - `{{ASK}}`: the decision you want
3. In `outputs/<slug>-pptx/ppt/notesSlides/notesSlide1.xml` replace `{{NOTES}}` with the speaker notes. For more paragraphs, repeat `<a:p><a:r><a:t>…</a:t></a:r></a:p>`.
4. Escape XML in every text you insert: `&` becomes `&amp;`, `<` becomes `&lt;`, `>` becomes `&gt;`. Text that starts or ends with a space: write `<a:t xml:space="preserve">` instead of `<a:t>`.
5. Colours: navy `0B2545` for text and orange `F28C28` for the number are in `srgbClr val="…"`. Change them only to match the design guide. Keep the font `Arial`: other fonts may be missing on the machine that opens the file.
6. Check no `{{` is left in either file.
7. Zip from inside the work folder. List `[Content_Types].xml` first.
   - Mac: `cd outputs/<slug>-pptx && zip -X -D -r ../<YYYY-MM-DD>-<slug>.pptx '[Content_Types].xml' _rels docProps ppt -x '*.DS_Store'`
   - Windows (PowerShell): `Add-Type -AssemblyName System.IO.Compression.FileSystem; [IO.Compression.ZipFile]::CreateFromDirectory("$PWD\outputs\<slug>-pptx", "$PWD\outputs\<YYYY-MM-DD>-<slug>.pptx")`
8. Delete the work folder. Open the file: Mac `open outputs/<file>.pptx`, Windows `start outputs\<file>.pptx`.

Do not edit any other file in the template. Keynote rejects the deck if the notes or master parts change.
