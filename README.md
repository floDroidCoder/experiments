- Password for certificate is P@ssw0rd, totally secure !
- Secret for certificate is P@ssw0rd, totally secure !

https://spectralops.io/blog/top-9-git-secret-scanning-tools/

Gitleaks:
- Cannot find the README.md secret
- Cannot find the Java secret
- Found the AWS_KEY in the .env, cmd file
````
  Finding:     ... run -e SEMGREP_APP_TOKEN=da3edb619deb67174bb82007511c68ef8a6cc96a93315a56b2011d2b71d1e6b8 --rm -v "%cd%:/src"...
Secret:      da3edb619deb67174bb82007511c68ef8a6cc96a93315a56b2011d2b71d1e6b8
RuleID:      generic-api-key
Entropy:     3.812949
File:        README.md
Line:        60
Commit:      801858a284710be911c35c2ad5052c6ca51416ba
Author:      fgenaudet
Email:       fgenaudet@fgenaudet.com
Date:        2024-08-26T11:36:10Z
Fingerprint: 801858a284710be911c35c2ad5052c6ca51416ba:README.md:generic-api-key:60

Finding:     ... run -e SEMGREP_APP_TOKEN=da3edb619deb67174bb82007511c68ef8a6cc96a93315a56b2011d2b71d1e6b8 --rm -v "%cd%:/src"...
Secret:      da3edb619deb67174bb82007511c68ef8a6cc96a93315a56b2011d2b71d1e6b8
RuleID:      generic-api-key
Entropy:     3.812949
File:        semgrep.cmd
Line:        1
Commit:      801858a284710be911c35c2ad5052c6ca51416ba
Author:      fgenaudet
Email:       fgenaudet@fgenaudet.com
Date:        2024-08-26T11:36:10Z
Fingerprint: 801858a284710be911c35c2ad5052c6ca51416ba:semgrep.cmd:generic-api-key:1

Finding:     ... run -e SEMGREP_APP_TOKEN=da3edb619deb67174bb82007511c68ef8a6cc96a93315a56b2011d2b71d1e6b8 --rm -v "%cd%:/src"...
Secret:      da3edb619deb67174bb82007511c68ef8a6cc96a93315a56b2011d2b71d1e6b8
RuleID:      generic-api-key
Entropy:     3.812949
File:        semgrep.cmd
Line:        1
Commit:      768eee8a5f47484a62a3bd9175ceb4fbf26c4823
Author:      GENAUDET Florian
Email:       florian.genaudet@sword-group.com
Date:        2024-08-26T10:44:19Z
Fingerprint: 768eee8a5f47484a62a3bd9175ceb4fbf26c4823:semgrep.cmd:generic-api-key:1

Finding:     AWS_KEY=AKIAIOSFODNN7EXAMPLE
Secret:      AKIAIOSFODNN7EXAMPLE
RuleID:      aws-access-token
Entropy:     3.684184
File:        .env
Line:        1
Commit:      12fe526540c878260e2776469500fa76cbc1c109
Author:      GENAUDET Florian
Email:       florian.genaudet@sword-group.com
Date:        2024-08-26T08:44:48Z
Fingerprint: 12fe526540c878260e2776469500fa76cbc1c109:.env:aws-access-token:1

Finding:     ... [.env:1] AWS_KEY = AKIAIOSFODNN7EXAMPLE
Secret:      AKIAIOSFODNN7EXAMPLE
RuleID:      aws-access-token
Entropy:     3.684184
File:        README.md
Line:        37
Commit:      768eee8a5f47484a62a3bd9175ceb4fbf26c4823
Author:      GENAUDET Florian
Email:       florian.genaudet@sword-group.com
Date:        2024-08-26T10:44:19Z
Fingerprint: 768eee8a5f47484a62a3bd9175ceb4fbf26c4823:README.md:aws-access-token:37

