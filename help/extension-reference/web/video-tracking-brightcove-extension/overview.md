---
title: Video Tracking | BrightCove Release Notes
seo-title: Video Tracking | BrightCove Release Notes for Adobe Experience Platform Launch
description: Video Tracking | BrightCove Release Notes for Adobe Experience Platform Launch
seo-description: Video Tracking | BrightCove Release Notes for Adobe Experience Platform Launch
---

# Video Tracking | BrightCove Release Notes

## June 14, 2020

### Video Tracking | BrightCove  1.0.2

**Video Custom Cue Tracker: BrightCove | Extension Documentation**

**Pre-Requisites**

Each Launch property needs the following installed and configured:

* Adobe Analytics extension
* Experience Cloud Visitor ID Service extension
* Core extension

Per [https://studio.support.brightcove.com/publish/choosing-correct-embed-code.html](https://studio.support.brightcove.com/publish/choosing-correct-embed-code.html), use the "In-Page embed code (Advanced)" code snippet in the HTML of each Web page where a video player is to render. See also: [https://studio.support.brightcove.com/players/generating-player-embed-code.html](https://studio.support.brightcove.com/players/generating-player-embed-code.html)

While this extension version 1.0.0 supports embedding multiple BrightCove videos on a single Web page, be sure that any "id" property within the advanced embed tags has different values. For example:

* `player1`
* `player2` 
* And so on

On pages with multiple videos, note that each video uses the same configuration set in the Launch rule executing on that page. For example, if you create a rule with an event that triggers on video 50% complete, each video on the page will trigger the rule at the 50% cue point.

If the webpage you are planning to use with this extension has a chance of interacting with the video before the Launch tag has completely loaded, consider loading the Launch library synchronously, and place the `<script type="text/javascript">_satellite.pageBottom();</script>` tag before the video embed on the page to mitigate potential timing issues. For reference, here is the link, [https://docs.brightcove.com/brightcove-player/1.x/Player.html#vjsplayer](https://docs.brightcove.com/brightcove-player/1.x/Player.html#vjsplayer), to the BrightCove API that is used with this extension.

**Data Elements**

There are seven data elements available within the extension, none of which require configuration.

* **Playhead Position:** This data element records the place, in seconds, of the playhead position on the video timeline, when it is called upon within a Launch Rule.
* **Video Account ID:** This data element records the ID of the Brightcove account that published the video.
* **Video Duration:** This data element records the total duration, in seconds, of the video content. Additionally, a Calculated Metric can be created within Analytics to convert the number in seconds, to minutes or hours.
* **Video Ad Support:** This data elements specifies whether ads are supported within the video or not.
* **Video ID:** This data element specifies the BrightCove ID associated with the video.
* **Video Name:** This data element specifies the descriptive, or friendly name of the video.
* **Video Tags:** This data element specifies the tags that the video is associated with.

**Events**

There are seven events available within the extension. Only Custom Cue Point Tracking requires configuration.

* **Custom Cue Point Tracking:** This event triggers when the video reaches the specified video threshold percentage. For example, if a video is 60 seconds and the specified cue point is 50%, the event will trigger at the 30 second mark.
> [!NOTE]
>
> This event triggers every time this cue point is reached. For example, if the user reaches the 50% mark, seeks the video before the 50% mark, then reaches the 50% mark again, the trigger fires again.

* **Video Completed:** This event triggers when a video fully-completes.
* **Video Loaded Meta Data:** This event is fired when the player has received initial duration and dimension information.
* **Video Pause:** This event triggers when the video is paused.
* **Video Resume:** This event triggers when the video content is resumed after a pause event.
* **Video Screen Change:** The event triggers when the video switches in or out of full screen mode.
* **Video Start:** This event triggers when video content starts for the first time.

**Usage**

There will be one Launch Rule for every Video Event (the seven events listed above). As a result, you need to create a specific Launch rule for each event you want to track. In other words, if you don't want to track Video Pause, you wouldn't create a rule for it.

The rules have 3 actions:

1. The first action sets the Adobe Analytics variables (create Data Elements for all, or some, of the Data Elements listed above).
2. The second action sends the Analytics beacon.
3. The third clears the Analytics variables.

_Example Launch Rule for "Video Start"_

The following Video Extension objects are to be included:

**Events** :

1. "Video Start" (This event causes the rule to fire when the visitor starts playing a BrightCove video.)

**Condition** : None

**Actions** :

1. In an Analytics "Set Variables" action, set:
   * The event for **Video Start** (example: event17)
   * A prop/eVar for the **Video Name Data Element** (example: eVar10)
   * A prop/eVar for the **Video Duration Data Element** (example: eVar11)
   * A prop/eVar for for the **Current Video Place** Data Element (example: eVar12)
2. The Analytics "Send Beacon" action (`s.tl`)
3. The Analytics "Clear Variables" action

> [!TIP]
> For those who may not want to provision multiple eVars or props for each video element, data elements values can be concatenated within Launch, and then parsed into Classification reports using the Classification Rule Builder Tool, [https://docs.adobe.com/content/help/en/analytics/components/classifications/classifications-rulebuilder/classification-rule-builder.html](https://docs.adobe.com/content/help/en/analytics/components/classifications/classifications-rulebuilder/classification-rule-builder.html), and then applied as a segment in Analysis Workspace.
>
> To do this, create a new data element called something like "Video MetaData> and program it to pull in all the Video Data Elements (listed above) and concatenate them together.

```
var r = [];

r.push( \_satellite.getVar( &#39;Video ID&#39; ) );

r.push( \_satellite.getVar( &#39;Video Name&#39; ) );

r.push( \_satellite.getVar( &#39;Video Duraction&#39; ) );

return r.join(&#39;|&#39;);
```
