| Field | Details |
|---|---|
| **Pentester Name** | Chinedum Nelson Ariwa |
| **Program/Batch** | B083-Networkwalks |
| **Assessment Date** | October 2, 2026 |
| **Project** | Mediroza Hospital Penetration Testing |
| **Client/Target** | `https://medirozahospital.com` |
| **Authorization** | Written permission stated in the project brief |
| **Operating Environment** | Kali Linux running in VirtualBox |
| **Tools Used** | Nmap, cURL, WhatWeb, Burp Suite Community Edition, and a web browser |
| **Project Status** | In progress; update based on verified milestone evidence |

2. Scope and Methodology
   
2.1 Scope
   
| Item | Description |
|---|---|
| `Target` | `https://medirozahospital.com` |
| Assessment Type | Authorized educational web application penetration testing |
| `M1` | Initial Access | Retrieve three designated patient PDF lab reports and document proof of access. |
| `M2` |  Data Extraction | Analyze the encryption of the three PDF files and document successful recovery of their contents. |
| `M3` | Critical Data Exposure | Investigate and document the required staff salary and shareholder information. |
| `M4` | Penetration Testing Report | Prepare the report, including findings, evidence, risk ratings, and remediation recommendations. |

2.2 Tools and Their Purposes
| Tool | Purpose |
|---|---|
| `Kali Linux` | Testing environment for reconnaissance and web application assessment. |
| `Nmap` | Identify the target host and scan selected web ports. |
| `cURL` | Inspect HTTP response headers and retrieve website resources. |
| `WhatWeb` | Identify web technologies where responses permit. |
| `Burp Suite Community Edition` | Inspect browser-generated HTTP requests and responses. |
| `Web Browser` | Navigate the website and inspect pages through normal browsing. |
| `VirtualBox` | Run the Kali Linux virtual machine. |

3. Findings and Prove of Exploitations
3.1 Patients and Staff Login Portal
   
| Field | Patient Portal | Staff Portal |

|---|---|---|
| **Endpoint** | /patient/login.php | /staff/login.php |
| **HTTP Method** | `POST` | `POST` |
| **Username Field** | username | username |
| **Password Field** | password` | `password` |
| **Observed Status** | Login page loaded successfully | Login page accessed |
| **Security Assessment** | Authentication mechanism identified | Authentication mechanism identified |

Observation: Both portals use username-and-password authentication. The presence of these login pages alone does not establish a security vulnerability.

3.2 Potentially Exposed Legacy Database Backup
| Field | Details |
|---|---|
| **Finding** | Potentially exposed legacy database backup |
| **Directory Observed** | `/old/` |
| **Filename Observed** | `mediroza_db_backup_2019_sql` |
| **Reported Information** | Staff names, telephone numbers, email addresses, and salary details |
| **Potential Impact** | Unauthorized disclosure of confidential staff or business information |
| **Evidence Required** | Screenshot of the directory listing, exact resource path, and relevant HTTP response |
| **Risk Rating** | Potentially High, subject to verification |

Observation: The reported exposure warrants investigation. Confirm the resource's accessibility and authorization requirements before assigning a final risk rating. Do not include actual patient records or unnecessary staff personal information in the report.

4. Milestone Progress
This table shows which project objectives I have completed.
| Milestone | Required Task | Evidence to Include | Status |
|---|---|---|---|
| `M1` | Initial Access** | Access the designated patient PDF reports and retrieve all three files. | Screenshots and evidence confirming retrieval of the three PDFs. | Completed. |
| `M2` | Data Extraction** | Crack the encryption and recover the contents of all three PDF files. | Evidence of the encryption analysis and successful recovery for each file. | Completed. |
| `M3` | Critical Data Exposure** | Identify staff salaries and shareholder details. | Redacted evidence supporting both findings. | Staff salary information reportedly accessed; confirm shareholder details separately. |
| `M4` | Pentest Report** | Produce the final report with findings, risk ratings, and recommendations. | Completed report with supporting evidence. | In progress until the report is finalized. |

5. Risk Rating
| S/N | Finding | Evidence Collected | Risk Factor | Risk Rating | Justification |
|---|---|---|---|---|---|
| 1 | `Exposure of patient PDF laboratory reports` | `Evidence showing that three patient PDF reports were retrieved` | **Confidentiality breach involving sensitive medical information** | **Critical** | `If the reports contain real patient medical information and were accessible without authorization, the exposure could seriously compromise patient privacy and confidentiality.`|
| 2 | `Exposure of a legacy database backup` | `Evidence showing that `mediroza_db_backup_2019_sql` was publicly accessible` | **Unauthorized access to database information** | **Critical** | If the backup contains sensitive patient records, staff information, credentials, or other confidential data, public access could expose a substantial amount of information. |
| 3 | `Exposure of staff salary information` | `Evidence showing staff salary details were accessible` | **Confidentiality breach involving employee financial information** | **High** | `Unauthorized disclosure of salary information could violate employee privacy and expose confidential organizational information`. |
| 4 | `Exposure of staff names, phone numbers, and email addresses` | `Evidence showing staff contact information was accessible` | **Personal information disclosure** | **High** | `Exposed contact details could facilitate phishing, social engineering, impersonation, or targeted attacks against hospital staff. |
| 5 | `Exposure of shareholder details` | `Evidence showing shareholder information was accessible` | **Disclosure of confidential business information** | **High**, `if the information is confidential and the impact is significant` | `The impact depends on the sensitivity of the information, whether it was intended for public release, and whether it could enable fraud or targeted attacks`. |
| 6 | `Patient and staff login portals` | `Burp Suite evidence showing the login pages and their HTTP requests` | **Potential authentication risk** | **Informational — no vulnerability established** | `The existence of login pages and the use of POST requests do not, by themselves, demonstrate a vulnerability. A higher rating requires evidence of a specific authentication weakness`. | 

