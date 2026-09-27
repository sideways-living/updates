# Sideways Living updates

Public distribution repository for Sideways Living macOS applications.
Application source code and signing credentials do not belong here.

GitHub Pages serves feeds and release notes from docs/. GitHub Releases serves
versioned signed and notarised archives. No app update is published yet.

## Publishing an app

1. Build, Developer ID sign, notarise and staple the app in its source repository.
2. Package it without altering its signature. Create an app-specific release tag,
   for example inboxminder-1.0.0-100. Never replace an existing archive.
3. Upload the archive to a GitHub Release. Publish and verify its unauthenticated
   download before publishing a feed that references it.
4. Use Sparkle tools and the app's dedicated Ed25519 key to generate the appcast.
   Use the fixed release asset URL, never releases/latest/download.
5. Put the generated feed in docs/<app-slug>/<stable-or-beta>/appcast.xml and
   versioned release notes alongside it. Retain prior compatible feed entries.
6. Review the feed signature, archive length, version and minimum OS. Push the
   docs change, wait for Pages deployment and verify the public XML/download.
7. Test an update from an older signed build through installation and relaunch.

Private keys remain in the release Mac's Keychain with encrypted offline backup.
Do not upload tokens, credentials, mailbox data or unsigned placeholder feeds.
Each app uses its own Sparkle key; channels for the same app share that key.

Custom domain: updates.sidewayslivi.ng. Configure it in repository Settings > Pages
before switching DNS. Pages source: main branch, /docs. Require HTTPS after the
certificate is issued. Domain ownership verification is recommended in account
Settings > Pages using the exact TXT record supplied by GitHub.