Finding:     ... [.env:1] AWS_KEY = AKIAIOSFODNN7EXAMPLE
Secret:      AKIAIOSFODNN7EXAMPLE
RuleID:      aws-access-token
Entropy:     3.684184
File:        README.md
Line:        38
Commit:      768eee8a5f47484a62a3bd9175ceb4fbf26c4823
Author:      GENAUDET Florian
Email:       florian.genaudet@sword-group.com
Date:        2024-08-26T10:44:19Z
Fingerprint: 768eee8a5f47484a62a3bd9175ceb4fbf26c4823:README.md:aws-access-token:38

Finding:     ...AWS_KEY", "value": "AKIAIOSFODNN7EXAMPLE", "file": ".env", "...
Secret:      AKIAIOSFODNN7EXAMPLE
RuleID:      aws-access-token
Entropy:     3.684184
File:        README.md
Line:        53
Commit:      768eee8a5f47484a62a3bd9175ceb4fbf26c4823
Author:      GENAUDET Florian
Email:       florian.genaudet@sword-group.com
Date:        2024-08-26T10:44:19Z
Fingerprint: 768eee8a5f47484a62a3bd9175ceb4fbf26c4823:README.md:aws-access-token:53

Finding:     ...AWS_KEY", "value": "AKIAIOSFODNN7EXAMPLE", "file": ".env", "...
Secret:      AKIAIOSFODNN7EXAMPLE
RuleID:      aws-access-token
Entropy:     3.684184
File:        README.md
Line:        53
Commit:      768eee8a5f47484a62a3bd9175ceb4fbf26c4823
Author:      GENAUDET Florian
Email:       florian.genaudet@sword-group.com
Date:        2024-08-26T10:44:19Z
Fingerprint: 768eee8a5f47484a62a3bd9175ceb4fbf26c4823:README.md:aws-access-token:53

2:08PM INF 8 commits scanned.
2:08PM INF scan completed in 38.3ms
2:08PM WRN leaks found: 8
 ````

Git-secret:
- Cannot find .env secret even with the regexp
- Cannot find README.md secret
- Found the Java secret with custom regexp
- Found the json secret
- Cannot find Yml secret
````
$ git secrets --scan
README.md:118:src/SecureHttpClient.java:3:    private static String AD_PASSWORD = "P@ssw0rd";
README.md:147:[WARNING] [src/env.json:2] AWS_KEY = QOSLKFNFS01254
README.md:148:[WARNING] [src/env.json:3] AWS_SECRET_KEY = QOSLKFNFS01254/DSDSDSDDS/KEY
README.md:149:[WARNING] [src/env.json:3] AWS_SECRET_KEY = QOSLKFNFS01254/DSDSDSDDS/KEY
README.md:161:[WARNING] [out/production/Java_MTLS/env.json:2] AWS_KEY = QOSLKFNFS01254
README.md:162:[WARNING] [out/production/Java_MTLS/env.json:3] AWS_SECRET_KEY = QOSLKFNFS01254/DSDSDSDDS/KEY
README.md:163:[WARNING] [out/production/Java_MTLS/env.json:3] AWS_SECRET_KEY = QOSLKFNFS01254/DSDSDSDDS/KEY
src/InsecurePasswordExample.java:8:        String password = "P@ssw0rd123";

[ERROR] Matched one or more prohibited patterns

Possible mitigations:
- Mark false positives as allowed using: git config --add secrets.allowed ...
- Mark false positives as allowed by adding regular expressions to .gitallowed at repository's root directory
- List your configured patterns: git config --get-all secrets.patterns
- List your configured allowed patterns: git config --get-all secrets.allowed
- List your configured allowed patterns in .gitallowed at repository's root directory
- Use --no-verify if this is a one-time false positive
````

