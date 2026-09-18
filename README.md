# Printer wall

A self-contained static webpage displaying all five printer Device pages: 10.6.3.10, 10.6.3.11, 10.6.3.12, 10.6.3.13, and 10.6.3.40. No build, dependencies, account, or API key is required.

## Publish on GitHub Pages

1. Create a GitHub repository or use an existing one.
2. Upload `index.html` to the repository root and commit it. The README is optional.
3. Under **Settings → Pages**, select **Deploy from a branch**, select your branch (usually `main`) and **/(root)**, then save.
4. Open the published URL shown by GitHub after deployment completes.
5. Use it on a computer connected to the printer network or its VPN. Allow local-network access if prompted.

The site has not been published for you. GitHub only serves the dashboard; your browser connects directly to the printers. Publishing this file does not make the printers publicly accessible, but anyone who can read the page source can see the listed private addresses.

## Controls

- Five embedded views, with three columns on wide displays, two on medium displays, and one on phones. A two-column option provides larger panels.
- Fit and individual zoom settings, with scrollable panels.
- Per-printer refresh, Open in a new tab, and Expand where browser full screen is available.
- Refresh all and optional timed refresh. Refresh returns to `/#/device`. Timed refresh pauses while the dashboard tab is hidden and starts off on each visit.

## Connection requirements and limitations

These are real embedded websites, not copies of the screenshot. Their content is not simulated. Live connectivity and printer embedding compatibility must be checked on your own network.

GitHub Pages supports HTTPS. The printer URLs use HTTP. Current Chrome supports permission-gated local-network access, including a mixed-content exception for private IP addresses. Other browsers, versions, managed policies, or privacy settings may block these frames. The screenshot appears to use Brave; its behavior may differ from Chrome, so test current Chrome if Brave blocks a panel. Do not disable browser security globally.

Even with network permission, printers can prevent embedding with `X-Frame-Options` or a Content Security Policy `frame-ancestors` rule. A static GitHub Pages site cannot bypass that. If Open works but embedding fails, ask IT to inspect these headers. If embedding cannot be enabled appropriately, use separate tabs or ask IT for an internal dashboard/proxy configured for these printers. An internal HTTP dashboard avoids HTTPS-to-HTTP mixed content but does not bypass embedding restrictions. A proxy cannot run on GitHub Pages itself.

The dashboard cannot inspect a cross-origin printer page, read toner levels, confirm successful loading, or distinguish a blocked frame from an offline printer. “Requested” is a refresh-request timestamp, not proof that a printer is online. The parent page intentionally makes no online/offline claims.

If a printer uses another page path, edit its URL construction near `const url` in `index.html`. All five addresses are in the `addresses` array. Fit uses a 1020 × 650 content area based on the supplied screenshot; use zoom and scroll if the printer layout differs.

References:
- https://developer.chrome.com/blog/local-network-access
- https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/X-Frame-Options
