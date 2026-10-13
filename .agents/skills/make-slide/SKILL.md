---
name: make-slide
description: Plan and build a PowerPoint deck (.pptx), any number of slides, each one laid out from the user's design guide, with no installs. Use it for "plan a deck", "build the slides", "make the PowerPoint", "turn the plan into a deck".
---

# Make slides

A `.pptx` file is a zip of XML files. `shell/` holds an empty deck: the package parts PowerPoint and Keynote need, no slides and no design. You design every slide yourself from the plan and the design guide, write it as XML, zip the folder and look at the result. Do not install anything. Do not use Python, Node or python-pptx: a fresh laptop may not have them. Every command below ships with macOS or Windows.

## Before you build

- Read `wiki/profile/` (profile, business profile, voice guide, design guide) and the wiki articles the deck draws on. Every slide follows the design guide. No design guide: say so and offer `create-design-guide`.
- Plan first, build second. In plan mode, write the plan below as your plan and build once the user approves it. Not in plan mode and no agreed plan yet: show the plan in the chat and wait for a yes before you write any file. The user does not need to ask for a framework or a slide count: the plan always has both.
- Once the plan is agreed, save it to `outputs/YYYY-MM-DD-<slug>-plan.md` with the changes the user asked for, then build.

## The plan

1. **Audience and the one point.** Who sees the deck, what they should do or think afterwards, in one sentence. Take the audience from the request, the profile or the business profile. Unclear: ask, one question.
2. **Framework.** Pick the one that fits the audience and the goal. If the user named one, use theirs.

   | Goal | Framework | Slides carry |
   |---|---|---|
   | Someone has to decide | SCQA (Minto), answer first | answer and ask, situation, complication, why not the obvious fix, ask |
   | Sell a fix to people who do not feel the pain yet | Problem, solution, benefit | the pain, what it costs, the fix, what changes, the ask |
   | Show a change or a transformation | Before, after, bridge | today, the better state, how we get there |
   | Report results or a project status | What, so what, now what | the facts, what they mean, the next step |
   | Win support for one claim | One claim, three reasons | the claim, one slide per reason with its evidence, the claim again |
   | Inspire or open a talk | Story: hero, obstacle, turn, lesson | one slide per beat, the lesson last |

   Write why it fits in two lines: the audience, the goal, and what in the voice guide it matches.
3. **Slide count.** As many slides as the framework needs for this content, one idea each, usually three to seven. If the user gave a number, use it and merge or split steps to fit.
4. **Per slide:** its step in the framework, the headline, the layout sketched in text (what sits where), where the accent goes, the speaker notes, and the wiki article each fact comes from.
5. **Layouts.** Choose each for its content: a big number, cards in a row, two columns, a quote, a before and after, a crossed-out option. Do not repeat one layout across the deck unless the design guide asks for it.
6. **Gaps.** List what the wiki does not say but the deck would need. Do not fill it from memory.

## Units

The slide is 16:9, 12192000 by 6858000 EMU.

- Design guide in px on a 1920 by 1080 canvas: position and size in EMU = px × 6350. Font size `sz` = px × 50 (32 px is `sz="1600"`).
- Design guide in pt: EMU = pt × 12700. `sz` = pt × 100.

## Make the text fit

PowerPoint does not shrink text for you. Size every text box before you write it:

- Width of one line ≈ characters × font size × 0.6 (Arial; about 0.55 for a serif display font, 0.7 for all caps or bold).
- Height ≈ lines × font size × 1.2.
- Make the box at least that big, plus 10 percent. If it does not fit inside the margins, shorten the text or lower the size.
- Big numbers and one-line headlines get `wrap="none"`, so they never break onto a second line.

## Fonts

Use the fonts the design guide names. Check they are installed: Mac `ls /Library/Fonts ~/Library/Fonts /System/Library/Fonts | grep -i <name>`, Windows `Get-ChildItem C:\Windows\Fonts, "$env:LOCALAPPDATA\Microsoft\Windows\Fonts" -Name | Select-String <name>`. A missing font: use the closest installed one and say which in the report.

