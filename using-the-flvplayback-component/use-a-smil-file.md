# Use a SMIL file

To handle multiple streams for multiple bandwidths, the VideoPlayer class uses a
helper class (NCManager) that supports a subset of SMIL. SMIL is used identify
the location of the video stream, the layout (width and height) of the FLV file,
and the source FLV files that correspond to the different bandwidths. It can
also be used to specify the bit rate and duration of the FLV file.

Use the `source` parameter or the FLVPlayback.source property (ActionScript) to
specify the location of a SMIL file. For more information, see
[Specify the FLVPlayback source parameter](./use-the-flvplayback-component/flvplayback-component-parameters.md#specify-the-flvplayback-source-parameter)
and the `FLVPlayback.source` property in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

The following example shows a SMIL file that streams multiple bandwidth FLV
files from a FMS using RTMP:

    <smil>
    	<head>
    		<meta base="rtmp://myserver/myapp/" />
    		<layout>
    			<root-layout width="240" height="180" />
    		</layout>
    	</head>
    	<body>
            <switch>
                    <ref src="myvideo_cable.flv" dur="3:00.1"/>
                    <video src="myvideo_isdn.flv" system-bitrate="128000" dur="3:00.1"/>
                    <video src="myvideo_mdm.flv" system-bitrate="56000"dur="3:00.1"/>
            </switch>
    	</body>
    </smil>

The `<head>` tag may contain the `<meta>` and `<layout>` tags. The `<meta>` tag
supports only the `base` attribute, which is used to specify the URL of the
streaming video (RTMP from a FMS).

The `<layout>` tag supports only the `root-layout` element, which is used to set
the `height` and `width` attributes, and, therefore, determines the size of the
window in which the FLV file is rendered. These attributes accept only pixel
values, not percentages.

Within the body of the SMIL file, you can either include a single link to a FLV
source file or, if you're streaming multiple files for multiple bandwidths from
a FMS (as in the previous example), you can use the `<switch>` tag to list the
source files.

The `video` and `ref` tags within the `<switch>` tag are synonymous—they both
can use the `src` attribute to specify FLV files. Further, each can use the
`region`, `system-bitrate`, and `dur` attributes to specify the region, the
minimum bandwidth required, and the duration of the FLV file.

Within the `<body>` tag, only one occurrence of either the `<video>`, `<src>`,
or `<switch>` tag is allowed.

The following example shows a progressive download for a single FLV file that
does not use bandwidth detection:

    <smil>
        <head>
            <layout>
                <root-layout width="240" height="180" />
            </layout>
        </head>
        <body>
            <video src=""myvideo.flv" />
        </body>
    </smil>

## \<smil\>

#### Availability

Flash Professional 8.

#### Usage

    <smil>
    ...
    child tags...
    </smil>

#### Attributes

None.

#### Child tags

    <head>, <body>

#### Parent tag

None.

#### Description

Top-level tag, which identifies a SMIL file.

#### Example

The following example shows a SMIL file specifying three FLV files:

    <smil>
    	<head>
    		<meta base="rtmp://myserver/myapp/" />
    		<layout>
    			<root-layout width="240" height="180" />
    		</layout>
    	</head>
    	<body>
    	<switch>
                <ref src="myvideo_cable.flv" dur="3:00.1"/>
                <video src="myvideo_isdn.flv" system-bitrate="128000" dur="3:00.1"/>
                <video src="myvideo_mdm.flv" system-bitrate="56000"dur="3:00.1"/>
            </switch>
    	</body>
    </smil>

## \<head\>

#### Availability

Flash Professional 8.

#### Usage

    <head>
    ...
    child tags...
    </head>

#### Attributes

None.

#### Child tags

    <meta>, <layout>

#### Parent tag

    <smil>

#### Description

Supporting the `<meta>` and `<layout>` tags, specifies the location and default
layout (height and width) of the source FLV files.

#### Example

The following example sets the root layout to 240 pixels by 180 pixels:

    <head>
    <meta base="rtmp://myserver/myapp/" />
    <layout>
        <root-layout width="240" height="180" />
    </layout>
    </head>

## \<meta\>

#### Availability

Flash Professional 8.

#### Usage

    <meta/>

#### Attributes

    base

#### Child tags

    <layout>

#### Parent tag

None.

#### Description

Contains the `base` attribute which specifies the location (RTMP URL) of the
source FLV files.

#### Example

The following example shows a meta tag for a base location on `myserver`:

    <meta base="rtmp://myserver/myapp/" />

## \<layout\>

#### Availability

Flash Professional 8.

#### Usage

    <layout>
    ...
    child tags...
    </layout>

#### Attributes

None.

#### Child tags

    <root-layout>

#### Parent tag

    <meta>

#### Description

Specifies the width and height of the FLV file.

#### Example

The following example specifies the layout of 240 pixels by 180 pixels:

    <layout>
    <root-layout width="240" height="180" />
    </layout>

## \<root-layout\>

#### Availability

Flash Professional 8.

#### Usage

    <root-layout...attributes.../>

#### Attributes

Width, height

#### Child tags

None.

#### Parent tag

    <layout>

#### Description

Specifies the width and height of the FLV file.

#### Example

The following example specifies the layout of 240 pixels by 180 pixels:

    <root-layout width="240" height="180" />

## \<body\>

#### Availability

Flash Professional 8.

#### Usage

    <body>
    ...
    child tags...
    </body>

#### Attributes

None.

#### Child tags

    <video>, <ref>, <switch>

#### Parent tag

    <smil>

#### Description

Contains the `<video>`, `<ref>`, and `<switch>` tags, which specify the name of
the source FLV file, the minimum bandwidth, and the duration of the FLV file.
The `system-bitrate` attribute is supported only when using the `<switch>` tag.
Within the `<body>` tag, only one instance of either the `<switch>`, `<video>`,
or `<ref>` tag is allowed.

#### Example

The following example specifies three FLV files, two using the `video` tag, and
one using the `ref` tag:

    <body>
    <switch>
        <ref src="myvideo_cable.flv" dur="3:00.1"/>
        <video src="myvideo_isdn.flv" system-bitrate="128000" dur="3:00.1"/>
        <video src="myvideo_mdm.flv" system-bitrate="56000"dur="3:00.1"/>
    </switch>
    </body>

## \<video\>

#### Availability

Flash Professional 8.

#### Usage

    <video...attributes.../>

#### Attributes

    src, system-bitrate, dur

#### Child tags

None.

#### Parent tag

    <body>

#### Description

Synonymous with the `<ref>` tag. Supports the `src` and `dur` attributes, which
specify the name of the source FLV file and its duration. The `dur` attribute
supports the full (00:03:00:01) and partial (03:00:01) time formats.

#### Example

The following example sets the source and duration for a video:

    <video src="myvideo_mdm.flv" dur="3:00.1"/>

## \<ref\>

#### Availability

Flash Professional 8.

#### Usage

    <ref...attributes.../>

#### Attributes

    src, system-bitrate, dur

#### Child tags

None.

#### Parent tag

    <body>

#### Description

Synonymous with `<video>` tag. Supports the `src` and `dur` attributes, which
specify the name of the source FLV file and its duration. The `dur` attribute
supports the full (00:03:00:01) and partial (03:00:01) time formats.

#### Example

The following example sets the source and duration for a video:

    <ref src="myvideo_cable.flv" dur="3:00.1"/>

## \<switch\>

#### Availability

Flash Professional 8.

#### Usage

    <switch>
    	...
    	child tags...
    </switch>

#### Attributes

None.

#### Child tags

    <video>, <ref>

#### Parent tag

    <body>

#### Description

Used with either the `<video>` or `<ref>` child tag to list the FLV files for
multiple bandwidth video streaming. The `<switch>` tag supports the
`system-bitrate` attribute, which specifies the minimum bandwidth as well as the
`src` and `dur` attributes.

#### Example

The following example specifies three FLV files, two using the `video` tag, and
one using the `ref` tag:

    <switch>
    	<ref src="myvideo_cable.flv" dur="3:00.1"/>
    	<video src="myvideo_isdn.flv" system-bitrate="128000" dur="3:00.1"/>
    	<video src="myvideo_mdm.flv" system-bitrate="56000"dur="3:00.1" />
    </switch>
