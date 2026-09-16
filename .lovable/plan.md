# Add project list and project identity

## What will change
- Add a left-side project panel showing the active project's title and style.
- List all projects owned by the signed-in user below it.
- Let the user switch projects and create a newly named project from the panel.
- Keep the selected project's Sources, Chat, Studio, and Channels content together when switching.
- Use a compact mobile layout so the project controls remain usable on small screens.

## Technical details
- Extend the existing workspace request to return the user's project list and load a selected project.
- Share the selected project through the authenticated app layout so every existing page updates together.
- Display the analysed visual style from each project's channel profile, with a clear pending state before analysis.
- Resolve the observed sign-in page hydration mismatch while touching the authenticated shell.
- Verify project creation, switching, desktop/mobile layout, and existing navigation.
