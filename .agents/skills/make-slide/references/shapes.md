# Slide parts and shapes

Copy these and fill in the values in angle brackets. Colors are hex without `#`. Positions and sizes are EMU, font sizes are `sz` (see Units in `SKILL.md`).

## Slide: `ppt/slides/slideN.xml`

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<p:sld xmlns:a="http://schemas.openxmlformats.org/drawingml/2006/main" xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships" xmlns:p="http://schemas.openxmlformats.org/presentationml/2006/main"><p:cSld><p:bg><p:bgPr><a:solidFill><a:srgbClr val="<background>"/></a:solidFill><a:effectLst/></p:bgPr></p:bg><p:spTree><p:nvGrpSpPr><p:cNvPr id="1" name=""/><p:cNvGrpSpPr/><p:nvPr/></p:nvGrpSpPr><p:grpSpPr/>
<shapes go here>
</p:spTree></p:cSld><p:clrMapOvr><a:masterClrMapping/></p:clrMapOvr></p:sld>
```

## Slide links: `ppt/slides/_rels/slideN.xml.rels`

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Relationships xmlns="http://schemas.openxmlformats.org/package/2006/relationships"><Relationship Id="rId1" Type="http://schemas.openxmlformats.org/officeDocument/2006/relationships/slideLayout" Target="../slideLayouts/slideLayout1.xml"/><Relationship Id="rId2" Type="http://schemas.openxmlformats.org/officeDocument/2006/relationships/notesSlide" Target="../notesSlides/notesSlideN.xml"/></Relationships>
```

## Notes: `ppt/notesSlides/notesSlideN.xml`

One `<a:p>` per paragraph.

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<p:notes xmlns:a="http://schemas.openxmlformats.org/drawingml/2006/main" xmlns:p="http://schemas.openxmlformats.org/presentationml/2006/main" xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"><p:cSld><p:spTree><p:nvGrpSpPr><p:cNvPr id="1" name=""/><p:cNvGrpSpPr/><p:nvPr/></p:nvGrpSpPr><p:grpSpPr/><p:sp><p:nvSpPr><p:cNvPr id="2" name="Notes"/><p:cNvSpPr><a:spLocks noGrp="1"/></p:cNvSpPr><p:nvPr><p:ph type="body" sz="quarter" idx="3"/></p:nvPr></p:nvSpPr><p:spPr/><p:txBody><a:bodyPr/><a:lstStyle/><a:p><a:r><a:t><notes paragraph></a:t></a:r></a:p></p:txBody></p:sp></p:spTree></p:cSld><p:clrMapOvr><a:masterClrMapping/></p:clrMapOvr></p:notes>
```

## Notes links: `ppt/notesSlides/_rels/notesSlideN.xml.rels`

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Relationships xmlns="http://schemas.openxmlformats.org/package/2006/relationships"><Relationship Id="rId1" Type="http://schemas.openxmlformats.org/officeDocument/2006/relationships/notesMaster" Target="../notesMasters/notesMaster1.xml"/><Relationship Id="rId2" Type="http://schemas.openxmlformats.org/officeDocument/2006/relationships/slide" Target="../slides/slideN.xml"/></Relationships>
```

## Register: `[Content_Types].xml`, before `</Types>`

```xml
<Override PartName="/ppt/slides/slideN.xml" ContentType="application/vnd.openxmlformats-officedocument.presentationml.slide+xml"/><Override PartName="/ppt/notesSlides/notesSlideN.xml" ContentType="application/vnd.openxmlformats-officedocument.presentationml.notesSlide+xml"/>
```

## Register: `ppt/_rels/presentation.xml.rels`, before `</Relationships>`

```xml
<Relationship Id="rId<100+N>" Type="http://schemas.openxmlformats.org/officeDocument/2006/relationships/slide" Target="slides/slideN.xml"/>
```

## Text box

Headline, number, body, caption, footer. Several runs in one paragraph give mixed colors in one line. More lines: more `<a:p>`. Add `algn="ctr"` or `algn="r"` to `<a:pPr>` to center or right-align. Bold: `b="1"`. Struck through: `strike="sngStrike"`. Use `wrap="none"` instead of `wrap="square"` for anything that must stay on one line.