Whispers:
- Found .env secrets
- Found certificate secrets
- Cannot find README.md secret
- Cannot find Java secret
````
whispers.exe .
[WARNING] [src/.env:0] file = src/.env
[WARNING] [src/.env:1] AWS_KEY = AKIAIOSFODNN7EXAMPLE
[WARNING] [src/.env:1] AWS_KEY = AKIAIOSFODNN7EXAMPLE
[WARNING] [src/.env:2] AWS_SECRET_KEY = wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
[WARNING] [src/.env:2] AWS_SECRET_KEY = wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
[WARNING] [src/client.crt:0] file = src/client.crt
[WARNING] [src/clientKeystore.jks:0] file = src/clientKeystore.jks
[WARNING] [src/clientTruststore.jks:0] file = src/clientTruststore.jks
[WARNING] [src/env.json:2] AWS_KEY = QOSLKFNFS01254
[WARNING] [src/env.json:3] AWS_SECRET_KEY = QOSLKFNFS01254/DSDSDSDDS/KEY
[WARNING] [src/env.json:3] AWS_SECRET_KEY = QOSLKFNFS01254/DSDSDSDDS/KEY
[WARNING] [src/server.crt:0] file = src/server.crt
[WARNING] [src/serverKeystore.jks:0] file = src/serverKeystore.jks
[WARNING] [src/serverTruststore.jks:0] file = src/serverTruststore.jks
[WARNING] [out/production/Java_MTLS/.env:0] file = out/production/Java_MTLS/.env
[WARNING] [out/production/Java_MTLS/.env:1] AWS_KEY = AKIAIOSFODNN7EXAMPLE
[WARNING] [out/production/Java_MTLS/.env:1] AWS_KEY = AKIAIOSFODNN7EXAMPLE
[WARNING] [out/production/Java_MTLS/.env:2] AWS_SECRET_KEY = wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
[WARNING] [out/production/Java_MTLS/.env:2] AWS_SECRET_KEY = wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
[WARNING] [out/production/Java_MTLS/client.crt:0] file = out/production/Java_MTLS/client.crt
[WARNING] [out/production/Java_MTLS/clientKeystore.jks:0] file = out/production/Java_MTLS/clientKeystore.jks
[WARNING] [out/production/Java_MTLS/clientTruststore.jks:0] file = out/production/Java_MTLS/clientTruststore.jks
[WARNING] [out/production/Java_MTLS/env.json:2] AWS_KEY = QOSLKFNFS01254
[WARNING] [out/production/Java_MTLS/env.json:3] AWS_SECRET_KEY = QOSLKFNFS01254/DSDSDSDDS/KEY
[WARNING] [out/production/Java_MTLS/env.json:3] AWS_SECRET_KEY = QOSLKFNFS01254/DSDSDSDDS/KEY
[WARNING] [out/production/Java_MTLS/server.crt:0] file = out/production/Java_MTLS/server.crt
[WARNING] [out/production/Java_MTLS/serverKeystore.jks:0] file = out/production/Java_MTLS/serverKeystore.jks
[WARNING] [out/production/Java_MTLS/serverTruststore.jks:0] file = out/production/Java_MTLS/serverTruststore.jks
````

Semgrep
- Found no secret (because semgrep code product and not semgrep secret) https://semgrep.dev/blog/2023/introducing-semgrep-secrets 
- Found 2 vulns in java code
````
C:\Dev\Java_MTLS>docker run -e SEMGREP_APP_TOKEN=da3edb619deb67174bb82007511c68ef8a6cc96a93315a56b2011d2b71d1e6b8 --rm -v "%cd%:/src" semgrep/semgrep semgrep scan
METRICS: Using configs from the Registry (like --config=p/ci) reports pseudonymous rule metrics to semgrep.dev.
To disable Registry rule metrics, use "--metrics=off".
Using configs only from local files (like --config=xyz.yml) does not enable metrics.

More information: https://semgrep.dev/docs/metrics



