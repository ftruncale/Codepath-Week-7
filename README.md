# Project 7 - WordPress Pentesting

Time spent: **X** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds (CVE-2017-6817)
  - [ ] Summary:
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.13
  - [ ] GIF Walkthrough: ![Dunno why this didn't load](/images/youtubeXSS.gif 'instructions')
  - [ ] Steps to recreate:
    - On a post or page, embed a YouTube url with the format of:
      `[embed src='https://youtube.com/embed/whateverPAYLOAD'][/embed]`
    - Requires usage of escape characters to avoid filtering.
    - Ex: `[embed src='https://youtube.com/embed/whatever\x3csvg onload=alert(1)\x3e'][/embed]`
    - View the page with the payload
  - [ ] Affected source code:
    - [embed.php](https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8)
2. Large File Upload Error XSS (CVE-2017-9061)
  - [ ] Summary:
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.15
  - [ ] GIF Walkthrough: ![Dunno why this didn't load](/images/largefileXSS.gif 'instructions')
  - [ ] Steps to recreate:
    - Go to the wp-admin add media page `../wp-admin/media-new.php`
    - Upload a 20MB or larger file with the filename as the payload (Example `thanks nasa<img src=x onerror=alert(1)>.png`)
  - [ ] Affected source code:
    - [handlers.js](https://github.com/WordPress/WordPress/commit/8c7ea71edbbffca5d9766b7bea7c7f3722ffafa6))
3. Nav Menu Title Cross-Site Scripting (XSS) (CVE-2015-5733)
  - [ ] Summary:
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.4
  - [ ] GIF Walkthrough: ![Dunno why this didn't load](/images/widgettitleXSS.gif 'instructions')
  - [ ] Steps to recreate:
    - Navigate to the widget page in wp-admin
    - Create a new text widget, with any title. Second entry-box is for payload.
    - Navigate to any page on the host, widget loads automatically and payload runs.
  - [ ] Affected source code:
    - [default-widgets.php](https://core.trac.wordpress.org/changeset/33529)
4.  Authenticated Cross-Site Scripting (XSS) via Media File Metadata (CVE-2017-6814)
  - [ ] Summary:
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.13
  - [ ] GIF Walkthrough: ![Dunno why this didn't load](/images/mediametadata.gif 'instructions')
  - [ ] Steps to recreate:
    - Add an mp3 with the title metadata set to `<noscript><script>alert(1);</script>`
    - Insert a playlist containing the mp3 into a post
    - View the page
  - [ ] Affected source code:
    - [media.php](https://github.com/WordPress/WordPress/commit/28f838ca3ee205b6f39cd2bf23eb4e5f52796bd7)

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [2017] [Francesca]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
