---
title: WIA_IPA_DATATYPE
description: The WIA_IPA_DATATYPE property contains the current data type setting for a device. A WIA minidriver creates and maintains this property.
keywords: ["WIA_IPA_DATATYPE Imaging Devices"]
topic_type:
- apiref
ms.topic: reference
api_name:
- WIA_IPA_DATATYPE
api_location:
- Wiadef.h
api_type:
- HeaderDef
ms.date: 10/04/2021
---

# WIA_IPA_DATATYPE

The WIA_IPA_DATATYPE property contains the current data type setting for a device. A WIA minidriver creates and maintains this property.

Property Type: VT_I4

Valid Values: WIA_PROP_LIST

Access Rights: Read/write

## Remarks

An application reads the WIA_IPA_DATATYPE property to determine the data type of an image. The application writes this property to set the current data type of the image that is about to be transferred.

The following table describes the constants that are valid with WIA_IPA_DATATYPE when the [**WIA_IPA_FORMAT**](wia-ipa-format.md) property is not set to WiaImgFmt_RAW.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Data type</th>
<th>Definition</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>WIA_DATA_AUTO</p></td>
<td><p>This value is valid for all programmable image data source items, including the Flatbed and Feeder. When this value is supported by the WIA mini-driver the WIA application client can set: <strong>WIA_IPA_DATATYPE</strong> in order to enable automatic color detection at the device.</p>
<p>When WIA_DATA_AUTO is set, the WIA mini-driver must update <a href="wia-ipa-depth.md" data-raw-source="[&lt;strong&gt;WIA_IPA_DEPTH&lt;/strong&gt;](wia-ipa-depth.md)"><strong>WIA_IPA_DEPTH</strong></a> on the same item to WIA_DEPTH_AUTO (which must be a supported value if the device supports automatic color).</p>
<p>When the <a href="wia-ipa-depth.md" data-raw-source="[&lt;strong&gt;WIA_IPA_DEPTH&lt;/strong&gt;](wia-ipa-depth.md)"><strong>WIA_IPA_DEPTH</strong></a> value WIA_DEPTH_AUTO is supported, the <strong>WIA_IPA_DATATYPE</strong> value WIA_DATA_AUTO is no longer optional and becomes a required value.</p></td>
</tr>
<tr class="even">
<td><p>WIA_DATA_COLOR</p></td>
<td><p>Scan data is red-green-blue (RGB). The full color format is described by using the following WIA properties:</p>
<ul>
<li><p><a href="wia-ipa-channels-per-pixel.md" data-raw-source="[&lt;strong&gt;WIA_IPA_CHANNELS_PER_PIXEL&lt;/strong&gt;](wia-ipa-channels-per-pixel.md)"><strong>WIA_IPA_CHANNELS_PER_PIXEL</strong></a></p></li>
<li><p><a href="wia-ipa-bits-per-channel.md" data-raw-source="[&lt;strong&gt;WIA_IPA_BITS_PER_CHANNEL&lt;/strong&gt;](wia-ipa-bits-per-channel.md)"><strong>WIA_IPA_BITS_PER_CHANNEL</strong></a></p></li>
<li><p><a href="wia-ipa-planar.md" data-raw-source="[&lt;strong&gt;WIA_IPA_PLANAR&lt;/strong&gt;](wia-ipa-planar.md)"><strong>WIA_IPA_PLANAR</strong></a></p></li>
<li><p><a href="wia-ipa-pixels-per-line.md" data-raw-source="[&lt;strong&gt;WIA_IPA_PIXELS_PER_LINE&lt;/strong&gt;](wia-ipa-pixels-per-line.md)"><strong>WIA_IPA_PIXELS_PER_LINE</strong></a></p></li>
<li><p><a href="wia-ipa-bytes-per-line.md" data-raw-source="[&lt;strong&gt;WIA_IPA_BYTES_PER_LINE&lt;/strong&gt;](wia-ipa-bytes-per-line.md)"><strong>WIA_IPA_BYTES_PER_LINE</strong></a></p></li>
<li><p><a href="wia-ipa-number-of-lines.md" data-raw-source="[&lt;strong&gt;WIA_IPA_NUMBER_OF_LINES&lt;/strong&gt;](wia-ipa-number-of-lines.md)"><strong>WIA_IPA_NUMBER_OF_LINES</strong></a></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>WIA_DATA_COLOR_DITHER</p></td>
<td><p>The same as WIA_DATA_COLOR, except that the data is dithered by using the currently selected dither pattern.</p></td>
</tr>
<tr class="even">
<td><p>WIA_DATA_COLOR_THRESHOLD</p></td>
<td><p>Color threshold data.</p></td>
</tr>
<tr class="odd">
<td><p>WIA_DATA_DITHER</p></td>
<td><p>Scan data is dithered by using the currently selected dither pattern.</p></td>
</tr>
<tr class="even">
<td><p>WIA_DATA_GRAYSCALE</p></td>
<td><p>Scan data represents intensity. The palette is a fixed, equally spaced grayscale with a depth that the <a href="wia-ipa-depth.md" data-raw-source="[&lt;strong&gt;WIA_IPA_DEPTH&lt;/strong&gt;](wia-ipa-depth.md)"><strong>WIA_IPA_DEPTH</strong></a> property specifies.</p></td>
</tr>
<tr class="odd">
<td><p>WIA_DATA_THRESHOLD</p></td>
<td><p>The threshold is one bit per pixel of black-and-white data. Data over the current value of <a href="wia-ips-threshold.md" data-raw-source="[&lt;strong&gt;WIA_IPS_THRESHOLD&lt;/strong&gt;](wia-ips-threshold.md)"><strong>WIA_IPS_THRESHOLD</strong></a> is converted to white; data under this value is converted to black.</p></td>
</tr>
</tbody>
</table>

