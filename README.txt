MEDIROZA GENERAL HOSPITAL - PENETRATION TEST PACKAGE
Networkwalks Internship - Batch B083, Week 4
=======================================================

CONTENTS
--------
Mediroza_Pentest_Report_Draft.docx
    Draft report covering work completed so far (recon + content
    discovery). Milestones 2-4 are not yet filled in because they
    depend on verified evidence from Milestone 1.

evidence/  (20 screenshots, numbered in chronological order)
    01-06   WHOIS, DNS (dig/host) lookups
    07-09   HTTP header checks, whatweb, early 404 responses
    10-11   nmap service/version + script scan
    12-16   gobuster directory brute-force (start to finish)
    17-18   wget attempts to retrieve candidate "report" files
    19-20   pdfinfo/exiftool tooling issues

STATUS / WHAT'S NOT DONE YET
-----------------------------
- M1 (Initial Access): NOT confirmed. The 3 downloaded files
  (pdf/report1.pdf, report2.pdf, report3.pdf) were pulled from a
  placeholder path ("FOUND/PATH" was never replaced with a real
  discovered path) and came back as text/html, not a real PDF.
  Run this to check:

      file pdf/report1.pdf pdf/report2.pdf pdf/report3.pdf

  If it says "HTML document," these are not the real deliverable.
  The gobuster scan returned HTTP 200 for almost every word tried,
  at a near-identical size (~12,000-12,280 bytes) - the server is
  likely returning a generic "soft 404" page instead of real 404s.
  Re-scan filtering out that response size (e.g. gobuster -fs <size>,
  or ffuf with a size/word filter) to surface genuinely different,
  real paths.

- M2 (crack encryption on the 3 files): not started - needs real
  PDFs first.

- M3 (salaries + shareholder details via metadata/exposure): not
  started - needs real PDFs first.

- M4 (final report): this draft covers Sections 1-6 using only
  what's actually verified; update Findings/Risk/Recommendations
  once M1-M3 produce confirmed evidence.

NEXT STEPS
----------
1. Verify file type of the 3 downloaded "PDFs" (command above).
2. Re-run content discovery with a response-size filter to cut out
   the soft-404 noise and find real candidate paths.
3. Once a genuine PDF is retrieved, confirm with `file` and
   `pdfinfo`/`exiftool` before treating it as the M1 deliverable.
4. Update the report's Findings, Risk Rating, and Recommendations
   sections with real M1-M3 results.
