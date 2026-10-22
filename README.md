# Git Client Preview website

Public product, support, and privacy pages for Git Client Preview, a native macOS Git application developed by Shawn Moore.

- Website: https://shawnmoore.github.io/git-client-preview/
- Support: https://shawnmoore.github.io/git-client-preview/support/
- Privacy: https://shawnmoore.github.io/git-client-preview/privacy/
- Public issue tracker: https://github.com/ShawnMoore/git-client-preview/issues

This repository contains only the website and public issue templates. The application's source repository is separate.

## Edit and preview

Edit the HTML files in `public/` and the shared stylesheet in `public/assets/styles.css`. There is no JavaScript, package installation, or build step. Navigation and FAQs work without scripts. All visual assets are local.

From this directory:

```sh
python3 -m http.server 4173 --bind 127.0.0.1 --directory public
```

Open http://127.0.0.1:4173/. Stop the server with Control-C.

The repository screenshot is an app test snapshot with demonstration data. Its source in the app project is `GitClientTests/__Snapshots__/BranchPickerFlowSnapshotTests/chosenColors.2-navigator-and-history-light.png`. The icon is the app's current default icon. Review image content before replacing either with screenshots from real repositories.

## GitHub Pages

In the repository's Settings → Pages, select **GitHub Actions** as the publishing source. `.github/workflows/pages.yml` uploads only `public/` and deploys it when those files change on `main`, or when the workflow is run manually. The issue forms are not part of the uploaded website.

## GitHub OAuth registration

For the app's existing device-code sign-in implementation:

| Field | Value |
| --- | --- |
| Application name | Git Client Preview |
| Homepage URL | https://shawnmoore.github.io/git-client-preview/ |
| Authorization callback URL | https://shawnmoore.github.io/git-client-preview/oauth/callback/ |
| Enable Device Flow | Enabled |
| Expire user access tokens | Enabled |

The callback page is informational. The implemented device flow completes through GitHub and the native app; this static site does not receive or exchange access tokens. Do not add OAuth credentials to the website. The public Client ID belongs in the native app's `GitClientIdentity.SignIn.gitHubClientID` setting.

## Content maintenance

- Support currently uses public GitHub Issues. There is no support email or private support intake form.
- The privacy policy describes the current preview's implementation, including local app storage, Keychain credentials, service connections, diagnostics, and GitHub Pages hosting logs. Review it whenever these behaviors change, and update its date.
- Update the product name throughout the HTML and this README when branding is finalized. If the repository or URL changes, also update canonical and social URLs, `robots.txt`, `sitemap.xml`, issue links, the 404 page, and OAuth registration.
- The privacy page does not promise automatic deletion of repositories, caches, recovery files, or backups on sign-out or uninstall.
