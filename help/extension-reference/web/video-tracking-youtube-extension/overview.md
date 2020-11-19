---
title: Video Tracking | YouTube Release Notes
seo-title: Video Tracking | YouTube Release Notes for Adobe Experience Platform Launch
description: Video Tracking | YouTube Release Notes for Adobe Experience Platform Launch
seo-description: Video Tracking | BrightCove Release Notes for Adobe Experience Platform Launch
---

# Video Tracking | YouTube Release Notes

## November 19, 2020

### Video Tracking | YouTube  1.0.0

**Video Custom Cue Tracker: YouTube | Extension Documentation**

**Pre-Requisites**

Each Launch property will need the Adobe Analytics, Experience Cloud Visitor ID Service, and Core extensions installed, and configured from the Extension screen.

Per https://developers.google.com/youtube/player_parameters, use the ”Embed a player using an tag” code snippet in the HTML of each Web page where a video player is to render.

This extension version 1.0.0 supports embedding one or more YouTube videos on a single Web page by inserting an ”id” attribute with a unique value in the iframe tag, and appending ”?enablejsapi=1” to the end of the ”src” attribute value, as such:

`<iframe id="player1" width="560" height="315" src="https://www.youtube.com/embed/xpatB77BzYE?enablejsapi=1" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>`

As the extension dynamically adds the id field and enablejsapi=1 query string parameter to the iframe dynamically, do not add these to the iFrame manually.

On pages with more than one video, note that each video will use the same configuration set in the Launch rule executing on that page. For example, if you create a rule with an event that triggers on video 50% complete, each video on the page will trigger the rule at the 50% cue point.

The Extension relies on the following logic to rewrite the iFrames:

document.onreadystatechange = function () {
 if (document.readyState === 'complete') {

Therefore, there will be a slight flicker after the page loads. This behavior is expected.

**Data Elements**

There are five data elements available within the extension, none of which require configuration.

1. **Playhead Position:** This data element records the place, in seconds, of the playhead position on the video timeline, when it is called upon within a Launch Rule.
2. **Video ID:** This data element specifies the YouTube ID associated with the video.
3. **Video Name:** This data element specifies the descriptive, or friendly name of the video.
4. **Video URL:** This data element returns the YouTube.com URL for the currently loaded/playing video.
5. **Video Duration:** This data element records the total duration, in seconds, of the video content.

**Events**

There are seven events available within the extension, only Custom Cue Point Tracking requires configuration.

1. **Video Ready:** This event will trigger when the video is cued, and ready to play.
2. **Video Start:** This event will trigger when the video is first started, and when player.getCurrentTime() === 0
3. **Video Pause:** This event will trigger when the video is paused.
4. **Video Resume:** This event will trigger when the video is resumed, and when player.getCurrentTime() !== 0
5. **Custom Cue Tracking:** This event will trigger when the video reaches the specified video threshold percentage. For example, if a video is 60 seconds and the specified cue point is 50%, the event with trigger when playhead position equals 30 seconds. Cue point tracking applies to both initial play, and replay. Note that if user seeks across a cue point, the event will not fire. Cue point events only fire when playhead crosses calculated cuepoint location on timeline, and video player is playing.
6. **Video Buffer:** This event will trigger when player downloads a certain amount of data before it begins playing the video.
7. **Video Ended:** This event will trigger when a video fully-completes.

**Usage**

There will be one Launch Rule for every Video Event (listed above). As such, the user of this extension needs to create a specific Launch rule for each event they want to track. In other words, if they don't want to track Video Pause, they wouldn't create a rule for it.

Rules have 3 actions:

1. Set variables: Set the Adobe Analytics variables (map to all or some included Data Elements).
2. Send beacon: Send the Adobe Analytics beacon as a custom link tracking call, and provide a ”Link Name” value.
3. Clear variables: Clear the Adobe Analytics variables.

Example Launch Rule for ”Video Start”:

The following Video Extension objects are to be included:

Events:

”Video Start” (this event will cause the rule to fire when the visitor starts playing a YouTube video)

Condition: None

Actions: Using Analytics extension, use the Analytics extension to:

1. ”Set Variables” action, to map:
• the event for Video Start,
• a prop/eVar for the Video Duration data element,
• a prop/eVar for the Video ID data element,
• a prop/eVar for the Video Name data element,
• a prop/eVar for the Video URL data element, and
2. Then include the ”Send Beacon” action (s.tl) with link name ”video start,”
3. followed by a ”Clear Variables” action.

Tip: For implementations where multiple eVars or props for each video element can't be used, data elements values can be concatenated within Launch, parsed into Classification reports using the Classification Rule Builder Tool, per https://docs.adobe.com/content/help/en/analytics/components/classifications/classifications-rulebuilder/classification-rule-builder.html, and then applied as a segment in Analysis Workspace.

To concatenate video information values, create a new data element called ”Video Meta Data,” and program it to pull in all the Video Data Elements (listed above) and assemble them together, as such:

`var r = ””;

r.push('YouTube'); //Player Name
r.push(_satellite.getVar('Video ID'));
r.push(_satellite.getVar('Video Name'));
r.push(_satellite.getVar('Video Duration'));

return r.join('|');`

