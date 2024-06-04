# Use Timed Text captions

The FLVPlaybackCaptioning component enables captioning for the associated
FLVPlayback component by downloading a Timed Text (TT) XML file. For more
information about Timed Text format, review the
[AudioVideo Timed Text](https://www.w3.org/AudioVideo/timetext.html) information
at [www.w3.org.](https://www.w3.org)

This section provides an overview of the supported Timed Text tags, the required
captioning file tags, and an example of a Timed Text XML file. For detailed
information on all the supported Timed Text tags, see
[Timed Text tags](#timed-text-tags).

The FLVPlaybackCaptioning component supports the following Timed Text tags:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Category</p></th>
<th><p>Task</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Paragraph formatting support</p></td>
<td><p>Align a paragraph right, left, or center</p></td>
</tr>
<tr class="even">
<td><p>Text formatting support</p></td>
<td><div>
<ul class="incremental">
<li><p>Set the size of the text with absolute pixel sizes or delta style
(for example, +2, -4)</p></li>
<li><p>Set the text color and font</p></li>
<li><p>Make text bold and italic</p></li>
<li><p>Set text justification</p></li>
</ul>
</div></td>
</tr>
<tr class="odd">
<td><p>Other formatting support</p></td>
<td><div>
<ul class="incremental">
<li><p>Set the background color of the TextField for captions</p></li>
<li><p>Set the background color of the TextField for captions to
transparent (alpha 0)</p></li>
<li><p>Set the word wrap of the TextField for captions (on or
off)</p></li>
</ul>
</div></td>
</tr>
</tbody>
</table>

The FLVPlaybackCaptioning component matches the time code of the FLV file. Every
caption must have a `begin` attribute, which determines when the caption should
appear. If the caption does not have a `dur` or `end` attribute, the caption
disappears when the next caption appears, or when the FLV file ends.

The following is an example of a Timed Text XML file. This file
(caption_video.xml) provides captioning for the caption_video.flv file. Access
these files at [caption_video.flv](../img/helpexamples/caption_video.flv) and
[caption_video.xml](../img/helpexamples/caption_video.xml).

    <?xml version="1.0" encoding="UTF-8"?>
    <tt xml:lang="en" xmlns="http://www.w3.org/2006/04/ttaf1"xmlns:tts="http://www.w3.org/2006/04/ttaf1#styling">
        <head>
            <styling>
                <style id="1" tts:textAlign="right"/>
                <style id="2" tts:color="transparent"/>
                <style id="3" style="2" tts:backgroundColor="white"/>
                <style id="4" style="2 3" tts:fontSize="20"/>
            </styling>
        </head>
        <body>
            <div xml:lang="en">
                <p begin="00:00:00.00" dur="00:00:03.07">I had just joined <span tts:fontFamily="monospaceSansSerif,proportionalSerif,TheOther"tts:fontSize="+2">Macromedia</span> in 1996,</p>
                <p begin="00:00:03.07" dur="00:00:03.35">and we were trying to figure out what to do about the internet.</p>
                <p begin="00:00:06.42" dur="00:00:03.15">And the company was in dire straights at the time.</p>
                <p begin="00:00:09.57" dur="00:00:01.45">We were a CD-ROM authoring company,</p>
                <p begin="00:00:11.42" dur="00:00:02.00">and the CD-ROM business was going away.</p>
                <p begin="00:00:13.57" dur="00:00:02.50">One of the technologies I remember seeing was Flash.</p>
                <p begin="00:00:16.47" dur="00:00:02.00">At the time, it was called <span tts:fontWeight="bold" tts:color="#ccc333">FutureSplash</span>.</p>
                <p begin="00:00:18.50" dur="00:00:01.20">So this is where Flash got its start.</p>
                <p begin="00:00:20.10" dur="00:00:03.00">This is smart sketch running on the <span tts:fontStyle="italic">EU-pin computer</span>,</p>
                <p begin="00:00:23.52" dur="00:00:02.00">which was the first product that FutureWave did.</p>
                <p begin="00:00:25.52" dur="00:00:02.00">So our vision for this product was to</p>
                <p begin="00:00:27.52" dur="00:00:01.10">make drawing on the computer</p>
                <p begin="00:00:29.02" dur="00:00:01.30" style="1">as <span tts:color="#ccc333">easy</span> as drawing on paper.</p>
            </div>
        </body>
    </tt>

## Timed Text tags

The FLVPlaybackCaptioning component supports Timed Text tags for captioning XML
files. For more information about the
[Audio Video Timed Text](https://www.w3.org/AudioVideo/timetext.html) tags,
review information at [www.w3.org](https://www.w3.org). The following table
lists supported and non-supported tags.

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Function</p></th>
<th><p>Tag/Value</p></th>
<th><p>Usage/Description</p></th>
<th><p>Example</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ignored tags</p></td>
<td><p>metadata</p></td>
<td><p>Ignored / allowed at any level of the document</p></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td><p>set</p></td>
<td><p>Ignored / allowed at any level of the document</p></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td><p>xml:lang</p></td>
<td><p>Ignored</p></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td><p>xml:space</p></td>
<td><p>Ignored / Behavior overrides to:</p>
<p>xml:space="default"</p></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td><p>layout</p></td>
<td><p>Ignored / including any region tags in a layout tag
section</p></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td><p>br tag</p></td>
<td><p>All attributes and contents are ignored.</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Media Timing for Captions</p></td>
<td><p>begin attributes</p></td>
<td><p>Allowed in p tags only. Required for media time deployment of
captions.</p></td>
<td><p>&lt;p begin="3s"&gt;</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>dur attributes</p></td>
<td><p>Allowed in p tags only. Recommended. If not included, the caption
ends with the FLV file or when another caption starts.</p></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td><p>end attributes</p></td>
<td><p>Allowed in p tags only. Recommended. If not included, the caption
ends with the FLV file or when another caption starts.</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Clock Timing for Captions</p></td>
<td><p>00:03:00.1</p></td>
<td><p>Full clock format</p></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td><p>03:00.1</p></td>
<td><p>Partial clock format</p></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td><p>10</p></td>
<td><p>Offset times without units. Offset represents seconds.</p></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td><p>00:03:00:05</p>
<p>00:03:00:05.1</p>
<p>30f</p>
<p>30t</p></td>
<td><p>Not supported. Time formats that include frames or ticks are not
supported.</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Body tag</p></td>
<td><p>body</p></td>
<td><p>Required / Support for only one body tag.</p></td>
<td><p>&lt;body&gt;&lt;div&gt;...&lt;/div&gt;&lt;/body&gt;</p></td>
</tr>
<tr class="odd">
<td><p>Content tag</p></td>
<td><p>div tag</p></td>
<td><p>Zero or more allowed. The first tag is used.</p></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td><p>p tag</p></td>
<td><p>Zero or more allowed.</p></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td><p>span tag</p></td>
<td><p>A logical container for a sequence of textual content units. No
support for nested spans. Support for attribute style tags.</p></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td><p>br tag</p></td>
<td><p>Denotes an explicit line break.</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Styling Tags</p>
<p>(All style tags are used within the p tag)</p></td>
<td><p>style</p></td>
<td><p>Reference one or more style elements. Can be used as a tag and as
an attribute. As a tag, an ID attribute is required (the style can be
reused in the document). Support for one or more style tags inside style
tag.</p></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td><p>tts:background Color</p></td>
<td><p>Specify a style property that defines the background color of a
region. Alpha is ignored unless set to zero (alpha 0) to make the
background transparent. The color format is #RRGGBBAA.</p></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td><p>tts:color</p></td>
<td><p>Specify a style property that defines the foreground color. Alpha
not supported for any colors. Value <samp>transparent</samp> translates
to black.</p></td>
<td><p>&lt;style id="3" style="2" tts:backgroundColor="white"/&gt;</p>
<p>"transparent" = #00000000</p>
<p>"black"=#000000FF</p>
<p>"silver"=#C0C0C0FF</p>
<p>"grey"=#808080FF</p>
<p>"white"=#FFFFFFFF</p>
<p>"maroon"=#800000FF</p>
<p>"red"=#FF0000FF</p>
<p>"purple"=#800080FF</p>
<p>"fuchsia"("magenta")=</p>
<p>#FF00FFFF</p>
<p>"green"=#008000FF</p>
<p>"lime"=#00FF00FF</p>
<p>"olive"=#808000FF</p>
<p>"yellow"=#FFFF00FF</p>
<p>"navy"=#000080FF</p>
<p>"blue"=#0000FFFF</p>
<p>"teal"=#008080FF</p>
<p>"aqua"("cyan")=#00FFFFFF</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>tts:fontFamily</p></td>
<td><p>Specify a style property that defines the font family.</p></td>
<td><p>"default" = <samp>_serif</samp></p>
<p>"monospace" = <samp>_typewriter</samp></p>
<p>"sansSerif" = <samp>_sans</samp></p>
<p>"serif" = <samp>_serif</samp></p>
<p>"monospaceSansSerif" = <samp>_typewriter</samp></p>
<p>"monospaceSerif" = <samp>_typewriter</samp></p>
<p>"proportionalSansSerif" = <samp>_sans</samp></p></td>
</tr>
<tr class="odd">
<td></td>
<td><p>tts:fontSize</p></td>
<td><p>Specify a style property that defines the font size. Only the
first (vertical) value is used if two are supplied. Percentage values
and units are ignored. Support for absolute pixel (for example, 12) and
relative style (for example +2) sizes.</p></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td><p>tts: fontStyle</p></td>
<td><p>Specify a style property that defines the font style.</p></td>
<td><p>"normal"</p>
<p>"italic"</p>
<p>"inherit"*</p>
<p>* The default behavior; inherits the style from the enclosing
tag.</p></td>
</tr>
<tr class="odd">
<td></td>
<td><p>tts: fontWeight</p></td>
<td><p>Specify a style property that defines the font weight.</p></td>
<td><p>"normal"</p>
<p>"bold"</p>
<p>"inherit"*</p>
<p>* The default behavior; inherits the style from the enclosing
tag.</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>tts: textAlign</p></td>
<td><p>Specify a style property that defines how inline areas are
aligned within a containing block area.</p></td>
<td><p>"left"</p>
<p>"right"</p>
<p>"center"</p>
<p>"start" (="left")</p>
<p>"end" (="right")</p>
<p>"inherit"*</p>
<p>*Inherits the style from the enclosing tag. If no textAlign tag is
set, the default is "left".</p></td>
</tr>
<tr class="odd">
<td></td>
<td><p>tts: wrapOption</p></td>
<td><p>Specify a style property that defines whether or not automatic
line wrapping (breaking) applies within the context of the affected
element. This setting affects all paragraphs in the caption
element.</p></td>
<td><p>"wrap"</p>
<p>"noWrap"</p>
<p>"inherit"*</p>
<p>*Inherits the style from the enclosing tag. If no wrapOption tag is
set, the default is "wrap".</p></td>
</tr>
<tr class="even">
<td><p>Non Supported Attributes</p></td>
<td><p>tts: direction</p>
<p>tts: display</p>
<p>tts: displayAlign</p>
<p>tts: dynamicFlow</p>
<p>tts: extent</p>
<p>tts: lineHeight</p>
<p>tts: opacity</p>
<p>tts: origin</p>
<p>tts: overflow</p>
<p>tts: padding</p>
<p>tts: showBackground</p>
<p>tts: textOutline</p>
<p>tts: unicodeBidi</p>
<p>tts: visibility</p>
<p>tts: writingMode</p>
<p>tts: zIndex</p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>