## Build

1. Copy the shell to a work folder next to the output:
   - Mac: `cp -R .agents/skills/make-slide/shell outputs/<slug>-pptx`
   - Windows (PowerShell): `Copy-Item -Recurse .agents/skills/make-slide/shell outputs/<slug>-pptx`
2. For each slide N (1, 2, 3 …) write four files and register them in three. The XML for each part and for every shape is in `references/shapes.md`.
   - `ppt/slides/slideN.xml`: the slide.
   - `ppt/slides/_rels/slideN.xml.rels`: links the layout, the notes and any picture.
   - `ppt/notesSlides/notesSlideN.xml`: the speaker notes.
   - `ppt/notesSlides/_rels/notesSlideN.xml.rels`: links the notes back to the slide.
   - In `[Content_Types].xml` add one `Override` for the slide and one for the notes.
   - In `ppt/presentation.xml` add `<p:sldId id="<255+N>" r:id="rId<100+N>"/>` inside `<p:sldIdLst>`, in slide order.
   - In `ppt/_rels/presentation.xml.rels` add the relationship `rId<100+N>` to `slides/slideN.xml`.
3. Escape XML in every text you insert: `&` becomes `&amp;`, `<` becomes `&lt;`, `>` becomes `&gt;`. Text that starts or ends with a space: write `<a:t xml:space="preserve">` instead of `<a:t>`.
4. Give every shape on a slide its own `id`, starting at 2.
5. Check every XML file you wrote or changed is well formed:
   - Mac: `xmllint --noout <file>` (no output means it is fine).
   - Windows (PowerShell): `[xml](Get-Content -Raw <file>) > $null` (no error means it is fine).
6. Zip from inside the work folder. List `[Content_Types].xml` first.
   - Mac: `cd outputs/<slug>-pptx && zip -X -D -r ../<YYYY-MM-DD>-<slug>.pptx '[Content_Types].xml' _rels docProps ppt -x '*.DS_Store'`
   - Windows (PowerShell): `Add-Type -AssemblyName System.IO.Compression.FileSystem; [IO.Compression.ZipFile]::CreateFromDirectory("$PWD\outputs\<slug>-pptx", "$PWD\outputs\<YYYY-MM-DD>-<slug>.pptx")`

Do not edit the master, the layout, the themes or the notes master in the shell. Keynote rejects the deck if they change.

## Look at every slide

Render the deck to pictures and look at each one before you report. XML that is valid can still show a cut number or overlapping text.

- Mac with Keynote: `osascript -e 'tell application "Keynote"' -e 'set d to open POSIX file "<absolute path to the .pptx>"' -e 'export d to POSIX file "<absolute path>/outputs/<slug>-check" as slide images with properties {image format:PNG}' -e 'close d saving no' -e 'end tell'`. The first time, macOS asks to let the app control Keynote: allow it.
- Windows with PowerPoint (PowerShell): `$pp = New-Object -ComObject PowerPoint.Application; $d = $pp.Presentations.Open("$PWD\outputs\<file>.pptx", $true, $false, $false); $d.SaveAs("$PWD\outputs\<slug>-check", 18); $d.Close(); $pp.Quit()`
- Neither app: Mac `qlmanage -t -s 1600 -o outputs/<slug>-check outputs/<file>.pptx` shows slide 1 only. Say that the other slides were not looked at.

On each picture check: no text cut off or wrapped where it should not, nothing overlaps, everything inside the margins, the accent only where the plan puts it, text readable against the background. Fix the XML, zip again, render again.

## Finish

1. Delete the work folder and the check folder: Mac `trash <folder>` (macOS 15 and later) or `mv <folder> ~/.Trash/`, Windows `Remove-Item -Recurse <folder>`. They are yours, so no need to ask. Leave only the `.pptx` and the plan in `outputs/`, no build scripts.
2. Open the file: Mac `open outputs/<file>.pptx`, Windows `start outputs\<file>.pptx`.
3. Report: one line per slide (headline, layout), where the deck differs from the plan, any font you swapped, and which slides you looked at.
