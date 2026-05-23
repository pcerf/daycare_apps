# Daycare Apps

A collection of single-file web applications for daycare / Kita management, designed to run in your browser. Just click the links below to use the App directly in your browser.

## Apps

Just click the links below to use the App directly in your browser.

- [notbetreuung.html](https://pcerf.github.io/daycare_apps/notbetreuung.html) — Notbetreuungs-Planer (German): kindergarten emergency-care planner with structured email queries to parents, Outlook `.msg` import of replies, drag-and-drop weekly scheduling, fairness-weighted auto-allocation across cumulative care hours, reusable standard plans for recurring scenarios, history tracking, parent-notification mails for assignments and refusals, and fully editable email templates with placeholder substitution.

## Privacy and Security

These apps are intended to run entirely in the user's browser. However, while I took great care to minimize interaction with external services, **some apps may load third-party libraries from CDNs on demand** or **contact external servers**, which means network requests are made and standard browser information is exposed to those servers. I have documented this to the best of my knowledge per app below (see [Acknowledgments and External Services](#acknowledgments-and-external-services) below). **You are responsible for reviewing the code yourself before use.** Use at your own risk.

## Acknowledgments and External Services

In this section I list which apps load third-party libraries from CDNs on demand or contact external servers and which don't. I might have made mistakes in compiling this list. **Hence, this list is not guaranteed to be complete. You are responsible for reviewing the code yourself before use. Use at your own risk.**

### notbetreuung.html
notbetreuung.html does not load any external libraries at runtime and does not contact external servers during runtime. All state lives in the browser's session storage; the app's only data export is a human-readable Markdown file the user saves locally. Parent notifications and inquiry mails are opened through the user's local mail client via `mailto:` links — the app itself never transmits these.

## License

MIT License

Copyright (c) 2026 Pascal Cerfontaine

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## Disclaimer

This software is provided as-is with no warranties. The authors are not responsible for any damages, data loss, or privacy issues arising from the use of these applications. Users should independently verify that the applications meet their security and privacy requirements before use.
