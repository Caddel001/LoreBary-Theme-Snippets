# LoreBary CSS Quick Guide

@harp, thanks for your awesome snippets 🫶🏻

---

## Choose the Correct Theme Area

LoreBary currently has two separate CSS surfaces. Their selectors are **not interchangeable**.

| Theme area | Root scope | Main attributes | Use it for |
| --- | --- | --- | --- |
| Laboratory / Chat Themes | `.lab-theme-scope` | `[data-lab]`, `[data-lab-role]` | Chat messages, the Laboratory header and footer, input controls, voice bubbles, and chat effects |
| Profile Themes | `.profile-theme-scope` | `[data-profile]`, ARIA states and labels | Profile avatars, navigation tabs, About Me, Write a Post, Gallery, Popular Creations, and feed posts |

> **Safe workflow:** Preview first. A working preview is not the same as a saved theme, and a saved draft is not the same as a published update. Keep a copy of the current CSS before larger changes.

Use narrow, stable selectors. Avoid broad rules such as `button { ... }` or `.profile-theme-scope img { ... }` unless every matching element should really change.

---

## 📋 Table of Contents

- [Choose the Correct Theme Area](#choose-the-correct-theme-area)
- [Converting Images to Base64](#converting-images-to-base64)
  - [How to Get the data:webp Base64 Code](#how-to-get-the-datawebp-base64-code)
- [Part I — Laboratory / Chat Themes](#part-i--laboratory--chat-themes)
- [Avatar Customization](#avatar-customization)
  - [Image around Avatar](#image-around-avatar)
  - [Avatar Glow on Hover](#avatar-glow-on-hover)
  - [Lift Hover](#lift-hover)
  - [Greyscale to Color on Hover](#greyscale-to-color-on-hover)
  - [Remove Avatar Outline/Gradient](#remove-avatar-outlinegradient)
  - [Square Avatar Boxes](#square-avatar-boxes)
  - [Small Avatars with Glowing Effect](#small-avatars-with-glowing-effect)
  - [Large Avatars Filling Portrait](#large-avatars-filling-portrait)
  - [Avatar Ring Glow](#avatar-ring-glow)
- [Chat Bubble Effects](#chat-bubble-effects)
  - [Remove Bubble Message Background](#remove-bubble-message-background)
  - [Bubble Hover Lift](#bubble-hover-lift)
  - [Button Bubbles](#button-bubbles)
- [Message Layout](#message-layout)
  - [Message Left Aligned](#message-left-aligned)
  - [Centered Chat Messages](#centered-chat-messages)
  - [Colorize Text Selection](#colorize-text-selection)
  - [Change Rating Symbols](#change-the-rating-symbol)
  - [Hide Timestamp](#hide-timestamp)
  - [Move Timestamp by Name (Right Side)](#move-timestamp-by-name-right-side)
  - [Time and Page Number Styling](#time-and-page-number-styling)
- [Header & Footer](#header--footer)
  - [Hide Avatars in Header](#hide-avatars-in-header)
  - [Hide Chat Name](#hide-chat-name)
  - [Remove Header Border](#remove-header-border)
  - [Remove Header Hairline Stripe](#remove-header-hairline-stripe)
  - [Transparent Footer](#transparent-footer)
  - [Smaller Visual Expression Portrait](#smaller-visual-expression-portrait)
  - [Small Button Footer](#small-button-footer)
  - [Small Button Header](#small-button-header)
- [Input Controls](#input-controls)
  - [Hide Action Button Labels](#hide-action-button-labels)
  - [Breathing Send Animation](#breathing-send-animation)
  - [Input Buttons Dim Until Hover](#input-buttons-dim-until-hover)
  - [Input Buttons Coloring](#input-buttons-coloring)
  - [Coloring Menu Button](#coloring-menu-button)
  - [Glowing Menu Button](#glowing-menu-button)
- [Write Menu & Voice Bubble](#write-menu--voice-bubble)
  - [Background in Write Menu](#background-in-write-menu)
  - [Text Color in Write Submenu](#text-color-in-write-submenu)
- [Part II — Profile Themes](#part-ii--profile-themes)
  - [Profile Theme Structure and Palette](#profile-theme-structure-and-palette)
  - [Fonts and Typography](#fonts-and-typography)
  - [Profile Avatar Frame](#profile-avatar-frame)
  - [Stickers and Decorative Images](#stickers-and-decorative-images)
  - [Main Profile Tabs and About Tabs](#main-profile-tabs-and-about-tabs)
  - [Moving and Framing a Status Block](#moving-and-framing-a-status-block)
  - [Write a Post](#write-a-post)
  - [SEE ALL and Popular Creations Buttons](#see-all-and-popular-creations-buttons)
  - [Comment, Share, and Like Buttons](#comment-share-and-like-buttons)
  - [Mobile Profile Repairs](#mobile-profile-repairs)
  - [Profile Selector Quick Reference](#profile-selector-quick-reference)
  - [Profile CSS Troubleshooting](#profile-css-troubleshooting)
- [Part III — Shared Animations](#part-iii--shared-animations-for-laboratory-and-profile-themes)
- [Background Effects](#background-effects)
  - [Animated Fireshine](#animated-fireshine)
  - [Animated Rain](#animated-rain)
  - [Animated Fog](#animated-fog)
  - [Animated Snow](#animated-snow)
  - [Animated Fireflies](#animated-fireflies)
  - [Animated Dustparticle](#animated-dustparticle)
  - [Animated Stars](#animated-stars)
  - [Animated Sunshine Underwater](#animated-sunshine-underwater)
  - [Animated Soft Godly Light](#animated-soft-godly-light)
  - [Shared Scrollable Foreground Fireflies and Stars](#shared-scrollable-foreground-fireflies-and-stars)

---

## Converting Images to Base64

### How to Get the data:webp Base64 Code

To use custom images in your CSS snippets, you'll need to convert them to Base64 format.

**Step 1: Prepare Your Image**
Get your image file ready (PNG, JPG, WebP, etc.)

**Step 2: Visit Base64 Converter**
Go to [Base64 Converter](https://base64.guru/converter/encode/image)

**Step 3: Configure Converter Settings**
Select every option like the example below:
- ☑️ Enable all available options
- Make sure settings match the configuration shown

<img src="./images/Base64-1.png" alt="Theme preview">
![Base64 converter settings](./images/Base64-1.png)

**Step 4: Upload Your Image**
Drop your image file into the converter tool

**Step 5: Copy the Code**
- Click the **Code** button to open the generated code
- Click **Copy** to copy the Base64 code to your clipboard

<img src="./images/Base64-2.png" alt="Theme preview">

**Step 6: Use in Your CSS**
Replace `XXX` in your CSS snippet with the copied Base64 code:

```css
.lab-theme-scope {
  --character-image: url("data:image/webp;base64,XXX");
  --user-image: url("data:image/webp;base64,XXX");
}
```

**Done!** Your image is now embedded in your CSS. 🎉

---

# Part I — Laboratory / Chat Themes

All snippets in Part I use `.lab-theme-scope` and belong to the Laboratory chat theme editor.

## Avatar Customization 

### Image around Avatar

Place custom images around your avatar frame. <img src="./images/avatar-add image to avatar.png" alt="Theme preview">

```css
.lab-theme-scope {
  --character-image: url("XXX");
  --user-image: url("XXX");
}

.lab-theme-scope [data-lab-role="character"],
.lab-theme-scope [data-lab-role="user"] {
  position: relative !important;
  overflow: visible !important;
}

/* --- Character AVATAR --- */
.lab-theme-scope [data-lab-role="character"]::after {
  content: "" !important;
  display: block !important;
  position: absolute !important;
  width: 90px !important;
  height: 89px !important;
  left: -12px !important;
  top: 12px !important;
  background-image: var(--character-image) !important;
  background-size: contain !important;
  background-repeat: no-repeat !important;
  background-position: center !important;
  transform: rotate(103deg) !important;
  pointer-events: none !important;
  z-index: 99 !important;
}

/* --- USER AVATAR --- */
.lab-theme-scope [data-lab-role="user"]::after {
  content: "" !important;
  display: block !important;
  position: absolute !important;
  width: 120px !important;
  height: 100px !important;
  right: -23px !important;
  top: 16px !important;
  background-image: var(--user-image) !important;
  background-size: contain !important;
  background-repeat: no-repeat !important;
  background-position: center !important;
  transform: rotate(8deg) scaleX(-1) !important;
  pointer-events: none !important;
  z-index: 99 !important;
}
```

**Customization:**
- Replace `XXX` with `data:webp;base64,` code (see [Converting Images to Base64](#converting-images-to-base64))
- `width` + `height`: Set the size of the image
- `left`: Shift the image left and right
- `top`: Shift the image up and down
- `rotate`: Rotate the image

---

### Avatar Glow on Hover

Add a glowing effect when hovering over avatars. <img src="./images/avatar-glow avatar when hover.png" alt="Theme preview">

```css
[data-lab="avatar"]:hover {
  box-shadow: 0 0 10px rgba(81, 160, 222, 0.3) !important;
  transition: box-shadow 0.2s !important;
}
```

---

### Lift Hover

Lift the avatar when you hover over it with a scale effect. <img src="./images/avatar-lift hover avatar.png" alt="Theme preview">

```css
[data-lab="avatar"] {
  transition: transform 0.25s ease, box-shadow 0.25s ease;
}

[data-lab="avatar"]:hover {
  transform: translateY(-2px) scale(1.05);
  box-shadow: 0 4px 14px rgba(0, 0, 0, 0.4);
}
```

---

### Greyscale to Color on Hover

Transform avatar from greyscale to color when you hover over it. <img src="./images/avatar-greyscale avatar until hover.png" alt="Theme preview">

```css
[data-lab="avatar"] img {
  filter: grayscale(100%) !important;
  transition: filter 0.3s !important;
}

[data-lab="avatar"]:hover img {
  filter: grayscale(0%) !important;
}
```

**Customization:**
- `img` = default version
- `hover img` = touching version
- `grayscale`: 0 = full color, 100 = no color

---

### Remove Avatar Outline/Gradient

Remove the default avatar outline styling. <img src="./images/avatar-remove avatar outline.png" alt="Theme preview">

```css
[data-lab="avatar"] {
  background: none !important;
  padding: 0 !important;
}
```

---

### Square Avatar Boxes

Change avatar corners from rounded to square. <img src="./images/avatar-sqaure avatar.png" alt="Theme preview">

```css
[data-lab="avatar"] {
  border-radius: 8px !important;
}
```

**Customization:**
- Adjust the `px` value for different corner radius (0 = perfectly square)

---

### Small Avatars with Glowing Effect

Create small circular avatars with a glowing colored ring effect.

```css
/* Small Avatars glowing */
[data-lab="avatar"] {
  border-radius: 50% !important;
  border: 1px solid rgba(255, 112, 74, 0.78) !important;
  box-shadow: 0 0 4px rgba(255,112,74,.88),
              0 0 14px rgba(255,112,74,.36),
              0 0 24px rgba(255,59,220,.16) !important;
}

[data-lab-role="user"] [data-lab="avatar"] {
  border-color: rgba(0, 223, 255, 0.82) !important;
  box-shadow: 0 0 4px rgba(0,223,255,.92),
              0 0 14px rgba(0,223,255,.42),
              0 0 24px rgba(255,59,220,.16) !important;
}
```

**Customization:**
- Change the `rgba()` values to customize the glow colors
- Adjust the `border-radius` for different shapes

---

### Large Avatars Filling Portrait

Make portrait avatars larger and fill the bubble space with no frame.

```css
/* Big Avatars filling Portrait */
[data-lab="portrait"],
[data-lab="portrait"] img {
  border: none !important;
  border-radius: 10px !important;
  box-shadow: none !important;
  object-fit: contain !important;
  object-position: center !important;
  background-size: contain !important;
  background-position: center !important;
  background-repeat: no-repeat !important;
}

[data-lab="bubble"]:has([data-lab="portrait"]) {
  min-height: clamp(260px, 20vw, 400px) !important;
}
```

**Customization:**
- `border-radius`: Adjust corner roundness
- `min-height`: Adjust the height of the portrait bubble

---

### Avatar Ring Glow

Add colored glowing rings to user and character avatars.

```css
[data-lab-role="user"] [data-lab="avatar"] {
  border-color: rgba(0, 223, 255, 0.82) !important;
  box-shadow: 0 0 4px rgba(0,223,255,.92),
              0 0 14px rgba(0,223,255,.42),
              0 0 24px rgba(255,59,220,.16) !important;
}

[data-lab-role="character"] [data-lab="avatar"] {
  border-color: rgba(0, 223, 255, 0.82) !important;
  box-shadow: 0 0 4px rgba(0,223,255,.92),
              0 0 14px rgba(0,223,255,.42),
              0 0 24px rgba(255,59,220,.16) !important;
}
```

**Customization:**
- Modify `rgba()` values to change glow colors for each role

---

## Chat Bubble Effects

### Remove Bubble Message Background

Make chat bubbles completely transparent.  <img src="./images/bubble-remove message border.png" alt="Theme preview">

```css
[data-lab="bubble"] {
  background: transparent !important;
  border: none !important;
  box-shadow: none !important;
  padding: 0 !important;
}
```

---

### Bubble Hover Lift

Lift chat bubbles slightly when you hover over them. 

```css
[data-lab="bubble"] {
  transition: transform 0.2s ease, box-shadow 0.2s ease !important;
}

[data-lab="bubble"]:hover {
  transform: translateY(-2px) !important;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2) !important;
}
```

---

### Button Bubbles

Style swipe buttons and mini actions on chat bubbles with custom colors and hover effects.

```css
/* Swipe-Buttons and mini actions on the chat bubbles */
[data-lab="swipe"],
[data-lab="action"] {
  color: #fff0d4 !important;
  background: linear-gradient(
    145deg,
    rgba(65, 48, 40, .91),
    rgba(31, 38, 37, .91)
  ) !important;
  border: 1px solid rgba(235, 173, 117, .48) !important;
  border-radius: 999px !important;
  box-shadow:
    inset 0 1px 0 rgba(255, 255, 255, .16),
    0 4px 12px rgba(44, 27, 19, .25) !important;
}

/* Hover */
[data-lab="swipe"]:hover,
[data-lab="action"]:hover {
  background: linear-gradient(
    145deg,
    rgba(90, 58, 42, .94),
    rgba(37, 79, 74, .92)
  ) !important;
  border-color: rgba(71, 145, 136, .78) !important;
}

/* Image icons */
[data-lab="swipe"] img,
[data-lab="action"] img,
img[data-lab="swipe"],
img[data-lab="action"] {
  filter: sepia(.62) saturate(.72) hue-rotate(335deg)
    brightness(1.18) contrast(.96) !important;
  opacity: 1 !important;
}

/* SVG icons */
[data-lab="swipe"] svg,
[data-lab="swipe"] svg *,
[data-lab="action"] svg,
[data-lab="action"] svg * {
  color: #fff0d4 !important;
  stroke: #fff0d4 !important;
}
```

---

## Message Layout

### Message Left Aligned

Align user messages to the left side instead of the right. 

Default: <img src="./images/message-left left aligned.png" alt="Theme preview"> right side: <img src="./images/message-left right aligned.png" alt="Theme preview">

```css
[data-lab-role="user"] {
  justify-content: flex-start !important;
}

[data-lab-role="user"] [data-lab="avatar"] {
  order: 0 !important;
}

[data-lab-role="user"] .max-w-\[65\%\] {
  order: 1 !important;
  text-align: left !important;
}
```

**Customization:**
- `order: 0` = avatar appears first (right side)
- Default behavior has avatar on left side like Bary

---

### Centered Chat Messages

Center chat messages with equal room on both sides. <img src="./images/bubble-centered messages.png" alt="Theme preview">

```css
[data-lab="message"] {
  max-width: 90% !important;
  margin-left: auto !important;
  margin-right: auto !important;
}
```

**Customization:**
- `max-width`: Adjust how close the text should be (100 = default, 90 = closer to center)

---

### Colorize Text Selection

Add color to selected text with a custom background. <img src="./images/message-colorize text.png" alt="Theme preview">

```css
.lab-theme-scope ::selection {
  background: rgba(174, 153, 255, 0.3);
  color: #fff;
}
```

**Customization:**
- `rgba()`: Set your preferred color (RGBA format)

---

### Change the Rating Symbol

Changes the rating acorns to sparkles

<img src="./images/message-hides timestamp at both sides.png" alt="Theme preview">

```css
[data-lab="rating"] img {
  content: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23ffffff' stroke-width='1.6' stroke-linejoin='round'%3E%3Cpath d='M12 2l2.2 6.6L21[...]
  width: 16px !important;
  height: 16px !important;
} 
```

---

### Hide Timestamp

Hide timestamps from all messages. 

```css
[data-lab="time"] {
  display: none !important;
}
```

---

### Move Timestamp by Name (Right Side)

Move timestamps to appear above the chat bubble on the right side. <img src="./images/message-default moves timestamp.png" alt="Theme preview">

```css
[data-lab="message"] > div:has([data-lab="bubble"]) {
  position: relative !important;
}

[data-lab="time"] {
  position: absolute !important;
  top: 4px !important;
  right: 8px !important;
  font-size: 0.7em !important;
}
```

**For left side, change to:**

<img src="./images/message-move timestamp.png" alt="Theme preview">

```css
[data-lab="time"] {
  position: absolute !important;
  top: 4px !important;
  left: 120px !important;
}
```

**Customization:**
- `font-size`: Changes the timestamp size
- `right`: Delete to set the timestamp to the left
- `top`: Delete to set the timestamp below the chat bubble

---

### Time and Page Number Styling

Style the time display and page numbering between swipe buttons with custom fonts and colors.

```css
/* Time and Page number between the swipe buttons */
[data-lab="time"],
.lab-theme-scope :has(> [data-lab="swipe"]) {
  color: #f1e5cf !important;
  -webkit-text-fill-color: #f1e5cf !important;
  font-family: 'Kalam', 'Trebuchet MS', sans-serif !important;
  font-size: .82rem !important;
  font-weight: 600 !important;
  letter-spacing: .03em !important;
  text-shadow: none !important;
  opacity: .9 !important;
}
```

**Customization:**
- `color`: Change the text color
- `font-family`: Use different fonts
- `font-size`: Adjust text size

---

## Header & Footer

### Hide Avatars in Header

Remove avatar display from the chat header. <img src="./images/header-hide avatar in header.png" alt="Theme preview">

```css
[data-lab="header"] [data-lab="avatar"],
[data-lab="header"] [data-lab="avatar"] + div {
  display: none !important;
}
```

---

### Hide Chat Name

Hide the chat name/title in the header. <img src="./images/header-hide chatname.png" alt="Theme preview">

```css
[data-lab="header-title"] > :first-child {
  font-size: 0 !important;
}
```

---

### Remove Header Border

Remove the border or shadow beneath the header. <img src="./images/header-remove header border.png" alt="Theme preview">

```css
[data-lab="header"] {
  border-bottom: none !important;
  box-shadow: none !important;
}
```

---

### Remove Header Hairline Stripe

Remove the decorative hairline stripe from the header. <img src="./images/header-remove hairline.png" alt="Theme preview">

```css
[data-lab="header"] > [aria-hidden="true"],
[aria-hidden="true"][style*="repeating-linear-gradient"] {
  display: none !important;
}
```

---

### Transparent Footer

Make the footer transparent with a frosted glass effect. <img src="./images/footer-transparent footer.png" alt="Theme preview">

```css
[data-lab="footer"] {
  background: rgba(0, 0, 0, 0.25) !important;
  backdrop-filter: blur(12px) !important;
  box-shadow: none !important;
  border: none !important;
}

/* Taller input box */
[data-lab="textbox"] {
  min-height: 52px !important;
}
```

**Customization:**
- `background`: Set a custom color (RGBA format)
- `min-height`: Adjust input box height

---

### Smaller Visual Expression Portrait

Scale down the expression portrait display. 

Default <img src="./images/message-default character.png" alt="Theme preview"> Example: <img src="./images/message-set character.png" alt="Theme preview">

```css
[data-lab="expression"] {
  scale: 0.7 !important;
  transform-origin: bottom left !important;
  margin-left: 20px !important;
  margin-bottom: 10px !important;
}
```

**Customization:**
- `scale`: Set the scale factor
- `margin-left`: Set further left/right
- `margin-bottom`: Set further up/down

---

### Small Button Footer

Style small buttons in the footer with custom text color.

```css
[data-lab="input"] > :is(button, [role="button"])
:not([data-lab="write"])
:not([data-lab="send"])
:not(:has([data-lab="write"], [data-lab="send"])),
[data-lab="input"] [data-lab*="image"] {
  color: #de3517 !important;
}

[data-lab="time-skip"] {
  color: #de3517 !important;
}

[data-lab="input"] button:not([data-lab]),
[data-lab="input"] [role="button"]:not([data-lab]) {
  color: #de3517 !important;
}
```

**Customization:**
- Change `#de3517` to your desired button color

---

### Small Button Header

Style small buttons in the header with custom text color.

```css
[data-lab="header"] button,
[data-lab="header"] [role="button"],
[data-lab="back"] {
  color: #de3517 !important;
}
```

**Customization:**
- Change `#de3517` to your desired button color

---

## Input Controls

### Hide Action Button Labels

Hide labels on action buttons (regenerate, enhance, continue, listen) showing only icons. <img src="./images/message-hidden action buttons.png" alt="Theme preview">

```css
[data-lab="action"] {
  font-size: 0 !important;
}

[data-lab="action"] img {
  width: 14px !important;
  height: 14px !important;
}
```

---

### Breathing Send Animation

Make the send button dim and brighten continuously like breathing. <img src="./images/input-breathing button.png" alt="Theme preview">

```css
@keyframes breathe {
  0%, 100% { opacity: 0.5; }
  50%      { opacity: 1; }
}

[data-lab="send"] {
  animation: breathe 2.5s ease infinite !important;
}
```

---

### Input Buttons Dim Until Hover

Dim write and send buttons until you hover over them. <img src="./images/input-dim buttons.png" alt="Theme preview">

```css
[data-lab="send"],
[data-lab="write"],
[data-lab="write-options"],
[data-lab="attach-image"],
[data-lab="input"] button[title*="auto" i] {
  opacity: 0.4 !important;
  transition: opacity 0.2s !important;
}

[data-lab="send"]:hover,
[data-lab="write"]:hover,
[data-lab="write-options"]:hover,
[data-lab="attach-image"]:hover,
[data-lab="input"] button[title*="auto" i]:hover {
  opacity: 1 !important;
}
```

**Customization:**
- `opacity`: Set the dimness/brightness (1 = bright, 0.1 = dark)

---

### Input Buttons Coloring

Apply custom color filters to input button icons. <img src="./images/input-coloring buttons.png" alt="Theme preview">

```css
[data-lab="send"] img,
[data-lab="write"] img {
  filter: brightness(1) sepia(0) saturate(1) hue-rotate(170deg) brightness(1.2) !important;
  opacity: 1 !important;
}
```

---

### Coloring Menu Button

Apply custom color to the menu button. <img src="./images/header-color menu.png" alt="Theme preview">

```css
img[data-lab="menu"] {
  filter: brightness(0.5) sepia(1) saturate(20) hue-rotate(165deg) brightness(0.9) !important;
  opacity: 1 !important;
}
```

**Customization:**
- `brightness`: 1 = dark, 99 = brightest
- `sepia`: 1 = default, 2 = sepia mode
- `saturate`: 0 = off, 99 = brightest shine
- `hue-rotate`: Adjusts the color

---

### Glowing Menu Button

Add a glowing effect to the menu button. <img src="./images/header-glow menu.png" alt="Theme preview">

```css
[data-lab="menu"] {
  filter: drop-shadow(0 0 8px rgba(255, 255, 255, 0.6)) !important;
}
```

**Customization:**
- `rgba()`: Set the glow color

---

## Write Menu & Voice Bubble

### Background in Write Menu

Add a custom gradient background to the write menu and voice bubble.

```css
[data-lab="voice-bubble"],
[data-lab="write-menu"] {
  background:
    linear-gradient(
      135deg,
      rgba(31, 16, 7, 0.92),
      rgba(18, 9, 4, 0.90)
    ) !important;

  border: 1px solid rgba(194, 138, 54, 0.42) !important;
  border-radius: 12px !important;

  box-shadow:
    0 8px 18px rgba(10, 5, 2, 0.44) !important;
}
```

**Customization:**
- Modify the gradient colors in `linear-gradient()`
- Adjust `border-color` and `border-radius` values

---

### Text Color in Write Submenu

Change the text color in the write submenu completely.

```css
[data-lab="write-menu"] > .px-3.py-2.text-\[10px\].leading-snug.text-gray-300 {
  color: #526b56 !important;
  -webkit-text-fill-color: #526b56 !important;
}

[data-lab="write-menu"] button,
[data-lab="write-menu"] button *,
[data-lab="write-menu"] [role="button"],
[data-lab="write-menu"] [role="button"] * {
  color: #526b56 !important;
  -webkit-text-fill-color: #526b56 !important;
}

/* For the info text at the bottom */
[data-lab="write-menu"] > .px-3.py-2.text-\[10px\].leading-snug.text-gray-300 {
    color: #000;
}
```

**Customization:**
- Replace `#526b56` with your desired color
- Replace `#000` with your desired bottom text color

---

# Part II — Profile Themes

Profile themes use `.profile-theme-scope` and `[data-profile="..."]`. Keep every profile rule inside the profile scope so it does not recolor LoreBary navigation, dialogs, or Laboratory chats.

## Profile Theme Structure and Palette

### Core component map

| Selector | Component |
| --- | --- |
| `[data-profile="scope"]` | Root of the themed profile |
| `[data-profile="hero"]` | Banner and identity area |
| `[data-profile="avatar-wrap"]` | Positioning anchor for a decorative avatar frame |
| `[data-profile="avatar"]` | Clipped avatar circle or shape |
| `[data-profile="avatar-img"]` | Actual portrait image |
| `[data-profile="tabs"]` / `[data-profile="tab"]` | Main profile navigation |
| `[data-profile="about"]` | About Me area and its icon tabs |
| `[data-profile="composer-slot"]` | Write a Post placement area |
| `[data-profile="gallery-preview"]` | Gallery preview panel |
| `[data-profile="popular-content"]` | Popular Creations panel and carousel |
| `[data-profile="feed-list"]` | Profile post feed |

### Reusable color variables

Change this small palette first. The component snippets below reuse these values.

```css
.profile-theme-scope[data-profile="scope"] {
  --theme-bg: #171512;
  --theme-panel: #2c241c;
  --theme-panel-2: #3b2e21;
  --theme-text: #fff1cf;
  --theme-muted: #c9b58f;
  --theme-edge: #a77b3f;
  --theme-accent: #d7ad63;
  --theme-shadow: 0 8px 24px rgba(0, 0, 0, .45);

  color: var(--theme-text) !important;
  background-color: var(--theme-bg) !important;
}
```

### Safe hover and keyboard focus

Use `:hover` for pointers and `:focus-visible` for keyboard navigation. Do not remove the focus outline without providing a visible replacement.

```css
@media (hover: hover) {
  .profile-theme-scope .theme-button:hover {
    color: #ffffff !important;
    background: #765034 !important;
    border-color: #f0cc83 !important;
    transform: translateY(-1px);
  }
}

.profile-theme-scope .theme-button:focus-visible {
  outline: 2px solid #fff1a8 !important;
  outline-offset: 2px;
}

.profile-theme-scope .theme-button:active {
  transform: translateY(1px);
}
```

---

## Fonts and Typography

Use a readable body font and reserve decorative fonts for names, headings, and selected labels. Always include fallback fonts because remote fonts can fail to load or may be blocked by the editor.

### Safe system-font setup

This method needs no external font file and works offline.

```css
.profile-theme-scope[data-profile="scope"] {
  --profile-font-body: Georgia, "Times New Roman", serif;
  --profile-font-title: "Trebuchet MS", Arial, sans-serif;
  font-family: var(--profile-font-body) !important;
}

.profile-theme-scope [data-profile="display-name"],
.profile-theme-scope [data-profile="display-name"] *,
.profile-theme-scope [data-profile="composer-header"] h3,
.profile-theme-scope section:has([data-profile="about-card"])
  > header :is(h2, span),
.profile-theme-scope [data-profile="gallery-preview"] h2,
.profile-theme-scope [data-profile="popular-content"] h2 {
  font-family: var(--profile-font-title) !important;
  letter-spacing: .08em;
}

.profile-theme-scope [data-profile="tab"],
.profile-theme-scope [data-profile="about-card"],
.profile-theme-scope [data-profile="composer-editor"] {
  font-family: var(--profile-font-body) !important;
}
```

### Laboratory font variables

Laboratory already exposes useful font variables. Set them on the Laboratory scope instead of repeating `font-family` on every message element.

```css
.lab-theme-scope {
  --lab-font-family: Georgia, "Times New Roman", serif;
  --lab-char-name-font: "Trebuchet MS", Arial, sans-serif;
  --lab-persona-name-font: "Trebuchet MS", Arial, sans-serif;
}
```

### Optional web font

Remote imports work only when the theme editor and the font host permit them. An `@import` rule must sit at the very top of the stylesheet, before normal CSS rules. Keep the fallback stack even when the import works.

```css
@import url("https://fonts.googleapis.com/css2?family=Cinzel:wght@600;700&family=Lexend:wght@400;600&display=swap");

.profile-theme-scope[data-profile="scope"] {
  --profile-font-body: Lexend, Arial, sans-serif;
  --profile-font-title: Cinzel, Georgia, serif;
}
```

If `@import` is rejected by the safety checker, use system fonts or embed a properly licensed WOFF2 file with `@font-face` and a Base64 data URL. Do not remove the fallback fonts.

### Useful typography properties

| Property | Purpose |
| --- | --- |
| `font-family` | Selects the font and fallbacks |
| `font-size` | Changes text size |
| `font-weight` | Controls regular, semibold, or bold text |
| `font-style` | Adds or removes italics |
| `letter-spacing` | Opens or tightens heading letters |
| `line-height` | Improves paragraph readability |
| `text-transform` | Uppercase, lowercase, or normal case |
| `text-shadow` | Separates text from textured backgrounds |

---

## Profile Avatar Frame

The most reliable profile frame is a transparent PNG or WebP attached to the outer avatar wrapper. Keep the portrait, the decorative frame, and the action buttons on separate layers.

| Before: portrait without the decorative frame | After: transparent frame aligned to the portrait |
| --- | --- |
| <img src="./images/profile/avatar-frame-before.png" alt="Profile avatar before adding the decorative frame"> | <img src="./images/profile/avatar-frame-after.png" alt="Profile avatar after adding the decorative frame"> |

### Centered decorative frame

```css
.profile-theme-scope [data-profile="avatar-wrap"] {
  position: relative;
  overflow: visible !important;
  isolation: isolate;
}

.profile-theme-scope [data-profile="avatar"] {
  position: relative;
  z-index: 1;
  overflow: hidden;
  border: 2px solid #d1b781 !important;
  background: #2e261d !important;
}

.profile-theme-scope [data-profile="avatar-wrap"]::after {
  content: "";
  position: absolute;
  inset: -5%;
  z-index: 3;
  pointer-events: none;
  background: url("YOUR-TRANSPARENT-FRAME.png") center / contain no-repeat;
}

.profile-theme-scope [data-profile="avatar-actions"] {
  position: relative;
  z-index: 5;
}
```

`pointer-events: none` is important: the transparent rectangle around the artwork must not block avatar or remove-button clicks.

### Fit the portrait inside the frame opening

Use the same inset for the portrait and its click overlay. Absolute positioning is more reliable than compensating with margins.

```css
.profile-theme-scope [data-profile="avatar"]
  > [data-profile="avatar-img"] {
  position: absolute !important;
  inset: 14% !important;
  width: 72% !important;
  height: 72% !important;
  margin: 0 !important;
  object-fit: cover !important;
  border-radius: 50% !important;
}

.profile-theme-scope [data-profile="avatar"] > div.absolute {
  inset: 14% !important;
}
```

### Asymmetrical frame artwork

Use this pattern when flowers, horns, a lantern, a skull, or another ornament extends farther on one side. Align the visible opening, not the full transparent image bounds.

```css
.profile-theme-scope [data-profile="avatar-wrap"]::after {
  content: "";
  position: absolute;
  width: 150%;
  height: 150%;
  left: -33%;
  top: -39%;
  z-index: 3;
  pointer-events: none;
  background: url("ASYMMETRICAL-FRAME.png") center / 100% 100% no-repeat;
}
```

### Mobile avatar alignment

```css
@media (max-width: 767px) {
  .profile-theme-scope [data-profile="avatar-wrap"]::after {
    inset: -5%;
  }

  .profile-theme-scope [data-profile="avatar"]
    > [data-profile="avatar-img"],
  .profile-theme-scope [data-profile="avatar"] > div.absolute {
    inset: 14% !important;
  }
}
```

If the artwork is asymmetrical, give its mobile rule its own `width`, `height`, `left`, and `top` values instead of reusing `inset`.

---

## Stickers and Decorative Images

The cleanest CSS-only sticker is a transparent PNG or WebP placed in a pseudo-element. Attach it to the nearest stable component, make that component `position: relative`, and keep the sticker click-through.

<img src="./images/profile/responsive-desktop-example.png" alt="Profile example with decorative character artwork and themed panels">

### Reusable sticker variable

```css
.profile-theme-scope[data-profile="scope"] {
  --profile-sticker: url("YOUR-TRANSPARENT-STICKER.png");
}
```

### Sticker above the About Me panel

```css
.profile-theme-scope section:has([data-profile="about-card"]) {
  position: relative;
  overflow: visible !important;
  isolation: isolate;
}

.profile-theme-scope
  section:has([data-profile="about-card"])::after {
  content: "";
  position: absolute;
  top: -54px;
  right: 18px;
  width: clamp(74px, 8vw, 108px);
  aspect-ratio: 1 / 1;
  z-index: 20;
  pointer-events: none;
  background: var(--profile-sticker) center / contain no-repeat;
  transform: rotate(8deg);
  filter: drop-shadow(0 7px 6px rgba(0, 0, 0, .55));
}
```

### Sticker in the center of the profile body

```css
.profile-theme-scope [data-profile="body-inner"] {
  position: relative;
  overflow: visible !important;
}

.profile-theme-scope [data-profile="body-inner"]::after {
  content: "";
  position: absolute;
  left: 50%;
  top: 330px;
  width: 340px;
  aspect-ratio: 4 / 3;
  z-index: 60;
  pointer-events: none;
  transform: translateX(-50%);
  background: var(--profile-sticker) center / contain no-repeat;
  filter: drop-shadow(0 12px 14px rgba(0, 0, 0, .66));
}
```

### How to move the sticker

| Change | Property |
| --- | --- |
| Move down | Increase `top` |
| Move up | Decrease `top` or use a negative value |
| Move right | Increase `left`, or decrease `right` |
| Move left | Decrease `left`, or increase `right` |
| Resize | Change `width`; keep `height: auto` or an `aspect-ratio` |
| Tilt | Change `rotate(...)` inside `transform` |
| Place above other layers | Increase `z-index` on the sticker and its positioned parent |

Do not set `left` and `right` together unless you intentionally want the browser to stretch the box. When centering with `left: 50%`, keep `translateX(-50%)` in the same `transform` declaration as any rotation.

### Mobile sticker rule

Large desktop stickers often overlap the composer on mobile. Reposition or hide them deliberately.

```css
@media (max-width: 767px) {
  .profile-theme-scope
    section:has([data-profile="about-card"])::after {
    top: -32px;
    right: 8px;
    width: 70px;
    transform: rotate(5deg);
  }

  .profile-theme-scope [data-profile="body-inner"]::after {
    display: none;
  }
}
```

One element provides only one `::before` and one `::after`. If both are already used for borders or particles, anchor the sticker to another stable container instead of overwriting the existing decoration.

### Laboratory sticker equivalent

The same positioning system works in Laboratory. Only the anchor changes.

```css
.lab-theme-scope {
  --lab-sticker: url("YOUR-TRANSPARENT-STICKER.png");
}

.lab-theme-scope [data-lab="header"] {
  position: relative;
  overflow: visible !important;
}

.lab-theme-scope [data-lab="header"]::after {
  content: "";
  position: absolute;
  top: -28px;
  right: 18px;
  width: 84px;
  aspect-ratio: 1 / 1;
  z-index: 20;
  pointer-events: none;
  background: var(--lab-sticker) center / contain no-repeat;
  transform: rotate(6deg);
}
```

---

## Main Profile Tabs and About Tabs

The main profile navigation and the five About Me icon tabs are separate components. Style them independently.

<img src="./images/profile/profile-tabs-example.png" alt="Example of fully styled profile navigation tabs">

### Main profile tabs, selected state, and counts

```css
.profile-theme-scope [data-profile="tab"] {
  min-height: 36px;
  padding: 7px 12px !important;
  margin: 0 2px;
  color: #eadcc7 !important;
  background: linear-gradient(#3f3328, #2c241d) !important;
  border: 1px solid rgba(205, 164, 95, .45) !important;
  border-radius: 7px !important;
}

@media (hover: hover) {
  .profile-theme-scope [data-profile="tab"]:hover {
    background: #594634 !important;
    border-color: #d9b978 !important;
  }
}

.profile-theme-scope
  [data-profile="tab"][aria-selected="true"] {
  color: #fff4d2 !important;
  background: linear-gradient(#7c8766, #535f4d) !important;
  border-color: #d8c49d !important;
}

.profile-theme-scope [data-profile="tab-count"] {
  color: #fff4d2 !important;
  background: #6d5e4b !important;
}
```

### About Me icon tabs

```css
.profile-theme-scope [data-profile="about"] [role="tab"] {
  margin-left: 0 !important;
  color: #f0e5d0 !important;
  background: linear-gradient(#4b3c2c, #33291f) !important;
  border: 1px solid rgba(213, 168, 93, .55) !important;
  border-radius: 8px 8px 0 0 !important;
}

/* Hide only the paper plate, not the visible tab icons. */
.profile-theme-scope [data-profile="about"]
  [role="tab"] img[src*="paper-tab.webp"] {
  opacity: 0 !important;
}

.profile-theme-scope [data-profile="about"]
  [role="tab"][aria-selected="true"] {
  background: #6c7656 !important;
  border-color: #ebcd8c !important;
}
```

---

## Moving and Framing a Status Block

There are two different cases: moving the complete native About Me card, or styling only a custom status block inside your About content.

### Move and frame the complete native About Me card

Margins keep the card in the normal page flow and are the safest way to move it.

```css
.profile-theme-scope section:has([data-profile="about-card"]) {
  position: relative;
  margin-top: 18px;
  margin-left: 24px;
  width: calc(100% - 24px);
  padding: 8px;
  border: 1px solid var(--theme-edge) !important;
  border-radius: 16px !important;
  background: rgba(23, 21, 18, .72) !important;
  box-shadow: var(--theme-shadow) !important;
}

.profile-theme-scope [data-profile="about-card"] {
  overflow: hidden;
  border: 1px solid rgba(215, 173, 99, .55) !important;
  border-radius: 12px !important;
  background: var(--theme-panel) !important;
}
```

For a small visual adjustment that should not change document flow, use `transform`. Remember that the original layout space remains where it was.

```css
.profile-theme-scope [data-profile="about-card"] {
  transform: translate(18px, -10px);
}
```

### Create a separate custom status box

If the About editor accepts custom HTML, give the status its own class. CSS cannot reliably select an element only because its visible text says “STATUS”.

```html
<section class="lb-profile-status">
  <h3 class="lb-profile-status__title">STATUS</h3>
  <p><strong>Currently working on</strong><br>Updating plugins</p>
  <p><strong>Coming next</strong><br>N/A</p>
  <p><strong>Energy level</strong><br>Tired</p>
</section>
```

```css
.profile-theme-scope .lb-profile-status {
  box-sizing: border-box;
  width: min(100%, 360px);
  margin: 22px auto;
  padding: 18px 20px;
  color: var(--theme-text);
  background:
    linear-gradient(145deg, rgba(59, 46, 33, .97), rgba(31, 25, 20, .97));
  border: 1px solid var(--theme-edge);
  border-left: 4px solid var(--theme-accent);
  border-radius: 14px;
  box-shadow: var(--theme-shadow);
}

.profile-theme-scope .lb-profile-status__title {
  margin: 0 0 12px;
  color: var(--theme-accent);
  font-family: var(--profile-font-title, Georgia, serif);
  letter-spacing: .12em;
}

.profile-theme-scope .lb-profile-status p {
  margin: 10px 0;
  line-height: 1.45;
}
```

### Move only the custom status box

```css
@media (min-width: 1024px) {
  .profile-theme-scope .lb-profile-status {
    position: relative;
    left: 28px;
    top: -14px;
  }
}

@media (max-width: 767px) {
  .profile-theme-scope section:has([data-profile="about-card"]) {
    margin-left: 0;
    width: 100%;
    padding: 5px;
  }

  .profile-theme-scope [data-profile="about-card"],
  .profile-theme-scope .lb-profile-status {
    left: auto;
    top: auto;
    width: 100%;
    transform: none;
  }
}
```

If the status is a single image rather than HTML, apply the frame to its wrapper and use `object-fit: contain` on the image so it remains readable instead of being cropped.

---

## Write a Post

The composer is not one box. It contains a card shell, header, option buttons, body, formatting toolbar, editor, placeholder, footer, switch, and Post button. Style each layer explicitly.

<img src="./images/profile/write-a-post-example.png" alt="Example of a themed Write a Post composer">

### Component map

| Selector | Component |
| --- | --- |
| `[data-profile="composer-slot"] > .surface-post` | Outer composer card |
| `[data-profile="composer-header"]` | WRITE A POST title row and top controls |
| `[data-profile="composer-header"] button` | Public and Notify followers buttons |
| `[data-profile="composer-body"]` | Avatar and editor area |
| `[data-profile="composer-toolbar"]` | Formatting toolbar |
| `[data-profile="composer-toolbar"] button` | Bold, italic, underline, attachment, emoji, and more |
| `[data-profile="composer-editor"]` | Editable text field |
| `[data-placeholder]::before` | Placeholder text |
| `[data-profile="composer-footer"]` | Terms, switch, and Post button area |

### Card shell and header

```css
.profile-theme-scope [data-profile="composer-slot"]
  > .surface-post {
  overflow: hidden;
  color: var(--theme-text) !important;
  background: var(--theme-panel) !important;
  border: 1px solid var(--theme-edge) !important;
  border-radius: 12px !important;
  box-shadow: var(--theme-shadow) !important;
}

.profile-theme-scope [data-profile="composer-header"] {
  color: #fff1cf !important;
  background: linear-gradient(100deg, #5b3a24, #38251a) !important;
  border-bottom: 1px solid rgba(213, 168, 93, .65) !important;
  border-radius: 11px 11px 0 0 !important;
}

.profile-theme-scope [data-profile="composer-header"] h3 {
  color: inherit !important;
  letter-spacing: .08em;
}

.profile-theme-scope [data-profile="composer-header"] button {
  color: #fff1cf !important;
  background: #30291f !important;
  border: 1px solid rgba(213, 168, 93, .55) !important;
}
```

### Body, toolbar, editor, and placeholder

```css
.profile-theme-scope [data-profile="composer-body"] {
  background: #c7ddeb !important;
  padding: 12px !important;
}

.profile-theme-scope [data-profile="composer-toolbar"] {
  color: #f6ead2 !important;
  background: #3b3026 !important;
  border-color: rgba(213, 168, 93, .55) !important;
}

.profile-theme-scope [data-profile="composer-toolbar"] button {
  color: #f6ead2 !important;
  background: #564331 !important;
  border: 1px solid rgba(235, 205, 140, .55) !important;
}

.profile-theme-scope [data-profile="composer-toolbar"]
  button[aria-pressed="true"] {
  color: #ffffff !important;
  background: #7c8766 !important;
  border-color: #f0d99f !important;
}

.profile-theme-scope [data-profile="composer-editor"] {
  min-height: 150px;
  color: #2b231d !important;
  background: #fff8e9 !important;
  border-color: rgba(137, 101, 48, .55) !important;
  caret-color: #6f3138;
}

.profile-theme-scope [data-profile="composer-editor"]
  [data-placeholder]::before {
  color: #7e746c !important;
  opacity: 1 !important;
}
```

### Footer switch

```css
.profile-theme-scope [data-profile="composer-footer"] {
  color: var(--theme-muted) !important;
}

.profile-theme-scope [data-profile="composer-footer"]
  input[type="checkbox"] + div {
  background: #665744 !important;
  border-color: #a78f6a !important;
}

.profile-theme-scope [data-profile="composer-footer"]
  input[type="checkbox"] + div::after {
  background: #fff3d3 !important;
}

.profile-theme-scope [data-profile="composer-footer"]
  input[type="checkbox"]:checked + div {
  background: #71805c !important;
}
```

Keep editor text and placeholder contrast high. Decorative textures should never make typed text difficult to read.

---

## SEE ALL and Popular Creations Buttons

These controls contain raster image plates and icons. Style the button image and the label separately.

| SEE ALL button | Popular Creations carousel arrow |
| --- | --- |
| <img src="./images/profile/see-all-example.png" alt="Themed SEE ALL button"> | <img src="./images/profile/carousel-arrow-example.png" alt="Themed Popular Creations carousel arrow"> |

### SEE ALL plate and label

```css
.profile-theme-scope [data-profile="gallery-preview"]
  .dashboard-action-button img[src*="btn_pixel_plate"],
.profile-theme-scope [data-profile="popular-content"]
  .dashboard-action-button img[src*="btn_pixel_plate"] {
  filter: sepia(.92) saturate(1.75) hue-rotate(346deg)
          brightness(.86) contrast(1.28)
          drop-shadow(0 2px 2px rgba(0, 0, 0, .5)) !important;
}

.profile-theme-scope [data-profile="gallery-preview"]
  .dashboard-action-button span,
.profile-theme-scope [data-profile="popular-content"]
  .dashboard-action-button span {
  color: #fff1cf !important;
  text-shadow: 0 1px 2px rgba(0, 0, 0, .88) !important;
}
```

### Popular Creations scroll arrows

```css
.profile-theme-scope
  button[aria-label^="Scroll popular creations"] {
  background: #5b3a24 !important;
  border: 1px solid #d5a85d !important;
  box-shadow: inset 0 1px rgba(255, 241, 200, .35),
              0 2px 5px rgba(0, 0, 0, .5) !important;
}

.profile-theme-scope
  button[aria-label^="Scroll popular creations"] img {
  filter: sepia(1) saturate(1.8) hue-rotate(345deg)
          brightness(1.35) contrast(1.1) !important;
}

@media (hover: hover) {
  .profile-theme-scope
    button[aria-label^="Scroll popular creations"]:hover {
    background: #765034 !important;
    border-color: #f0cc83 !important;
  }
}
```

The `^=` operator matches both arrow labels because both begin with the same phrase.

---

## Comment, Share, and Like Buttons

```css
.profile-theme-scope [data-profile="post-like"],
.profile-theme-scope [data-profile="post-likes"],
.profile-theme-scope [data-profile="post-engagement"]
  button[aria-label="Comments"],
.profile-theme-scope [data-profile="post-engagement"]
  button[aria-label="Share"] {
  color: #fff1cf !important;
  background: linear-gradient(#5a432f, #3a2b20) !important;
  border: 1px solid #bd9457 !important;
  border-radius: 8px !important;
}

.profile-theme-scope [data-profile="post-engagement"]
  img[src*="feed_action_"],
.profile-theme-scope [data-profile="post-engagement"]
  img[src*="feed_filter_"] {
  filter: sepia(1) saturate(1.4) hue-rotate(345deg)
          brightness(1.35) !important;
}

.profile-theme-scope [data-profile="post-like"][aria-pressed="true"] {
  color: #ffffff !important;
  background: #71805c !important;
  border-color: #f0d99f !important;
}
```

### Recoloring raster UI icons

CSS `color` does not recolor the pixels of a PNG or WebP. Use a scoped `filter` on known UI assets instead.

```css
/* Good: only pixel icons inside the main profile tabs. */
.profile-theme-scope [data-profile="tab"]
  img[src*="/img/pixel/"] {
  filter: grayscale(1) sepia(.5) saturate(.6)
          brightness(1.9) contrast(.8) !important;
}

/* Avoid: this would also recolor portraits and gallery covers. */
/* .profile-theme-scope img { filter: sepia(1); } */
```

Useful starting points:

| Target | Filter |
| --- | --- |
| Warm gold | `sepia(1) saturate(1.8) hue-rotate(345deg) brightness(1.35) contrast(1.1)` |
| Cream | `grayscale(1) sepia(.5) saturate(.6) brightness(1.9) contrast(.8)` |
| Muted moss | `sepia(.8) saturate(.8) hue-rotate(55deg) brightness(.85) contrast(1.15)` |
| Burgundy | `sepia(1) saturate(2.2) hue-rotate(305deg) brightness(.72) contrast(1.25)` |
| Moon blue | `grayscale(.3) sepia(.4) saturate(1.7) hue-rotate(165deg) brightness(1.05)` |

Filter functions run from left to right. The same filter can look different on a blue plate and a gray icon.

---

## Mobile Profile Repairs

Start with the desktop component and override only what becomes too wide, clipped, or misaligned below the breakpoint.

### Responsive result example

**Desktop**

<img src="./images/profile/responsive-desktop-example.png" alt="Completed profile theme on desktop">

**Mobile**

<img src="./images/profile/responsive-mobile-example.png" alt="The same profile theme adapted for mobile" width="390">

```css
@media (max-width: 767px) {
  .profile-theme-scope [data-profile="tabs"] {
    display: flex !important;
    overflow-x: auto;
    gap: 4px;
    scrollbar-width: none;
  }

  .profile-theme-scope [data-profile="tab"] {
    flex: 0 0 auto;
    min-width: 52px;
    padding: 6px 8px !important;
    font-size: 10px !important;
  }

  .profile-theme-scope [data-profile="composer-header"] {
    display: flex !important;
    flex-wrap: wrap;
    gap: 8px;
    padding: 9px !important;
  }

  .profile-theme-scope [data-profile="composer-body"] {
    padding: 9px !important;
  }

  .profile-theme-scope [data-profile="composer-editor"] {
    min-height: 140px;
  }

  .profile-theme-scope [data-profile="about"] [role="tablist"] {
    display: grid !important;
    grid-template-columns: repeat(5, minmax(0, 1fr));
    gap: 3px;
  }

  .profile-theme-scope [data-profile="about"] [role="tab"] {
    width: 100% !important;
    min-width: 0 !important;
    margin: 0 !important;
  }
}
```

Mobile failure checklist:

- A fixed pixel width is wider than the viewport.
- A flex row cannot wrap.
- A decorative pseudo-element creates horizontal overflow.
- The frame was scaled but the portrait inset was not.
- A desktop margin still pushes the avatar or composer sideways.
- Text is present but has insufficient contrast on the mobile background.
- The browser window looks narrow, but the real viewport is still wider than `767px`.

## Profile Selector Quick Reference

### Identity and navigation

| Selector | Use |
| --- | --- |
| `[data-profile="hero"]` | Banner and identity block |
| `[data-profile="avatar-wrap"]` | Decorative avatar-frame anchor |
| `[data-profile="avatar"]` | Avatar crop, border, and shadow |
| `[data-profile="avatar-img"]` | Portrait size and `object-fit` |
| `[data-profile="avatar-actions"]` | Avatar action controls and stacking layer |
| `[data-profile="avatar-remove"]` | Remove-avatar control |
| `[data-profile="level"]` / `[data-profile="level-icon"]` | Level label and icon |
| `[data-profile="streak"]` / `[data-profile="streak-icon"]` | Streak counter and icon |
| `[data-profile="member-since-icon"]` | Calendar icon |
| `[data-profile="count-followers"]` | Followers button |
| `[data-profile="count-following"]` | Following button |
| `[data-profile="tabs"]` / `[data-profile="tab"]` | Main navigation |
| `[data-profile="tab-notch"]` | Decorative tab notch |
| `[data-profile="tab-count"]` | Number shown on a tab |

### Content, composer, and actions

| Selector | Use |
| --- | --- |
| `[data-profile="about"]` | About Me section root |
| `[data-profile="about-card"]` | Native About Me content card |
| `[data-profile="body-inner"]` | Main body positioning anchor for large stickers |
| `[data-profile="about-edit"]` | Edit About Me button |
| `[data-profile="about-more"]` | Show more button |
| `[data-profile="additional-info"]` | Role, availability, gender, and relationship information |
| `[data-profile="gallery-preview"]` | Gallery preview shell |
| `[data-profile="gallery-grid"]` | Gallery image grid |
| `[data-profile="popular-content"]` | Popular Creations shell and carousel |
| `[data-profile="feed-list"]` | Post feed container |
| `[data-profile="post"]` | One post card |
| `[data-profile="post-header"]` | Post author and metadata row |
| `[data-profile="post-body"]` | Main post content |
| `[data-profile="post-engagement"]` | Like, comment, and share row |
| `[data-profile="post-like"]` / `[data-profile="post-likes"]` | Like controls and reactions |
| `[data-profile="post-comment-count"]` | Comment count text |
| `[data-profile="composer-slot"]` | Write a Post placement area |
| `[data-profile="composer-header"]` | Composer title and options row |
| `[data-profile="composer-body"]` | Composer avatar and editor body |
| `[data-profile="composer-toolbar"]` | Formatting controls |
| `[data-profile="composer-editor"]` | Editable text field |
| `[data-profile="composer-footer"]` | Terms, switch, and Post action area |

### Useful attribute patterns

| Pattern | Use |
| --- | --- |
| `[aria-selected="true"]` | Currently selected tab |
| `[aria-pressed="true"]` | Pressed toolbar or like button |
| `button[aria-label="Comments"]` | Comment action |
| `button[aria-label="Share"]` | Share action |
| `button[aria-label^="Scroll popular creations"]` | Both Popular Creations arrows |
| `img[src*="btn_pixel_plate"]` | Pixel plate behind dashboard buttons |
| `img[src*="pixel_arrow.webp"]` | Pixel arrow image |
| `img[src*="paper-tab.webp"]` | Paper plate behind About icons |
| `input[type="checkbox"] + div` | Visual track after a custom checkbox |
| `[data-placeholder]::before` | Editor placeholder pseudo-element |

Attribute matching operators:

```css
[attr="exact value"]   /* exact match */
[attr^="starts with"]  /* begins with */
[attr$="ends with"]    /* ends with */
[attr*="contains"]     /* contains text */
```

---

## Profile CSS Troubleshooting

### If the safety checker reports incomplete CSS

1. Look at the end of the CSS first. An abrupt ending often identifies the broken rule.
2. Search for a property with no value, such as `background-color:` followed by `}` or the end of the file.
3. Check that every opening `{` has a closing `}`.
4. Check that comments contain both `/*` and `*/`.
5. Check that every quoted `url("...")` has a closing quote and parenthesis.
6. Remove only the newest block temporarily and preview again. Keep the original draft intact.

```css
/* Broken: missing value */
.card { background-color: }

/* Broken: missing closing brace */
.card {
  color: #fff;

/* Broken: unfinished URL */
.frame { background-image: url("frame.png; }

/* Valid */
.card {
  color: #fff;
  background-color: #231d18;
}
```

### Final profile test checklist

- Test desktop and a verified viewport at or below `767px`.
- Check every main tab and every About Me icon tab.
- Check Write a Post while empty, focused, and containing text.
- Check Public, Notify followers, the switch, and the Post button.
- Check SEE ALL, both carousel arrows, comment, share, and like states.
- Confirm that avatar art does not cover the remove button, level, or streak badge.
- Confirm that decorative layers do not block clicks.
- Confirm that portraits and gallery covers are not caught by broad image filters.
- Preview, save, and publish as separate deliberate steps.

---

# Part III — Shared Animations for Laboratory and Profile Themes

CSS animation mechanics and @keyframes work in both editors. The visual effect can stay the same; only the element that carries the pseudo-element may differ. The collection below remains unchanged and is now grouped at the end of the handbook.

> The existing full-page examples use html::before and html::after, so the same snippet can run from either editor. For a component-scoped, scrollable foreground layer, use the final shared firefly/star recipe in this section.

## Background Effects

### Animated Fireshine

Create an animated fire effect at the bottom of the screen.

<img src="./images/background-Fireshine.png" alt="Theme preview">

```css
html, body, #app, main {
  background-color: #0d0505 !important;
}

html::after {
  content: "";
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100vw;
  height: 35vh; /* How high the fire should reach */
  pointer-events: none;
  z-index: 1;
  
  background: linear-gradient(to top, rgba(242, 76, 0, 0.35), rgba(242, 153, 0, 0.15), transparent);
  filter: blur(8px);
  
  animation: lorebaryFire 0.15s ease-in-out infinite alternate;
}

@keyframes lorebaryFire {
  0% {
    transform: scaleY(1);
    opacity: 0.85;
  }
  100% {
    transform: scaleY(1.12) scaleX(1.01);
    opacity: 1;
  }
}

div[class*="chat"], div[class*="message"], .messages-container {
  position: relative;
  z-index: 5 !important;
}
```

---

### Animated Rain

Create a gentle animated rain effect as a background.

<img src="./images/background-Rain.png" alt="Theme preview">

```css
html, body, #app, main {
  background-color: #06080c !important;
  position: relative;
}

html::before {
  content: "";
  position: fixed;
  top: -30%;
  left: 0;
  width: 100vw;
  height: 160vh;
  pointer-events: none;
  z-index: 1;
  opacity: 0.12; /* Brightness of first layer */

  background: conic-gradient(from 180deg at 50% 50%, 
    transparent 0deg, 
    rgba(255, 255, 255, 0.5) 0.5deg, 
    transparent 1deg
  );
  background-size: 50px 220px;

  animation: gentleSummerRain1 1.2s linear infinite !important;
}

html::after {
  content: "";
  position: fixed;
  top: -30%;
  left: 0;
  width: 100vw;
  height: 160vh;
  pointer-events: none;
  z-index: 1;
  opacity: 0.10;

  background: conic-gradient(from 180deg at 50% 50%, 
    transparent 0deg, 
    rgba(255, 255, 255, 0.5) 0.5deg, 
    transparent 1deg
  );
  background-size: 45px 240px;

  animation: gentleSummerRain2 1.1s linear infinite !important;
}

@keyframes gentleSummerRain1 {
  0% {
    transform: translateY(0px);
    background-position: 0px 0px;
  }
  100% {
    transform: translateY(220px);
    background-position: 0px 440px;
  }
}

@keyframes gentleSummerRain2 {
  0% {
    transform: translateY(0px);
    background-position: 25px 0px;
  }
  100% {
    transform: translateY(240px);
    background-position: 25px 480px;
  }
}

div[class*="chat"], div[class*="message"], .messages-container, .chat-layout {
  position: relative;
  z-index: 5 !important;
}
```

---

### Animated Fog

Create a gentle fog over the whole screen

<img src="./images/animated-fog.png" alt="Theme preview">

```css
html, body, #app, main {
    background-color: #0b0d11 !important; /* Dark blue-gray as base */
    position: relative;
    overflow: hidden;
}

html::before {
    content: "" !important;
    position: fixed !important;
    top: -20%;
    left: -20%;
    width: 140vw;
    height: 140vh;
    pointer-events: none;
    z-index: 1 !important;
    opacity: 0.18; 

    background-image: 
        radial-gradient(circle at 30% 40%, rgba(200, 210, 220, 0.4) 0%, transparent 60%),
        radial-gradient(circle at 70% 60%, rgba(180, 195, 210, 0.3) 0%, transparent 70%);
    filter: blur(40px);
    animation: laboratoryFogMoving1 25s ease-in-out infinite alternate !important;
}

html::after {
    content: "" !important;
    position: fixed !important;
    top: -30%;
    left: -30%;
    width: 160vw;
    height: 160vh;
    pointer-events: none;
    z-index: 2 !important;
    opacity: 0.12;

    background-image: 
        radial-gradient(circle at 50% 50%, rgba(220, 225, 235, 0.3) 0%, transparent 65%),
        radial-gradient(circle at 20% 80%, rgba(160, 175, 190, 0.2) 0%, transparent 55%);
    filter: blur(60px);
    animation: laboratoryFogMoving2 35s ease-in-out infinite alternate !important;
}

@keyframes laboratoryFogMoving1 {
    0% {
        transform: translate(0px, 0px) scale(1) rotate(0deg);
    }
    50% {
        transform: translate(40px, 30px) scale(1.1) rotate(3deg);
    }
    100% {
        transform: translate(-20px, 50px) scale(0.95) rotate(-2deg);
    }
}

@keyframes laboratoryFogMoving2 {
    0% {
        transform: translate(0px, 0px) scale(1) rotate(0deg);
    }
    50% {
        transform: translate(-50px, 40px) scale(1.05) rotate(-4deg);
    }
    100% {
        transform: translate(30px, -20px) scale(1) rotate(2deg);
    }
}

div[class*="chat"], div[class*="message"], .messages-container, .chat-layout {
    position: relative;
    z-index: 5 !important;
}
```

---

### Animated Snow

Let gentle snow fall in the background.

<img src="./images/animated-snow.png" alt="Theme preview">

```css
html, body, #app, main {
    background-color: #060810 !important;
    position: relative;
    overflow: hidden;
}

html::before {
    content: "" !important;
    position: fixed !important;
    top: -10%;
    left: -10%;
    width: 120vw;
    height: 120vh;
    pointer-events: none;
    z-index: 1 !important;
    opacity: 0.22;
    background-image: 
        radial-gradient(circle, #ffffff 10%, transparent 11%),
        radial-gradient(circle, #ffffff 7%, transparent 8%),
        radial-gradient(circle, #ffffff 9%, transparent 10%),
        radial-gradient(circle, #ffffff 6%, transparent 7%);
    background-size: 140px 140px; 
    background-position: 13px 27px, 89px 113px, 47px 71px, 119px 43px;

    animation: 
        endlessSnow1 22s linear infinite,
        snowWobble1 7s ease-in-out infinite alternate !important;
}

html::after {
    content: "" !important;
    position: fixed !important;
    top: -10%;
    left: -10%;
    width: 120vw;
    height: 120vh;
    pointer-events: none;
    z-index: 2 !important;
    opacity: 0.14;
    background-image: 
        radial-gradient(circle, #ffffff 6%, transparent 7%),
        radial-gradient(circle, #ffffff 4%, transparent 5%),
        radial-gradient(circle, #ffffff 5%, transparent 6%),
        radial-gradient(circle, #ffffff 3%, transparent 4%);
    background-size: 110px 110px;
    background-position: 7px 83px, 53px 19px, 97px 61px, 29px 101px;

    animation: 
        endlessSnow2 34s linear infinite,
        snowWobble2 11s ease-in-out infinite alternate !important;
}

@keyframes endlessSnow1 {
    0% { 
        background-position: 13px 27px, 89px 113px, 47px 71px, 119px 43px; 
    }
    100% { 
        background-position: 13px 447px, 89px 533px, 47px 491px, 119px 463px; 
    }
}

@keyframes endlessSnow2 {
    0% { 
        background-position: 7px 83px, 53px 19px, 97px 61px, 29px 101px; 
    }
    100% { 
        background-position: 7px 413px, 53px 349px, 97px 391px, 29px 431px; 
    }
}

@keyframes snowWobble1 {
    0% { transform: translateX(0px) rotate(0deg) scale(1); }
    50% { transform: translateX(30px) rotate(1deg) scale(1.04); }
    100% { transform: translateX(-20px) rotate(-1deg) scale(0.96); }
}

@keyframes snowWobble2 {
    0% { transform: translateX(15px) rotate(0deg); }
    100% { transform: translateX(-35px) rotate(2deg); }
}

div[class*="chat"], div[class*="message"], .messages-container, .chat-layout {
    position: relative;
    z-index: 5 !important;
}
```

---

### Animated Fireflies

Let fireflies fly through your screen

<img src="./images/animated-fireflies.png" alt="Theme preview">

```css
html::before,
html::after {
  content: "" !important;
  position: fixed !important;
  inset: 0;
  width: 100vw;
  height: 100vh;
  height: 100dvh;
  pointer-events: none;
  z-index: 1 !important;
  background-repeat: repeat;
  will-change: background-position, opacity;
}

html::before {
  background-image:
    radial-gradient(circle, rgba(204,255,51,1) 0 1px, rgba(204,255,51,.32) 2px, transparent 7px),
    radial-gradient(circle, rgba(175,255,40,.95) 0 1px, rgba(175,255,40,.20) 2px, transparent 6px),
    radial-gradient(circle, rgba(220,255,80,.90) 0 1px, rgba(220,255,80,.26) 3px, transparent 8px),
    radial-gradient(circle, rgba(204,255,51,.82) 0 1px, rgba(204,255,51,.14) 2px, transparent 5px);
  background-size: 277px 331px, 349px 283px, 421px 367px, 313px 397px;
  background-position: 43px 287px, 213px 161px, 127px 343px, 267px 119px;
  animation:
    fireflyDriftA 43s linear infinite,
    fireflyPulseA 7.4s ease-in-out infinite !important;
  animation-delay: -17s, -2.6s !important;
}

html::after {
  background-image:
    radial-gradient(circle, rgba(255,244,120,.92) 0 1px, rgba(255,244,120,.22) 2px, transparent 7px),
    radial-gradient(circle, rgba(167,255,67,.86) 0 1px, rgba(167,255,67,.16) 3px, transparent 6px),
    radial-gradient(circle, rgba(224,255,137,.76) 0 1px, rgba(224,255,137,.12) 2px, transparent 5px);
  background-size: 389px 457px, 293px 419px, 463px 347px;
  background-position: 319px 391px, 91px 247px, 241px 79px;
  animation:
    fireflyDriftB 58s linear infinite,
    fireflyPulseB 10.8s ease-in-out infinite !important;
  animation-delay: -31s, -7.1s !important;
}

@keyframes fireflyDriftA {
  0% {
    background-position: 43px 287px, 213px 161px, 127px 343px, 267px 119px;
  }
  36% {
    background-position: 72px 91px, 187px -31px, 158px 172px, 239px -102px;
  }
  71% {
    background-position: 31px -142px, 249px -271px, 109px -79px, 296px -314px;
  }
  100% {
    background-position: 86px -389px, 169px -497px, 181px -286px, 231px -541px;
  }
}

@keyframes fireflyDriftB {
  0% {
    background-position: 319px 391px, 91px 247px, 241px 79px;
  }
  44% {
    background-position: 281px 103px, 128px -17px, 207px -186px;
  }
  76% {
    background-position: 337px -151px, 73px -273px, 269px -397px;
  }
  100% {
    background-position: 263px -487px, 146px -612px, 219px -731px;
  }
}

@keyframes fireflyPulseA {
  0%, 100% { opacity: .12; }
  18% { opacity: .42; }
  37% { opacity: .20; }
  61% { opacity: .50; }
  79% { opacity: .16; }
}

@keyframes fireflyPulseB {
  0%, 100% { opacity: .08; }
  26% { opacity: .30; }
  49% { opacity: .12; }
  73% { opacity: .36; }
  89% { opacity: .10; }
}
```

---

### Animated Dustparticle

Let dust hover across the screen

```css
html, body, #app, main {
    background-color: #020204 !important; 
    position: relative;
    overflow: hidden;
}

html::before {
    content: "" !important;
    position: fixed !important;
    width: 1.5px !important;
    height: 1.5px !important;
    top: 0;
    left: 0;
    background: transparent;
    pointer-events: none;
    z-index: 2 !important;
    box-shadow: 
        120px 240px #ffffff,   340px 80px rgba(255,255,255,0.8),  560px 420px #ffffff,
        780px 150px rgba(255,255,255,0.9),  910px 620px #ffffff,  210px 710px rgba(255,255,255,0.7),
        430px 890px #ffffff,   850px 330px rgba(255,255,255,0.8),  620px 780px #ffffff,
        150px 520px rgba(255,255,255,0.9),  950px 210px #ffffff,  710px 920px rgba(255,255,255,0.7),
        1100px 110px #ffffff,  1250px 480px rgba(255,255,255,0.8), 1380px 750px #ffffff,
        1520px 310px rgba(255,255,255,0.9), 1680px 820px #ffffff, 1850px 190px rgba(255,255,255,0.7),
        50vw 25vh #ffffff,     85vw 60vh rgba(255,255,255,0.9),   15vw 75vh #ffffff;

    animation: naturalCosmosTwinkle 4s ease-in-out infinite alternate !important;
}

html::after {
    content: "" !important;
    position: fixed !important;
    top: -30%;
    left: -30%;
    width: 160vw;
    height: 160vh;
    pointer-events: none;
    z-index: 1 !important;
    opacity: 0.22;

    background-image: 
        radial-gradient(circle at 25% 25%, rgba(138, 43, 226, 0.3) 0%, transparent 55%),  
        radial-gradient(circle at 75% 65%, rgba(0, 102, 204, 0.25) 0%, transparent 60%);  
    
    filter: blur(60px);
    animation: cosmosNebulaMove 50s ease-in-out infinite alternate !important;
}

@keyframes naturalCosmosTwinkle {
    0% {
        opacity: 0.25;
        transform: scale(0.98);
    }
    100% {
        opacity: 0.75;
        transform: scale(1.02); 
    }
}

/* --- ANIMATION: NEBULA SWIRL --- */
@keyframes cosmosNebulaMove {
    0% { transform: translate(0px, 0px) rotate(0deg); }
    100% { transform: translate(30px, 40px) rotate(1deg); }
}

div[class*="chat"], div[class*="message"], .messages-container, .chat-layout {
    position: relative;
    z-index: 5 !important;
}
```

---

### Animated Stars

Let stars twinkle in your background

<img src="./images/animated-sterne.png" alt="Theme preview">

```css
html, body, #app, main {
    background-color: #020204 !important; 
    position: relative;
    overflow: hidden;
}

html::before {
    content: "" !important;
    position: fixed !important;
    width: 1.2px !important;
    height: 1.2px !important;
    top: 0;
    left: 0;
    background: transparent;
    pointer-events: none;
    z-index: 2 !important;
    border-radius: 50% !important;

    box-shadow: 
        120px 240px #ffffff,   340px 80px rgba(255,255,255,0.4),  560px 420px #ffffff,
        780px 150px rgba(255,255,255,0.7),  910px 620px #ffffff,  210px 710px rgba(255,255,255,0.3),
        430px 890px #ffffff,   850px 330px rgba(255,255,255,0.5),  620px 780px #ffffff,
        150px 520px rgba(255,255,255,0.6),  950px 210px #ffffff,  710px 920px rgba(255,255,255,0.4),
        1100px 110px #ffffff,  1250px 480px rgba(255,255,255,0.5), 1380px 750px #ffffff,
        1520px 310px rgba(255,255,255,0.7), 1680px 820px #ffffff, 1850px 190px rgba(255,255,255,0.3),
        50vw 25vh rgba(255,255,255,0.8),     85vw 60vh #ffffff,   15vw 75vh rgba(255,255,255,0.5),
        250px 180px rgba(255,255,255,0.4), 680px 50px #ffffff,   1150px 800px rgba(255,255,255,0.5),
        1420px 910px #ffffff,  1710px 430px rgba(255,255,255,0.6),
        250px 350px 0 1.2px #ffffff,        
        1450px 180px 0 1.5px #ffffff,       
        650px 600px 0 1.3px rgba(255,255,255,0.9), 
        80vw 80vh 0 1.4px #ffffff,          
        35vw 75vh 0 1.2px rgba(255,255,255,0.9);   

    animation: staticCosmosTwinkle 5s ease-in-out infinite alternate !important;
}

html::after {
    content: "" !important;
    position: fixed !important;
    top: -30%;
    left: -30%;
    width: 160vw;
    height: 160vh;
    pointer-events: none;
    z-index: 1 !important;
    opacity: 0.20;

    background-image: 
        radial-gradient(circle at 25% 25%, rgba(138, 43, 226, 0.3) 0%, transparent 55%),  
        radial-gradient(circle at 75% 65%, rgba(0, 102, 204, 0.25) 0%, transparent 60%);  
    
    filter: blur(60px);
    animation: cosmosNebulaMove 60s ease-in-out infinite alternate !important;
}

@keyframes staticCosmosTwinkle {
    0% { opacity: 0.3; }
    100% { opacity: 0.85; }
}

@keyframes cosmosNebulaMove {
    0% { transform: translate(0px, 0px) rotate(0deg); }
    100% { transform: translate(20px, 30px) rotate(0.5deg); }
}

div[class*="chat"], div[class*="message"], .messages-container, .chat-layout {
    position: relative;
    z-index: 5 !important;
}
```

---

### Animated Sunshine Underwater

Sunshine under water with small rising bubbles

<img src="./images/animated-sunshine and water.png" alt="Theme preview">

```css
html, body, #app, main {
    background-color: #080a10 !important; 
    position: relative;
    overflow: hidden;
}

html::before {
    content: "" !important;
    position: fixed !important;
    bottom: -20% !important;
    left: -10vw !important;
    width: 120vw !important;
    height: 140vh !important;
    pointer-events: none !important;
    z-index: 1 !important;
    opacity: 0.35;

    background-image: 
        radial-gradient(circle at 120px 280px, #ffffff 1px, transparent 2px),
        radial-gradient(circle at 120px 280px, transparent 2px, rgba(255, 255, 255, 0.3) 3px, transparent 4px),
        radial-gradient(circle at 380px 140px, #ffffff 0.5px, transparent 1.5px),
        radial-gradient(circle at 380px 140px, transparent 1.5px, rgba(255, 255, 255, 0.25) 2.5px, transparent 3.5px);
    
    background-size: 500px 500px, 700px 700px !important;
    background-repeat: repeat !important;

    animation: 
        bubblesUltraSlowRise 65s linear infinite,
        bubblesUltraSlowWobble 9s ease-in-out infinite alternate !important;
}

html::after {
    content: "" !important;
    position: fixed !important;
    top: -20% !important; 
    left: 10% !important; 
    width: 100vw !important;
    height: 70vh !important; 
    pointer-events: none !important;
    z-index: 2 !important; 
    background: linear-gradient(135deg, 
        rgba(255, 255, 255, 0.22) 0%, 
        rgba(255, 255, 255, 0.12) 15%, 
        rgba(255, 255, 255, 0.04) 40%, 
        transparent 70%
    );

    filter: blur(45px) !important;
    animation: holyLightGlow 8s ease-in-out infinite alternate !important;
    transform-origin: top center !important;
}

@keyframes bubblesUltraSlowRise {
    0% { background-position: 0px 0px, 200px 0px; }
    100% { background-position: 0px -3500px, 200px -3500px; }
}

@keyframes bubblesUltraSlowWobble {
    0% { transform: translateX(0px); }
    50% { transform: translateX(20px); }
    100% { transform: translateX(-15px); }
}

@keyframes holyLightGlow {
    0% {
        opacity: 0.40; 
        transform: scale(0.95) rotate(0deg);
    }
    50% {
        opacity: 0.85; 
        transform: scale(1.05) rotate(1deg); 
    }
    100% {
        opacity: 0.50;
        transform: scale(0.98) rotate(-0.5deg);
    }
}

div[class*="chat"], div[class*="message"], .messages-container, .chat-layout {
    position: relative;
    z-index: 5 !important;
}
```

---

### Animated Soft Godly Light

Creates a soft shine at the top of the screen.

<img src="./images/animated-soft shine top.png" alt="Theme preview">

```css
html, body, #app, main {
    background-color: #06080c !important; 
    position: relative;
    overflow: hidden;
}

html::after {
    content: "" !important;
    position: fixed !important;
    top: -25% !important; 
    left: 0 !important;
    right: 0 !important;
    margin: 0 auto !important; 
    width: 85vw !important; 
    height: 80vh !important; 
    pointer-events: none !important;
    z-index: 1 !important; 
    background: linear-gradient(to bottom, 
        rgba(255, 210, 120, 0.26) 0%, 
        rgba(255, 185, 80, 0.16) 20%, 
        rgba(230, 150, 50, 0.05) 50%, 
        transparent 85%
    );

    filter: blur(55px) !important;
    animation: holyGoldenGlow 9s ease-in-out infinite alternate !important;
    transform-origin: top center !important;
}

@keyframes holyGoldenGlow {
    0% {
        opacity: 0.45; 
        transform: scaleX(0.92) scaleY(0.96); 
    }
    50% {
        transform: scaleX(1.06) scaleY(1.03); 
    }
    100% {
        opacity: 0.55;
        transform: scaleX(0.96) scaleY(0.98);
    }
}

div[class*="chat"], div[class*="message"], .messages-container, .chat-layout {
    position: relative;
    z-index: 5 !important;
}
```

---

## Shared Scrollable Foreground Fireflies and Stars

The `@keyframes` and gradient particles are identical in Laboratory and Profile Themes. Only the two mounting selectors differ. Use `position: absolute`, not `fixed`, when the particles should move with the themed content while scrolling.

```css
/* The scrolling container in each theme area. */
.lab-theme-scope,
.profile-theme-scope[data-profile="scope"] {
  position: relative;
}

/* The same visual layer is mounted on both theme roots. */
.lab-theme-scope::before,
.profile-theme-scope[data-profile="scope"]::before {
  content: "";
  position: absolute;
  inset: 0;
  z-index: 40;
  pointer-events: none;
  background:
    radial-gradient(circle, #fff6a9 0 18%, #d7ff75 24%, transparent 65%)
      12% 18% / 10px 10px no-repeat,
    radial-gradient(circle, #fff8bf 0 16%, #b9ff75 26%, transparent 67%)
      72% 42% / 8px 8px no-repeat,
    radial-gradient(circle, #ffffff 0 15%, #ffe89a 25%, transparent 68%)
      88% 74% / 7px 7px no-repeat;
  animation: shared-particle-drift 7s ease-in-out infinite alternate,
             shared-particle-blink 2.4s ease-in-out infinite;
}

@keyframes shared-particle-drift {
  from { transform: translate3d(-5px, 0, 0); }
  to   { transform: translate3d(8px, -12px, 0); }
}

@keyframes shared-particle-blink {
  0%, 100% { opacity: .35; filter: brightness(.9); }
  45%      { opacity: 1; filter: brightness(1.6); }
}

@media (prefers-reduced-motion: reduce) {
  .lab-theme-scope::before,
  .profile-theme-scope[data-profile="scope"]::before {
    animation: none !important;
    opacity: .65;
  }
}
```

Keep the particle count and size modest on mobile. `pointer-events: none` prevents the foreground layer from blocking controls. `transform`, `filter`, and `opacity` can create stacking contexts, so check that menus and dialogs still appear above the decoration.

### Reusing any animation in both editors

1. Keep the visual properties and `@keyframes` unchanged.
2. Replace the original mounting selector with both theme roots, separated by a comma.
3. Use `absolute` for an effect that scrolls with the themed content.
4. Use `fixed` only when an effect should remain attached to the viewport.
5. Add a `prefers-reduced-motion` rule for moving effects.

---

## Changelog

- **2026-10-10:** Added Part II for Profile Themes with example images, typography, sticker positioning, status-card layout, and before/after comparisons. Moved the animation collection to Part III and added a shared Laboratory/Profile foreground-particle recipe.
- **2026-07-17:** Previous Laboratory / Chat Themes guide update.

**Last Updated:** 2026-10-10
