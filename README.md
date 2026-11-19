# Week 3 Password Recovery with John and NetworkWalks Tools

Michael Tostao Paul | NetworkWalks | Batch B084 | 19 November 2026

I recovered passwords from two instructor-provided training PDFs and verified both by opening the original files. Work was limited to the supplied lab files.

## Results

| Module | Target | Password | Result |
| --- | --- | --- | --- |
| PM1 | My Locked PDF1.pdf | `good-luck` | Recovered with John on Windows and Johnny on Kali; PDF opening confirmed |
| PM2 | My Locked PDF1 (for NW Tools Lab WK3-PM2).pdf | `password1` | Recovered with NetworkWalks tools; PDF opening confirmed |

## Report

[Read the report](Michael_B084_Week3_Report.pdf) or [download the editable version](Michael_B084_Week3_Report.docx).

## PM1 steps

1. Verified John 1.9.0-jumbo-1 on Windows.
2. Extracted the PDF verification data using `pdf2john.pl` and Strawberry Perl.
3. Removed the filename prefix so `hash1.txt` started with `$pdf$` and retained the complete hash on one line.
4. Ran John with `--format=pdf` and the bundled `password.lst`.
5. Displayed the result with `--show --format=pdf` and opened the PDF with the recovered password.
6. Installed Johnny in Kali using `sudo apt install johnny`, configured `/usr/sbin/john`, and loaded `hash1.txt` through Open password file (PASSWD format).
7. Started a new attack. Johnny displayed the same recovered password.

![John recovery result](screenshots/01_PM1_John_Result.png)

## Troubleshooting

Windows Johnny failed with Bad Image error 0xc0000020 involving bundled DLLs. PowerShell extraction succeeded after Windows Explorer extraction errors, but it did not solve the GUI startup error. I completed the GUI task with Johnny in Kali instead. The Windows DLL cause remains unresolved.

John initially reported no password hashes loaded. After cleaning the filename prefix and explicitly selecting PDF format, it loaded the hash successfully.

The Kali file dialog extended beyond the visible VM window. Switching VirtualBox to full screen allowed me to select the file.

![Johnny configured in Kali](screenshots/04_Johnny_John_Path.png)
![Hash loaded in Johnny](screenshots/05_Johnny_Hash_Loaded.png)

## PM2 steps

1. Selected the dedicated PM2 PDF in the [Hash Calculator](https://networkwalks.com/hash-calculator/).
2. Copied the complete `$pdf$` value into the [Password Cracker](https://networkwalks.com/password-cracker/).
3. Used the built-in 100-password list. The tool found `password1` after 91 attempts.
4. Opened the original PDF with the recovered password.

![PM2 hash extraction](screenshots/06_PM2_Hash_Extraction.png)
![PM2 recovery result](screenshots/07_PM2_Password_Result.png)

## Evidence status

The opened PM1 and PM2 images are included below. The final Johnny password display was confirmed during the practical session; its screenshot is not included. The loaded-hash screenshot above is not evidence of the final Johnny recovery by itself.

![PM1 opened PDF](screenshots/09_PM1_PDF_Opened.png)
![PM2 opened PDF](screenshots/10_PM2_PDF_Opened.png)

The red-padlock image in `screenshots/11_Additional_Flag_Unassigned.png` contains a different flag. Its source PDF and recovery method have not been established, so no additional task completion is claimed.

## Scope

The optional Claude and HexStrike exercise, optional portal exercise, PDF2 and PDF3 are not claimed as completed. See the report for the documented steps and limitations.
