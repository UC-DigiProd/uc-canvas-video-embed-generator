# UC Canvas Video Embed Code Generator

A University of Canberra Digital Production utility for generating accessible, responsive video embed code for Canvas LMS.

The generator provides a simple way for staff to create consistent video embeds without needing to manually edit iframe code.

## Supported video sources

The generator supports:

- Echo360 LTI assets
- YouTube videos
- Kanopy videos
- ClickView videos

Input requirements vary by platform. The generator accepts supported video URLs or embed code, validates the input, and produces HTML ready to paste into the Canvas HTML Editor.

## Features

The generator:

- creates responsive video embeds with a maximum width of 704 px;
- generates meaningful iframe titles using the video title;
- adds a visible source attribution;
- identifies external viewing links in visible link text;
- does not enable autoplay;
- limits iframe permissions to those required by each video platform;
- validates supported URLs and hostnames;
- rejects non-HTTPS media URLs;
- safely handles user-entered titles, sources and other values;
- supports keyboard operation and accessible form validation;
- provides accessible status messages for generation, copying and errors;
- produces plain HTML that does not depend on external CSS or JavaScript when pasted into Canvas.

## Using the generator

1. Select the **Media source**.
2. Enter the **Video title**.
3. Enter the **Source or contributor**.
4. Enter the **Year**.
5. Paste the requested URL or embed code.
6. Select **Generate HTML code**.
7. Review and copy the generated HTML.
8. Open the relevant content in the Canvas HTML Editor and paste the generated code.
9. Save the Canvas content.
10. Check that the video displays and operates correctly after saving.

## Accessibility

The generator is designed with WCAG 2.2 Level AA requirements and accessible web development practices in mind.

Accessibility measures include:

- semantic HTML and native form controls;
- persistent form labels and instructions;
- keyboard-accessible controls and logical focus order;
- visible keyboard focus indicators;
- field-level validation and error identification;
- programmatically associated instructions and errors;
- accessible status announcements;
- responsive layouts that support narrow viewports and text enlargement;
- meaningful iframe titles;
- user-initiated video playback rather than autoplay;
- visible source attribution and external-platform link descriptions;
- no reliance on colour alone to communicate information.

### Video accessibility

The generator can improve the accessibility of the HTML surrounding an embedded video, but it cannot make the video itself accessible.

Before publishing a video in Canvas, check that the source media and video player meet the relevant accessibility requirements. Depending on the content, this may include:

- accurate captions;
- appropriate transcripts;
- audio description where important visual information is not otherwise communicated;
- keyboard-accessible player controls;
- clear focus indication within the player;
- accessible playback, volume, caption and fullscreen controls.

Accessibility therefore needs to be considered for both the generated embed code and the video being embedded.

## Canvas compatibility

The generated HTML is intentionally kept concise and uses standard HTML intended to be compatible with the Canvas HTML Editor.

Generated embeds avoid dependencies on:

- external stylesheets;
- JavaScript;
- custom data attributes;
- external CSS classes;
- obsolete iframe attributes.

Because Canvas sanitises HTML when content is saved, generated code should still be checked after it has been pasted into Canvas and saved.

When changing the generator, review any new elements, attributes or inline CSS against the current Canvas HTML Editor Allowlist before release.

## Security and input handling

URLs and embed code pasted into the generator are treated as untrusted input.

The generator:

- does not render pasted embed code in the generator interface;
- extracts iframe sources using browser parsing where appropriate;
- validates URL protocols and supported hostnames;
- accepts only HTTPS player and attribution URLs;
- escapes user-entered values before inserting them into generated HTML;
- rejects unsupported or malformed URLs;
- does not use `eval()` or `document.write()`.

## Platform notes

### Echo360

The generator accepts iframe code copied from the Echo360 LTI embed workflow in Canvas.

Echo360 public links are not supported because the generator is intended to preserve the Canvas/Echo360 LTI context.

### YouTube

Supported inputs include:

- standard YouTube watch URLs;
- `youtu.be` share URLs;
- supported YouTube embed URLs.

The generator extracts the video ID and creates canonical YouTube embed and attribution URLs.

### Kanopy

The generator accepts:

- Kanopy iframe embed code;
- Kanopy embed URLs;
- Kanopy watch URLs.

The institution path is retained where available, and the generator creates separate embed and watch URLs for the video.

### ClickView

The generator accepts:

- ClickView responsive iframe embed code;
- supported ClickView share or player URLs.

The validated ClickView player URL is retained for the embed and source attribution.

## Testing changes

Changes to the generator should be tested before release.

At minimum, check:

### Generator

- keyboard-only operation;
- visible focus indicators;
- required-field validation;
- error announcements;
- copy-to-clipboard behaviour and fallback;
- 200% text zoom;
- narrow viewport behaviour;
- handling of special characters in user-entered text;
- rejection of malformed and unsupported URLs.

### Generated Canvas content

For all four supported platforms:

1. Generate the embed.
2. Paste it into the Canvas HTML Editor.
3. Save the content.
4. Reopen the HTML Editor and confirm essential HTML has not been removed or changed.
5. Test keyboard access to the embedded player.
6. Test playback and player controls.
7. Test captions where available.
8. Test fullscreen operation.
9. Check the source attribution and destination.
10. Check the embed at narrow viewport widths and increased browser zoom.

## Technology

The generator intentionally uses a simple architecture:

- HTML5
- CSS
- vanilla JavaScript
- GitHub Pages

There are no JavaScript frameworks, build tools or runtime dependencies.

Roboto is used for the generator interface with Arial, Helvetica and generic sans-serif fallbacks.

The HTML generated for Canvas does not rely on the generator's fonts, stylesheet or JavaScript.

## Maintenance

When making changes, preserve the generator's core principles:

1. Accessible by default.
2. User-initiated media playback.
3. Minimal permissions for embedded players.
4. Defensive handling of pasted content.
5. Concise generated HTML.
6. Responsive behaviour.
7. Compatibility with the Canvas HTML Editor.
8. Clear source attribution.

Changes affecting generated HTML should be reviewed against the current Canvas HTML Editor Allowlist and relevant WCAG 2.2 requirements before release.
