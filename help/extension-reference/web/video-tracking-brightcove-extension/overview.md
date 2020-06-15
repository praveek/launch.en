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

Each Launch property will need the Adobe Analytics, Experience Cloud Visitor ID Service, and Core extensions installed, and configured in the Extension screen.

Per [https://studio.support.brightcove.com/publish/choosing-correct-embed-code.html](https://studio.support.brightcove.com/publish/choosing-correct-embed-code.html), use the &quot;In-Page embed code (Advanced)&quot; code snippet in the HTML of each Web page where a video player is to render. See also: [https://studio.support.brightcove.com/players/generating-player-embed-code.html](https://studio.support.brightcove.com/players/generating-player-embed-code.html)

While this extension version 1.0.0 supports embedding multiple BrightCove videos on a single Web page, be sure that the &quot;id&quot; property, if it exists, within the advanced embed tags have different values, like: &quot;player1,&quot; &quot;player2,&quot; etc.

On pages with multiple videos, note that each video will use the same configuration set in the Launch rule executing on that page. For example, if you create a rule with an event that triggers on video 50% complete, each video on the page will trigger the rule at the 50% cue point.

If the webpage you are planning to use with this extension has a chance of interacting with the video before the Launch tag has had a chance to completely load, please consider loading the Launch library synchronously, and place the \&lt;script type=&quot;text/javascript&quot;\&gt;\_satellite.pageBottom();\&lt;/script\&gt; tag before the video embed on the page to mitigate potential timing issues. For reference, here is the link, [https://docs.brightcove.com/brightcove-player/1.x/Player.html#vjsplayer](https://docs.brightcove.com/brightcove-player/1.x/Player.html#vjsplayer), to the BrightCove API that is used with this extension.

**Data Elements**

There are seven data elements available within the extension, none of which require configuration.

1. **Playhead Position:** This data element records the place, in seconds, of the playhead position on the video timeline, when it is called upon within a Launch Rule.
2. **Video Account ID:** This data element records the ID of the Brightcove account that published the video.
3. **Video Duration:** This data element records the total duration, in seconds, of the video content. Additionally, a Calculated Metric can be created within Analytics to convert the number in seconds, to minutes or hours.
4. **Video Ad Support:** This data elements specifies whether ads are supported within the video or not.
5. **Video ID:** This data element specifies the BrightCove ID associated with the video.
6. **Video Name:** This data element specifies the descriptive, or friendly name of the video.
7. **Video Tags:** This data element specifies the tags that the video is associated with.

**Events**

There are seven events available within the extension, only Custom Cue Point Tracking requires configuration.

1. **Custom Cue Point Tracking:** This event will trigger when the video reaches the specified video threshold percentage. For example, if a video is 60 seconds and the specified cue point is 50%, the event with trigger at the 30 second mark.
  - Please note that this event will trigger every time this cue point is reached. For example, if the user reaches the 50% mark, seeks the video before the 50% mark then reaches the 50% mark again, the trigger will fire again.
2. **Video Completed:** This event will trigger when a video fully-completes.
3. **Video Loaded Meta Data:** This event is fired when the player has received initial duration and dimension information.
4. **Video Pause:** This event will trigger when the video is paused.
5. **Video Resume:** This event will trigger when the video content is resumed after a pause event.
6. **Video Screen Change:** The event will trigger when the video switches in or out of full screen mode.
7. **Video Start:** This event will trigger when video content starts for the first time.

**Usage**

There will be one Launch Rule for every Video Event (the 7 events listed above). As such, the user of this extension needs to create a specific Launch rule for each event they want to track. In other words, if they don&#39;t want to track Video Pause, they wouldn&#39;t create a rule for it.

The rules have 3 actions:

1. the 1st action would set the AA variables (create Data Elements for all, or some, of the Data Elements listed above)
2. the 2nd would send the AA beacon,
3. and the 3rd would clear the AA variables.

_Example Launch Rule for &quot;Video Start&quot;_

The following Video Extension objects are to be included:

**Events** :

1. &quot;Video Start&quot; (this event will cause the rule to fire when the visitor starts playing a BrightCove video)

**Condition** : None

**Actions** :

1. In an Analytics &quot;Set Variables&quot; action, set;
  1. The event for **Video Start** (example: event17)
  2. a prop/eVar for the **Video Name Data Element** (example: eVar10)
  3. a prop/eVar for the **Video Duration Data Element** (example: eVar11)
  4. a prop/eVar for for the **Current Video Place** Data Element (example: eVar12)
2. the Analytics &quot;Send Beacon&quot; action (s.tl)
3. the Analytics &quot;Clear Variables&quot; action

_ **Tip:** _For those that may not want to provision multiple eVars or props for each video element, data elements values can be concatenated within Launch, and then parsed into Classification reports using the Classification Rule Builder Tool, [https://docs.adobe.com/content/help/en/analytics/components/classifications/classifications-rulebuilder/classification-rule-builder.html](https://docs.adobe.com/content/help/en/analytics/components/classifications/classifications-rulebuilder/classification-rule-builder.html), and then applied as segment in Analysis Workspace.

To do this create a new data element called something like &quot;Video MetaData&quot; and program it to pull in all the Video Data Elements (listed above) and concatenate them together.

`var r = [];

r.push( \_satellite.getVar( &#39;Video ID&#39; ) );

r.push( \_satellite.getVar( &#39;Video Name&#39; ) );

r.push( \_satellite.getVar( &#39;Video Duraction&#39; ) );


return r.join(&#39;|&#39;);`