Risk Rating Key
| Rating | Description |
|---|---|
| **Critical** | Exceptionally severe compromise or exposure of highly sensitive information. |
| **High** | Significant unauthorized access or disclosure of sensitive information. |
| **Medium** | Meaningful but more limited security impact. |
| **Low** | Limited direct security impact. |

Recommendation and Remediation
| No. | Area | Recommendation |
|---|---|---|
| 1 | Database Backups | Remove database backups from publicly accessible directories and store them in protected locations. |
| 2 | Backup Security | Encrypt backups, restrict access to authorized personnel, and establish a secure retention policy. |
| 3 | Patient Portal | Enforce server-side authentication and authorization for patient records. |
| 4 | Staff Portal | Apply role-based access controls and secure session management. |
| 5 | Sensitive Information | Restrict access to staff salaries, shareholder records, and patient information. |
| 6 | Monitoring | Review access logs for evidence of unauthorized access to exposed resources. |
| 7 | Data Protection | Redact unnecessary personal and medical information from report screenshots. |
| 8 | Security Testing | Conduct future assessments only within the authorized project scope. |

7. Conclusion
The assessment identified the patient and staff login portals and a potentially exposed legacy database backup. The login forms were inspected, and staff salary information was reportedly observed in the database.
The penetration testing assessment of Mediroza Hospital identified potential security risks involving the exposure of patient laboratory reports, legacy database backups, staff personal information, salary details, and shareholder information. The findings highlight the importance of strengthening access controls, securing sensitive files, removing publicly accessible backups, and improving data protection and monitoring. Based on the evidence collected, prompt remediation is recommended to reduce the risk of unauthorized access, data breaches, and privacy violations. These findings demonstrate the value of regular security assessments in protecting confidential information and maintaining the hospital’s information security.

8. Evidence Collected
<img width="1366" height="728" alt="image" src="https://github.com/user-attachments/assets/5d4a8332-6aad-483f-8146-6d0702cf4917" />
<img width="1366" height="728" alt="image" src="https://github.com/user-attachments/assets/401d6a09-be4e-4684-91f7-7d223a55c0f5" />
<img width="1366" height="728" alt="image" src="https://github.com/user-attachments/assets/a8d46a6f-e198-4f95-8f5c-2d41c81bcf62" />
<img width="1366" height="728" alt="image" src="https://github.com/user-attachments/assets/fb8dc889-d9a5-413b-b5c3-7233fa16f5d5" />
<img width="1366" height="728" alt="image" src="https://github.com/user-attachments/assets/759fd0e4-e2d7-4bd3-add6-040aa45cf93b" />
<img width="1366" height="728" alt="image" src="https://github.com/user-attachments/assets/7f284bd3-1374-4756-b22a-1d29d7dff966" />
<img width="1366" height="728" alt="image" src="https://github.com/user-attachments/assets/8ebfe687-06a6-4638-8738-8421ff07b50c" />
<img width="1366" height="728" alt="image" src="https://github.com/user-attachments/assets/83617d6e-5f9c-4bfd-a211-6bb2ea41889c" />
<img width="1366" height="728" alt="image" src="https://github.com/user-attachments/assets/45ff679c-b175-4765-b307-4f3349f43f57" />
<img width="1366" height="728" alt="image" src="https://github.com/user-attachments/assets/b2945f60-a848-4fab-8321-37b0e1041653" />
<img width="1366" height="728" alt="image" src="https://github.com/user-attachments/assets/0400dce6-541e-4ad0-a827-153978045eff" />
<img width="1366" height="728" alt="image" src="https://github.com/user-attachments/assets/4f005320-7d2f-4ca4-abdf-a6349d167fcf" />
<img width="1366" height="728" alt="image" src="https://github.com/user-attachments/assets/d7af7844-dafd-482e-8356-7326df2aa12e" />
<img width="1366" height="728" alt="image" src="https://github.com/user-attachments/assets/f4fa2247-6947-4a34-a56b-3cf79a26022d" />















