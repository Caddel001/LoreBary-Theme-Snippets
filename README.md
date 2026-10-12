# LoreBary Theme Snippets

Copy-ready CSS snippets for building LoreBary **Laboratory / Chat Themes** and **Profile Themes**.

## Start Here

Open the [LoreBary CSS Quick Guide](./LoreBary%20CSS%20Quick%20Guide.md) for the complete handbook, examples, selector references, and troubleshooting notes.

## Choose the Correct Theme Area

| Theme area | Root scope | Use it for |
| --- | --- | --- |
| Laboratory / Chat Themes | `.lab-theme-scope` | Chat messages, Laboratory avatars, header, footer, LoreBary 2.5 controls, long-press menus, and chat effects |
| Profile Themes | `.profile-theme-scope` | Profile avatar frames, tabs, About Me, Write a Post, Gallery, Popular Creations, and feed posts |

The two areas use different selectors. A Laboratory snippet will usually not affect a profile page until its selector is adapted for the profile structure.

## Shared Animations

CSS animation properties and `@keyframes` work the same in both editors. The handbook keeps the animation collection at the end and shows how to mount the same effect on both `.lab-theme-scope` and `.profile-theme-scope`. Use `position: absolute` when the effect should move with the themed content while scrolling.

## Repository Structure

- [`LoreBary CSS Quick Guide.md`](./LoreBary%20CSS%20Quick%20Guide.md) — the complete handbook
- [`images/`](./images) — screenshots and preview images used by the guide
- [`images/profile/`](./images/profile) — profile-theme examples, before/after comparisons, and desktop/mobile previews

## Safe Workflow

1. Keep a copy of the current CSS.
2. Add or change one logical component at a time.
3. Preview the result on desktop and at a real mobile viewport.
4. Check hover, selected, pressed, disabled, and keyboard-focus states.
5. Save only after the preview is correct; publish only when the saved version has been verified.

## Credits

Thanks to **@harp** for the original collection of useful LoreBary snippets. 🫶🏻

## Latest Guide Update
- **2026-10-11:** Added a number of snippets from @pikachuthehedgehogtheherooftime
- **2026-10-10:** Replaced the legacy Laboratory button examples with the live-verified LoreBary 2.5 composer, toolbar, active/open states, long-press settings dialogs, and dropdown selectors.
- **2026-10-10:** Added a dedicated Profile Themes section, font recipes, sticker placement, movable status cards, example images, avatar before/after framing, desktop/mobile previews, selector references, and a shared animation section for both theme editors.