```xml
<p:sp><p:nvSpPr><p:cNvPr id="<id>" name="<name>"/><p:cNvSpPr txBox="1"/><p:nvPr/></p:nvSpPr><p:spPr><a:xfrm><a:off x="<x>" y="<y>"/><a:ext cx="<width>" cy="<height>"/></a:xfrm><a:prstGeom prst="rect"><a:avLst/></a:prstGeom><a:noFill/></p:spPr><p:txBody><a:bodyPr wrap="square" lIns="0" tIns="0" rIns="0" bIns="0" anchor="t"/><a:lstStyle/><a:p><a:pPr algn="l"/><a:r><a:rPr lang="en-US" sz="<size>" b="0"><a:solidFill><a:srgbClr val="<color>"/></a:solidFill><a:latin typeface="<font>"/></a:rPr><a:t><text></a:t></a:r></a:p></p:txBody></p:sp>
```

Bullets: put `<a:buChar char="•"/>` in `<a:pPr marL="342900" indent="-342900">` of each paragraph.

## Card: filled shape with text

`prst="rect"` for square corners, `roundRect` for rounded (the `adj` value sets the radius, 0 to 50000). Outline only: replace the `solidFill` in `spPr` with `<a:noFill/>` and set `<a:ln w="19050"><a:solidFill><a:srgbClr val="<color>"/></a:solidFill></a:ln>`. Other shapes: `ellipse`, `rightArrow`, `chevron`.

```xml
<p:sp><p:nvSpPr><p:cNvPr id="<id>" name="<name>"/><p:cNvSpPr/><p:nvPr/></p:nvSpPr><p:spPr><a:xfrm><a:off x="<x>" y="<y>"/><a:ext cx="<width>" cy="<height>"/></a:xfrm><a:prstGeom prst="roundRect"><a:avLst><a:gd name="adj" fmla="val 15000"/></a:avLst></a:prstGeom><a:solidFill><a:srgbClr val="<fill>"/></a:solidFill><a:ln><a:noFill/></a:ln></p:spPr><p:txBody><a:bodyPr wrap="square" lIns="91440" tIns="45720" rIns="91440" bIns="45720" anchor="ctr"/><a:lstStyle/><a:p><a:pPr algn="ctr"/><a:r><a:rPr lang="en-US" sz="<size>"><a:solidFill><a:srgbClr val="<text color>"/></a:solidFill><a:latin typeface="<font>"/></a:rPr><a:t><text></a:t></a:r></a:p></p:txBody></p:sp>
```

## Line

Horizontal: `cy="0"`. Vertical: `cx="0"`. Width `w` in EMU (12700 is 1 pt).

```xml
<p:cxnSp><p:nvCxnSpPr><p:cNvPr id="<id>" name="<name>"/><p:cNvCxnSpPr/><p:nvPr/></p:nvCxnSpPr><p:spPr><a:xfrm><a:off x="<x>" y="<y>"/><a:ext cx="<length>" cy="0"/></a:xfrm><a:prstGeom prst="line"><a:avLst/></a:prstGeom><a:ln w="12700"><a:solidFill><a:srgbClr val="<color>"/></a:solidFill></a:ln></p:spPr></p:cxnSp>
```

## Picture

For a logo or a photo the design guide or the plan names.

1. Copy the file to `ppt/media/<name>.png` (or `.jpg`) in the work folder.
2. In `[Content_Types].xml` add `<Default Extension="png" ContentType="image/png"/>` (or `Extension="jpg" ContentType="image/jpeg"`) once, after the other `Default` lines.
3. In the slide's `.rels` add `<Relationship Id="rId3" Type="http://schemas.openxmlformats.org/officeDocument/2006/relationships/image" Target="../media/<name>.png"/>`. Next picture: `rId4`, and so on.
4. Keep the aspect ratio: read the pixel size (Mac `sips -g pixelWidth -g pixelHeight <file>`, Windows `Add-Type -AssemblyName System.Drawing; $i=[Drawing.Image]::FromFile("<full path>"); "$($i.Width) $($i.Height)"`) and set `cy` = `cx` × height ÷ width.

```xml
<p:pic><p:nvPicPr><p:cNvPr id="<id>" name="<name>"/><p:cNvPicPr><a:picLocks noChangeAspect="1"/></p:cNvPicPr><p:nvPr/></p:nvPicPr><p:blipFill><a:blip r:embed="rId3"/><a:stretch><a:fillRect/></a:stretch></p:blipFill><p:spPr><a:xfrm><a:off x="<x>" y="<y>"/><a:ext cx="<width>" cy="<height>"/></a:xfrm><a:prstGeom prst="rect"><a:avLst/></a:prstGeom></p:spPr></p:pic>
```
