# CSCA Trust Store

## 📄 Overview

This repository serves as a stable, auditable host for the official ICAO Master List of Country Signing Certification Authority (CSCA) certificates.

The primary purpose of this repository is to provide a reliable, direct download link for our ePassport verification service. The official ICAO distribution page is protected by a CAPTCHA and a Terms of Service agreement, which prevents automated fetching. This repository bridges that gap by storing a manually downloaded copy of the official list, allowing our application to reliably access its trust store on startup.

---

## 🛡️ Source of Truth

The file contained in this repository is a direct copy of the official Master List provided by the International Civil Aviation Organization (ICAO). The authenticity and integrity of the list itself are cryptographically guaranteed by the ICAO's digital signature within the file.

The official source page for this file is:
**[ICAO Public Key Directory - ICAO Master List](https://www.icao.int/icao-pkd-icao-master-list)**

---

## 📁 File Description

This repository contains a single, critical file:

*   `allowlist.ml`

This is the ICAO Master List. It is not a simple certificate file, but a CMS (Cryptographic Message Syntax) `SignedData` structure that contains a collection of CSCA certificates from countries participating in the ICAO Public Key Directory (PKD). Our application is designed to parse this specific file format.

---

## 🔄 Maintenance Procedure

To ensure the trust store remains current, the `allowlist.ml` file should be updated periodically (e.g., every 3-6 months).

The update process is as follows:

1.  **Download:** Navigate to the official [ICAO Master List page](https://www.icao.int/icao-pkd-icao-master-list). Complete the CAPTCHA and accept the terms to download the latest master list file.
2.  **Rename:** The downloaded file will have a versioned name (e.g., `icao-master-list-001.ml`). Rename this file to exactly `allowlist.ml`.
3.  **Upload:** In this GitHub repository, use the "Add file" -> "Upload files" function to upload the new `allowlist.ml`. This will automatically replace the existing file.
4.  **Commit:** Use a clear and descriptive commit message for the change, including the date of the update. For example: `Update allowlist.ml with version from 2025-08-19`.

---

## 🚀 Usage

The ePassport verification service is configured to download this file from its raw GitHub URL at startup. The application caches the file and the certificates extracted from it.

The direct URL used by the application is:

`https://raw.githubusercontent.com/zenopie/csca-trust-store/main/allowlist.ml`

---

## ⚖️ Disclaimer

This repository is a mirror and is not the official distribution point for the ICAO Master List. It is maintained for stability and accessibility purposes. All data contained within the `masterlist.ml` file is provided and signed by the ICAO.