┌─────────────┐
│ Scan Status │
└─────────────┘
  Scanning 21 files tracked by git with 1848 Code rules:

  Language      Rules   Files          Origin      Rules
 ─────────────────────────────        ───────────────────
  <multilang>      36      21          Community    1040
  java            258       3          Pro rules     808
  yaml             29       2



┌─────────────────┐
│ 2 Code Findings │
└─────────────────┘

    src/Client.java
    ❯❱ java.lang.security.audit.weak-ssl-context.weak-ssl-context
          An insecure SSL context was detected. TLS versions 1.0, 1.1, and all SSL versions are considered
          weak encryption and are deprecated. Use SSLContext.getInstance("TLSv1.2") for the best security.
          Details: https://sg.run/4x7E

           ▶▶┆ Autofix ▶ SSLContext.getInstance("TLSv1.2")
           18┆ SSLContext sslContext = SSLContext.getInstance("TLS");

    src/Server.java
    ❯❱ java.lang.security.audit.weak-ssl-context.weak-ssl-context
          An insecure SSL context was detected. TLS versions 1.0, 1.1, and all SSL versions are considered
          weak encryption and are deprecated. Use SSLContext.getInstance("TLSv1.2") for the best security.
          Details: https://sg.run/4x7E

           ▶▶┆ Autofix ▶ SSLContext.getInstance("TLSv1.2")
           18┆ SSLContext sslContext = SSLContext.getInstance("TLS");



┌──────────────┐
│ Scan Summary │
└──────────────┘
Some files were skipped or only partially analyzed.
  Scan was limited to files tracked by git.
````

SHIFTLEFT SCAN
- Correctly detect code secrets
- Doesn't detect .env secrets
- Doesn't detect yaml secrets
- Doesn't detect markdown secrets
````
 docker run --rm -e "WORKSPACE=${PWD}" -v "/$PWD:/app" shiftleft/scan scan --out_dir=./scan_report --type=java,credscan,yaml,bash
````
````
███████╗ ██████╗ █████╗ ███╗   ██╗
██╔════╝██╔════╝██╔══██╗████╗  ██║
███████╗██║     ███████║██╔██╗ ██║
╚════██║██║     ██╔══██║██║╚██╗██║
███████║╚██████╗██║  ██║██║ ╚████║
╚══════╝ ╚═════╝╚═╝  ╚═╝╚═╝  ╚═══╝

[11:55:49] INFO     Scanning /app using plugins ['java', 'credscan', 'yaml', 'bash']

[11:55:53] INFO     Baseline file written to ./scan_report/.sastscan.baseline
                             Security Scan Summary
╔═══════════════════════════════════╤══════════╤══════╤════════╤═════╤════════╗
║ Tool                              │ Critical │ High │ Medium │ Low │ Status ║
╟───────────────────────────────────┼──────────┼──────┼────────┼─────┼────────╢
║ Shell Script Analysis             │        0 │    0 │      0 │   0 │   ✅   ║
║ Class File Analyzer               │        7 │    1 │      0 │   0 │   ❌   ║
║ Java Source Analyzer              │        0 │    0 │      0 │   0 │   ✅   ║
║ Security Audit for Infrastructure │        0 │    0 │      0 │   0 │   ✅   ║
╚═══════════════════════════════════╧══════════╧══════╧════════╧═════╧════════╝
````

Trufflehog
- Correct scan github repo
- Can't make it work in this project
````
 ./trufflehog.exe git https://github.com/trufflesecurity/test_keys --only-verified
 
 cd /c/Dev/test_keys
 ./trufflehog.exe filesystem .
````
````
2024-08-26T16:49:24+02:00       info-0  trufflehog      running source  {"source_manager_worker_id": "tLHj0", "with_units": true}
✅ Found verified result 🐷🔑
Detector Type: AWS
Decoder Type: PLAIN
Raw result: AKIAQYLPMN5HHHFPZAM2
Account: 052310077262
Is_canary: true
Message: This is an AWS canary token generated at canarytokens.org, and was not set off; learn more here: https://trufflesecurity.com/canaries
Arn: arn:aws:iam::052310077262:user/canarytokens.com@@c20nnjzlioibnaxvt392i9ope
Resource_type: Access key
File: new_key
Line: 1

