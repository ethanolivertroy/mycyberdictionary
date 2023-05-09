# Google Hacking

## Introduction

- Google Hacking was popularized by Johnny Long in 2001[^1^].
- It involves using search engines to uncover critical information, vulnerabilities, and misconfigured websites.
- This technique relies on clever search strings and operators[^3^], and it is an iterative process.

## Search Operators

### Site Operator

- The `site` operator limits searches to a single domain.
- Example: `site:megacorpone.com` (Figure 1)

### Filetype Operator

- The `filetype` (or `ext`) operator limits search results to the specified file type.
- Example: `site:megacorpone.com filetype:txt` (Figure 2)
- This query found the `robots.txt` file, which revealed a hidden PHP page (Listing 4).

### Exclude Operator

- The `-` operator can be used to exclude particular items from a search.
- Example: `site:megacorpone.com -filetype:html` (Figure 3)

### Intitle Operator

- The `intitle` operator finds pages with a specified word or phrase in the title.
- Example: `intitle:"index of" "parent directory"` (Figure 4)
- This query found misconfigured directory listings, which can reveal interesting files and sensitive information[^4^].

## Resources

- The Google Hacking Database (GHDB)[^5^] contains many creative searches that demonstrate the power of combined operators (Figure 5).
- The DorkSearch[^6^] portal provides a pre-built subset of queries and a builder tool to facilitate the search.

Mastery of these operators, combined with a keen sense of deduction, are key skills for effective search engine "hacking".

[^1^]: (Wikipedia, 2022) https://en.wikipedia.org/wiki/Google_hacking
[^2^]: (Johnny Long, Bill Gardner, Justin Brown, 2015), https://www.amazon.com/Google-Hacking-Penetration-Testers-Johnny/dp/0128029641/ref=dp_ob_image_bk
[^3^]: (Google, 2022), https://support.google.com/websearch/answer/2466433?hl=en
[^4^]: (MITRE, 2022), https://cwe.mitre.org/data/definitions/548.html
[^5^]: (OffSec, 2023), https://www.exploit-db.com/google-hacking-database
[^6^]: (DorkSearch, 2022), https://dorksearch.com/