The WIA_IPA_DATATYPE property is also used to describe the type of RAW data transfer to be used when the application sets the [**WIA_IPA_FORMAT**](wia-ipa-format.md) property to the value WiaImgFmt_RAW. The driver should set the WIA_IPA_DATATYPE property to a list of allowed values from which the application can pick.

The following table lists the constants that are valid with WIA_IPA_DATATYPE when WIA_IPA_FORMAT is set to WiaImgFmt_RAW.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Data type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>WIA_DATA_GRAYSCALE</p></td>
<td><p>Scan data represents intensity. The palette is a fixed, equally spaced grayscale with a depth that the <a href="wia-ipa-depth.md" data-raw-source="[&lt;strong&gt;WIA_IPA_DEPTH&lt;/strong&gt;](wia-ipa-depth.md)"><strong>WIA_IPA_DEPTH</strong></a> property specifies.</p>
<p>The <a href="wia-ipa-raw-bits-per-channel.md" data-raw-source="[&lt;strong&gt;WIA_IPA_RAW_BITS_PER_CHANNEL&lt;/strong&gt;](wia-ipa-raw-bits-per-channel.md)"><strong>WIA_IPA_RAW_BITS_PER_CHANNEL</strong></a> property must be set to 1.</p></td>
</tr>
<tr class="even">
<td><p>WIA_DATA_RAW_BGR</p></td>
<td><p>Scan data is in the BGR (blue-green-red) colorspace. The full color format is described by using the following WIA properties:</p>
<ul>
<li><p><a href="wia-ipa-channels-per-pixel.md" data-raw-source="[&lt;strong&gt;WIA_IPA_CHANNELS_PER_PIXEL&lt;/strong&gt;](wia-ipa-channels-per-pixel.md)"><strong>WIA_IPA_CHANNELS_PER_PIXEL</strong></a></p></li>
<li><p><a href="wia-ipa-bits-per-channel.md" data-raw-source="[&lt;strong&gt;WIA_IPA_BITS_PER_CHANNEL&lt;/strong&gt;](wia-ipa-bits-per-channel.md)"><strong>WIA_IPA_BITS_PER_CHANNEL</strong></a></p></li>
<li><p><a href="wia-ipa-pixels-per-line.md" data-raw-source="[&lt;strong&gt;WIA_IPA_PIXELS_PER_LINE&lt;/strong&gt;](wia-ipa-pixels-per-line.md)"><strong>WIA_IPA_PIXELS_PER_LINE</strong></a></p></li>
<li><p><a href="wia-ipa-bytes-per-line.md" data-raw-source="[&lt;strong&gt;WIA_IPA_BYTES_PER_LINE&lt;/strong&gt;](wia-ipa-bytes-per-line.md)"><strong>WIA_IPA_BYTES_PER_LINE</strong></a></p></li>
<li><p><a href="wia-ipa-number-of-lines.md" data-raw-source="[&lt;strong&gt;WIA_IPA_NUMBER_OF_LINES&lt;/strong&gt;](wia-ipa-number-of-lines.md)"><strong>WIA_IPA_NUMBER_OF_LINES</strong></a></p></li>
</ul>
<p>WIA_IPA_RAW_BITS_PER_CHANNEL must be set to 3.</p></td>
</tr>
<tr class="odd">
<td><p>WIA_DATA_RAW_CMY</p></td>
<td><p>Scan data is in the cyan-magenta-yellow (CMY) colorspace. The full color format is described by using the same WIA properties that are listed for WIA_DATA_RAW_BGR.</p>
<p>WIA_IPA_RAW_BITS_PER_CHANNEL must be set to 3.</p></td>
</tr>
<tr class="even">
<td><p>WIA_DATA_RAW_CMYK</p></td>
<td><p>Scan data is in the cyan-magenta-yellow-black (CMYK) colorspace. The full color format is described by using the same WIA properties that are listed for WIA_DATA_RAW_BGR.</p>
<p>WIA_IPA_RAW_BITS_PER_CHANNEL must be set to 4.</p></td>
</tr>
<tr class="odd">
<td><p>WIA_DATA_RAW_RGB</p></td>
<td><p>Scan data is in the red-green-blue (RGB) colorspace. The full color format is described using the same WIA properties as in WIA_DATA_RAW_BGR.</p>
<p>WIA_IPA_RAW_BITS_PER_CHANNEL must be set to 3.</p></td>
</tr>
<tr class="even">
<td><p>WIA_DATA_RAW_YUV</p></td>
<td><p>Scan data is in the luminance-blue difference-red difference (YUV) colorspace. The full color format is described by using the same WIA properties that are listed for WIA_DATA_RAW_BGR.</p>
<p>WIA_IPA_RAW_BITS_PER_CHANNEL must be set to 3.</p></td>
</tr>
<tr class="odd">
<td><p>WIA_DATA_RAW_YUVK</p></td>
<td><p>Scan data is in the luminance-blue difference-red difference-black (YUVK) colorspace. The full color format is described by using the same WIA properties that are listed for WIA_DATA_RAW_BGR.</p>
<p>WIA_IPA_RAW_BITS_PER_CHANNEL must be set to 4.</p></td>
</tr>
</tbody>
</table>