✅ Found verified result 🐷🔑
Detector Type: URI
Decoder Type: PLAIN
Raw result: https://admin:admin@the-internet.herokuapp.com
File: keys
Line: 2

Found unverified result 🐷🔑❓
Verification issue: verification failures: error dialing gitlab.com:22: dial tcp 172.65.251.78:22: i/o timeout, error dialing github.com:22: dial tcp 140.82.121.4:22: i/o timeout
Detector Type: PrivateKey
Decoder Type: PLAIN
Raw result: -----BEGIN OPENSSH PRIVATE KEY-----
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
Hx7UPVlTK8dyvk1Z+Yw0nrfNClI=
-----END OPENSSH PRIVATE KEY-----
File: keys

2024-08-26T16:49:34+02:00       info-0  trufflehog      finished scanning       {"chunks": 31, "bytes": 31005, "verified_secrets": 2, "unverified_secrets": 1, "scan_duration": "10.1182247s", "trufflehog_version": "3.81.9"}
````


GitGuardian
````
$ ggshield auth login
$ ggshield secret scan repo ../Java_MTLS
````
````
commit 7f8cb5ec746bd143539dbc91750215b5717b7f9c
Author: GENAUDET Florian <florian.genaudet@sword-group.com>
Date: Mon Aug 26 10:46:46 2024 +0200

> commit://7f8cb5ec746bd143539dbc91750215b5717b7f9c/src/SecureHttpClient.java: 1 incident detected

>> Secret detected: Username Password
   Validity: No Checker
   Occurrences: 1
   Known by GitGuardian dashboard: NO
   Incident URL: N/A
   Secret SHA: 0543f2b8a8f4c497d7032deea4133451343656e41620d89bf33bf92150ac82f7

    | @@ -0,0 +1,4 @@
  1 | +public class SecureHttpClient {
  2 | +    private static String AD_USERNAME = "fg*****et";
                                                |_username_|
  3 | +    private static String AD_PASSWORD = "P@****rd";
                                                |_password_|
  4 | +}

commit 768eee8a5f47484a62a3bd9175ceb4fbf26c4823
Author: GENAUDET Florian <florian.genaudet@sword-group.com>
Date: Mon Aug 26 12:44:19 2024 +0200

> commit://768eee8a5f47484a62a3bd9175ceb4fbf26c4823/semgrep.cmd: 1 incident detected

>> Secret detected: Generic High Entropy Secret
   Validity: No Checker
   Occurrences: 1
   Known by GitGuardian dashboard: NO
   Incident URL: N/A
   Secret SHA: 3744b076265709c14cd07ae2abdc22e4d813b90fa8f8c5b6d879a807e6351722

    | @@ -0,0 +1 @@
    | \ No newline at end of file
  1 | +▒APP_TOKEN=da3edb619de******************************************d2b71d1e6b8 --rm -v "▒
                  |____________________________apikey____________________________|

> commit://768eee8a5f47484a62a3bd9175ceb4fbf26c4823/src/SecureHttpClient.java: 1 incident detected

>> Secret detected: Username Password
   Validity: No Checker
   Occurrences: 1
   Known by GitGuardian dashboard: NO
   Incident URL: N/A
   Secret SHA: 0543f2b8a8f4c497d7032deea4133451343656e41620d89bf33bf92150ac82f7

    | @@ -1,4 +1,9 @@
