# Use cue points with captioning

Cue points allow you to interact with a video; for example, you can affect the
playing of an FLV file or display text at specific times in the video. If you
don't have a Timed Text XML file to use with an FLV file, you can embed event
cue points in an FLV file and then associate those cue points with text. This
section provides information on the FLVPlaybackCaptioning component cue points
standards and a brief overview of how to associate those cue points with text
for captioning. For more information on how to embed event cue points with the
Video Import wizard or the Adobe Media Encoder, "Working with Video," in _Using
Flash_.

## Understanding FLVPlaybackCaptioning cue point standards

Within the FLV file's metadata, a cue point is represented as an object with the
following properties: `name`, `time`, `type`, and `parameters`.
FLVPlaybackCaptioning ActionScript cue points have the following attributes:

`name`  
The `name` property is a string that contains the assigned name of the cue
point. The `name` property must start with the _fl.video.caption.2.0._ prefix
and follow the prefix with a string. The string is a series of positive integers
that increment each time to keep each name unique. The prefix includes the
version number that also matches the FLVPlayback version number. For Adobe Flash
CS4 and later, you must set the version number to `2.0`.

`time`  
The `time` property is the time when the caption should display.

`type`  
The `type` property is a string whose value is `"event"`.

`parameters`  
The `parameters` property is an array that supports the following name-and-value
pairs:

`text:String`  
The HTML-formatted text for the caption. This text is passed to the
`TextField.htmlText` property directly. The FLVPlaybackCaptioning component
supports an optional `text:` _n_ property, which supports the use of multiple
language tracks. For more information, see
[Support multiple language tracks with embedded cue points](#support-multiple-language-tracks-with-embedded-cue-points).

`endTime:Number`  
The time when the caption should disappear. If you do not specify this property
_,_ the FLVPlaybackCaptioning component assumes it is not a number (NaN), and
the caption is displayed until the FLV file completes (the FLVPlayback instance
dispatches the `VideoEvent.COMPLETE` event `)`. Specify the `endTime:Number`
property in seconds.

`backgroundColor:uint`  
This parameter sets the `TextField.backgroundColor`. This property is optional.

`backgroundColorAlpha:Boolean`  
If the backgroundColor has an alpha of 0%, then the parameter sets
`TextField.background` = `!backgroundColor`. This property is optional.

`wrapOption:Boolean`  
This parameter sets the TextField.wordWrap. This property is optional.

## Understanding captioning for event embedded cue points

If you do not have a Timed Text XML file that contains captions for your FLV
file, you can create captioning by associating an XML file that contains
captioning with event embedded cue points. The XML sample assumes you have
performed the following steps to create event embedded cue points in your video:

- Add the event cue points (following the FLVPlaybackCaptioning standards), and
  encode the video.

- In Flash, drag an FLVPlayback component and an FLVPlaybackCaptioning component
  to the Stage.

- Set the FLVPlayback and FLVPlaybackCaptioning components' source properties
  (the location of your FLV file and the location of your XML file).

- Publish.

  The following sample imports XML into the encoder:

      <?xml version="1.0" encoding="UTF-8" standalone="no" ?>
      <FLVCoreCuePoints>

        <CuePoint>
            <Time>9136</Time>
            <Type>event</Type>
            <Name>fl.video.caption.2.0.index1</Name>
            <Parameters>
                <Parameter>
                    <Name>text</Name>
                    <Value><![CDATA[Captioning text for the first cue point]]></Value>
                </Parameter>
            </Parameters>
        </CuePoint>

        <CuePoint>
            <Time>19327</Time>
            <Type>event</Type>
            <Name>fl.video.caption.2.0.index2</Name>
            <Parameters>
                <Parameter>
                    <Name>text</Name>
                    <Value><![CDATA[Captioning text for the second cue point]]></Value>
                </Parameter>
            </Parameters>
        </CuePoint>

        <CuePoint>
            <Time>24247</Time>
            <Type>event</Type>
            <Name>fl.video.caption.2.0.index3</Name>
            <Parameters>
                <Parameter>
                    <Name>text</Name>
                    <Value><![CDATA[Captioning text for the third cue point]]></Value>
                </Parameter>
            </Parameters>
        </CuePoint>

        <CuePoint>
            <Time>36546</Time>
            <Type>event</Type>
            <Name>fl.video.caption.2.0.index4</Name>
            <Parameters>
                <Parameter>
                    <Name>text</Name>
                    <Value><![CDATA[Captioning text for the fourth cue point]]></Value>
                </Parameter>
            </Parameters>
        </CuePoint>

      </FLVCoreCuePoints>

  The FLVPlaybackCaptioning component also supports multiple language tracks
  with embedded cue point. For more information, see
  [Support multiple language tracks with embedded cue points](#support-multiple-language-tracks-with-embedded-cue-points).

## Support multiple language tracks with embedded cue points

The FLVPlaybackCaptioning `track` property supports multiple language tracks
with embedded cue points, as long as the Timed Text XML file follows the
FLVPlaybackCaptioning cue point standards. (For more information, see
[Understanding FLVPlaybackCaptioning cue point standards](#understanding-flvplaybackcaptioning-cue-point-standards).)
However, the FLVPlaybackCaptioning component does not support multiple language
tracks in separate XML files. To use the `track` property, set the property to a
value not equal to 0. For example, if you set the track property to 1 (
`track == 1)`, the FLVPlaybackCaptioning component will search the cue point
parameters. If a match is not found, the text property in the cue point
parameters is used. For more information, see the `track` property in the
_ActionScript 3.0 Reference for the Adobe Flash Platform_.