If you can set the device to only a single value, create a WIA_PROP_LIST type and place the valid value in it.

Check the [**WIA_IPA_DEPTH**](wia-ipa-depth.md) property to determine the bit depth.

The WIA_IPA_DATATYPE property usually contains a single value for cameras.

## Requirements

**Header:** wiadef.h (include Wiadef.h)

## See also

[**WIA_IPA_BITS_PER_CHANNEL**](wia-ipa-bits-per-channel.md)

[**WIA_IPA_BYTES_PER_LINE**](wia-ipa-bytes-per-line.md)

[**WIA_IPA_CHANNELS_PER_PIXEL**](wia-ipa-channels-per-pixel.md)

[**WIA_IPA_DEPTH**](wia-ipa-depth.md)

[**WIA_IPA_FORMAT**](wia-ipa-format.md)

[**WIA_IPA_NUMBER_OF_LINES**](wia-ipa-number-of-lines.md)

[**WIA_IPA_PIXELS_PER_LINE**](wia-ipa-pixels-per-line.md)

[**WIA_IPA_PLANAR**](wia-ipa-planar.md)

[**WIA_IPA_RAW_BITS_PER_CHANNEL**](wia-ipa-raw-bits-per-channel.md)

[**WIA_IPS_THRESHOLD**](wia-ips-threshold.md)
