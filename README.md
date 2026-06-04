# Floaty Fork for LineGuide

This repository is the LineGuide-maintained fork of `kciter/Floaty`.

## Why This Fork Exists

LineGuide uses floating action menus that expand horizontally from the right edge of the screen toward the left. The upstream library is centered on vertical expansion, so we introduced a small fork to support the current product behavior without rewriting every menu immediately.

This fork is intended to be an interim solution while the app moves toward a SwiftUI-based replacement for these floating controls.

## What We Customized

The fork adds and preserves behavior needed for LineGuide's horizontal left-side menu layout:

- Support for directional expansion beyond the default vertical-only pattern.
- Left/right item placement and animation handling in the core `Floaty` implementation.
- Compatibility with the app's usage pattern where menus are configured with:
  - `verticalDirection = .left`
  - `openAnimationType = .none`

In practice, this allows the floating menu button to stay anchored near the right edge while menu items open horizontally toward the left, which fits the app's map workflows and avoids obscuring the main interaction area.

## Scope

This fork should stay intentionally narrow:

- Keep changes limited to behavior required by LineGuide.
- Avoid broad refactors unrelated to the menu-direction customization.
- Preserve upstream compatibility where practical so future upstream sync remains manageable.

## Upstream Handling

If we need fixes from `kciter/Floaty` in the future:

1. Pull changes into this fork first.
2. Reconcile them here.
3. Re-test the LineGuide horizontal menu behavior.
4. Update the app to the new fork revision only after verification.

The app should continue to depend on this fork as the single source of truth, not on a personal fork or the original upstream repository.

## Long-Term Plan

This fork is temporary. The long-term direction is to replace these UIKit/Storyboard-driven floating menus with a SwiftUI-based implementation owned directly by the LineGuide app.