1 1 |  public class SecureHttpClient {
2 2 |      private static String AD_USERNAME = "fg*****et";
                                                |_username_|
3 3 |      private static String AD_PASSWORD = "P@****rd";
                                                |_password_|
  4 | +
  5 | +    /* this is the PASSWORD of my account */

commit 801858a284710be911c35c2ad5052c6ca51416ba
Author: fgenaudet <fgenaudet@fgenaudet.com>
Date: Mon Aug 26 13:36:10 2024 +0200

> commit://801858a284710be911c35c2ad5052c6ca51416ba/semgrep.cmd: 1 incident detected

>> Secret detected: Generic High Entropy Secret
   Validity: No Checker
   Occurrences: 2
   Known by GitGuardian dashboard: NO
   Incident URL: N/A
   Secret SHA: 3744b076265709c14cd07ae2abdc22e4d813b90fa8f8c5b6d879a807e6351722

    | @@ -1 +1 @@
    | \ No newline at end of file
  1 | +▒APP_TOKEN=da3edb619de******************************************d2b71d1e6b8 --rm -v "▒
                  |____________________________apikey____________________________|
...
1   | -▒APP_TOKEN=da3edb619de******************************************d2b71d1e6b8 --rm -v "▒
                  |____________________________apikey____________________________|

> commit://801858a284710be911c35c2ad5052c6ca51416ba/src/InsecurePasswordExample.java: 1 incident detected

>> Secret detected: Generic Password
   Validity: No Checker
   Occurrences: 1
   Known by GitGuardian dashboard: NO
   Incident URL: N/A
   Secret SHA: cdbe387e743e242ed0f7301e3254d50aad88209601a200142d5cf4d06fe3d638

  2 | +    public static void main(String[] args) {
  3 | +        // Hardcoded plain text password (This is insecure!)
  4 | +        String password = "P@*******23";
                                  |_password_|
  5 | +
  6 | +        // Simulating usage of the password (e.g., authentication)

> commit://801858a284710be911c35c2ad5052c6ca51416ba/src/SecureHttpClient.java: 1 incident detected

>> Secret detected: Username Password
   Validity: No Checker
   Occurrences: 1
   Known by GitGuardian dashboard: NO
   Incident URL: N/A
   Secret SHA: 0543f2b8a8f4c497d7032deea4133451343656e41620d89bf33bf92150ac82f7

    | @@ -1,9 +0,0 @@
1   | -public class SecureHttpClient {
2   | -    private static String AD_USERNAME = "fg*****et";
                                                |_username_|
3   | -    private static String AD_PASSWORD = "P@****rd";
                                                |_password_|
4   | -
5   | -    /* this is the PASSWORD of my account */

commit d5de1a5d93cdb1d29d8dcd9ff083f59ea8e8317d
Author: fgenaudet <fgenaudet@fgenaudet.com>
Date: Mon Aug 26 13:38:07 2024 +0200

> commit://d5de1a5d93cdb1d29d8dcd9ff083f59ea8e8317d/src/InsecurePasswordExample.java: 1 incident detected

>> Secret detected: Generic Password
   Validity: No Checker
   Occurrences: 1
   Known by GitGuardian dashboard: NO
   Incident URL: N/A
   Secret SHA: cdbe387e743e242ed0f7301e3254d50aad88209601a200142d5cf4d06fe3d638

    | @@ -7,6 +11,6 @@ public class InsecurePasswordExample {
3 7 |          // Hardcoded plain text password (This is insecure!)
4 8 |          String password = "P@*******23";
                                  |_password_|
5 9 |
  6 | +    public static void main(String[] args) throws SQLException {

commit 213a8bbf5050e89d257fc06496afb5e05bd54e3e
Author: fgenaudet <fgenaudet@fgenaudet.com>
Date: Mon Aug 26 16:50:17 2024 +0200

> commit://213a8bbf5050e89d257fc06496afb5e05bd54e3e/README.md: 1 incident detected

>> Secret detected: OpenSSH Private Key
   Validity: No Checker
   Occurrences: 1
   Known by GitGuardian dashboard: NO
   Incident URL: N/A
   Secret SHA: 5262e67846bb2dd2707b928e2cab187895205e363a054548bbcd8392fdd0175c

117 338 |
...
    296 | +Detector Type: PrivateKey
    297 | +Decoder Type: PLAIN
    298 | +Raw result: -----BEGIN OPENSSH PRIVATE KEY-----
    299 | ▒+b3BlbnNzaC1rZXktdjEAAAA***********************************************▒
    300 | ▒+**********************************************************************▒
    301 | ▒+**********************************************************************▒
    302 | ▒+**********************************************************************▒
    303 | ▒+**********************************************************************▒
    304 | ▒+**********************************************************************▒
    305 | ▒+**********************************************************************▒
    306 | ▒+**********************************************************************▒
    307 | ▒+**********************************************************************▒
    308 | ▒+********************+*********************************************+***▒
    309 | ▒+**********************************************************************▒
    310 | ▒+**********************************************************************▒
    311 | ▒+****+*****************************************************************▒
    312 | ▒+***************************+******************************************▒
    313 | ▒+**********+***********************************************************▒
    314 | ▒+***********+*************************************************+*+******▒
    315 | ▒+********+****************************+**********************+*********▒
    316 | ▒+********************************************************************+*▒
    317 | ▒+***********+**********************************************************▒
    318 | ▒+****************************************************+*****************▒
    319 | ▒+*************+*********************+**********************************▒
    320 | ▒+**+*******************************************************************▒
    321 | ▒+**********************************************************************▒
    322 | ▒+**********************************************************************▒
    323 | ▒+*********************************+********+***************************▒
    324 | ▒+********************************************************************+*▒
    325 | ▒+********************+*************************************************▒
    326 | ▒+***********************************************+**********************▒
    327 | ▒+****++****************************************************************▒
    328 | ▒+******************+***************************************************▒
    329 | ▒+**************************************************************+*******▒
    330 | ▒+******************************************************+***************▒
    331 | ▒+**************+*************************+*+***************************▒
    332 | ▒+**********************************************************************▒
    333 | ▒+*****+******************************************************+*********▒
    334 | ▒+************************************************+*********************▒
    335 | +***UPVlTK8dyvk1Z+Yw0nrfNClI=
    336 | +-----END OPENSSH PRIVATE KEY-----
          |________________________________apikey________________________________|
    337 | +File: keys

> commit://213a8bbf5050e89d257fc06496afb5e05bd54e3e/src/env.json: 1 incident detected

>> Secret detected: Generic High Entropy Secret
   Validity: No Checker
   Occurrences: 1
   Known by GitGuardian dashboard: NO
   Incident URL: N/A
   Secret SHA: e02b149713295b1f1c11a5dd5d018aee5adfff10b2245f33bc1413df6b43effa

  1 | +{
  2 | +  "AWS_KEY": "QOSLKFNFS01254",
  3 | +  "AWS_SECRET_KEY": "QOSLK******************S/KEY",
                            |__________apikey__________|
  4 | +  "AWS_IAM": "arn:aws:iam::123456789012:user/Development/product_1234/*"
  5 | +}

> commit://213a8bbf5050e89d257fc06496afb5e05bd54e3e/src/env.yml: 1 incident detected

>> Secret detected: Username Password
   Validity: No Checker
   Occurrences: 1
   Known by GitGuardian dashboard: NO
   Incident URL: N/A
   Secret SHA: ab8d5134bdfefbf720e15cad6171e51fed19f9bf35ca9969cc16b3a989cc1ac0

  3 | +app:
  4 | +  secrets:
  5 | +    - PASSWORD: P@****rd
                       |_password_|
  6 | +    - USERNAME: fg*****et
                       |_username_|
````


YELP/Detect-Secrets
````
$ detect-secrets scan > .secrets.baseline
$ detect-secrets audit .secrets.baseline
````
````
Secret:      1 of 8
Filename:    src\.env
Secret Type: AWS Access Key
----------
1:AWS_KEY=AKIAIOSFODNN7EXAMPLE
2:AWS_SECRET_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
----------
Should this string be committed to the repository? (y)es, (n)o, (s)kip, (q)uit: s

Secret:      2 of 8
Filename:    src\.env
Secret Type: Base64 High Entropy String
----------
1:AWS_KEY=AKIAIOSFODNN7EXAMPLE
2:AWS_SECRET_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
----------
Should this string be committed to the repository? (y)es, (n)o, (s)kip, (b)ack, (q)uit: s

Secret:      3 of 8
Filename:    src\.env
Secret Type: Secret Keyword
----------
1:AWS_KEY=AKIAIOSFODNN7EXAMPLE
2:AWS_SECRET_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
----------
Should this string be committed to the repository? (y)es, (n)o, (s)kip, (b)ack, (q)uit: s

Secret:      4 of 8
Filename:    src\Client.java
Secret Type: Secret Keyword
----------
5:import javax.net.ssl.*;
6:
7:public class Client {
8:
9:    private static final String KEYSTORE_LOCATION = "clientKeystore.jks";
10:    private static final String KEYSTORE_PASSWORD = "client";
11:    private static final String TRUSTSTORE_LOCATION = "clientTruststore.jks";
12:    private static final String TRUSTSTORE_PASSWORD = "client";
13:    private static final Logger LOGGER = Logger.getLogger(Client.class.getName());
14:
15:    public static void main(String[] args) {
----------
Should this string be committed to the repository? (y)es, (n)o, (s)kip, (b)ack, (q)uit: s

Secret:      5 of 8
Filename:    src\InsecurePasswordExample.java
Secret Type: Secret Keyword
----------
3:import java.sql.SQLException;
4:
5:public class InsecurePasswordExample {
6:    public static void main(String[] args) throws SQLException {
7:        // Hardcoded plain text password (This is insecure!)
8:        String password = "P@ssw0rd123";
9:
10:        // Simulating usage of the password (e.g., authentication)
11:        System.out.println("Connecting to the database with password: " + password);
12:
13:        // Here you would typically use the password to connect to a database or another service
----------
Should this string be committed to the repository? (y)es, (n)o, (s)kip, (b)ack, (q)uit: s

Secret:      6 of 8
Filename:    src\Server.java
Secret Type: Secret Keyword
----------
5:import javax.net.ssl.*;
6:
7:public class Server {
8:
9:    private static final String KEYSTORE_LOCATION = "serverKeystore.jks";
10:    private static final String KEYSTORE_PASSWORD = "password";
11:    private static final String TRUSTSTORE_LOCATION = "serverTruststore.jks";
12:    private static final String TRUSTSTORE_PASSWORD = "password";
13:    private static final Logger LOGGER = Logger.getLogger(Server.class.getName());
14:
15:    public static void main(String[] args) {
----------
Should this string be committed to the repository? (y)es, (n)o, (s)kip, (b)ack, (q)uit: s

Secret:      7 of 8
Filename:    src\env.json
Secret Type: Secret Keyword
----------
1:{
2:  "AWS_KEY": "QOSLKFNFS01254",
3:  "AWS_SECRET_KEY": "QOSLKFNFS01254/DSDSDSDDS/KEY",
4:  "AWS_IAM": "arn:aws:iam::123456789012:user/Development/product_1234/*"
5:}
----------
Should this string be committed to the repository? (y)es, (n)o, (s)kip, (b)ack, (q)uit: s

Secret:      8 of 8
Filename:    src\env.yml
Secret Type: Secret Keyword
----------
1:%YAML 1.2
2:---
3:app:
4:  secrets:
5:    - PASSWORD: P@ssword
6:    - USERNAME: fgenaudet
----------
Should this string be committed to the repository? (y)es, (n)o, (s)kip, (b)ack, (q)uit: s
````