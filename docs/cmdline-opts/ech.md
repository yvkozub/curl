---
c: Copyright (C) Daniel Stenberg, <daniel@haxx.se>, et al.
SPDX-License-Identifier: curl
Long: ech
Arg: <config>
Help: Configure Encrypted Client Hello (ECH) for use with the TLS session
Added: 8.6.1
Category: tls ECH
Multi: single
See-also:
  - doh-url
Example:
  - --ech true $URL
---

## `--ech`

Possible values for <config> are:
- "false": do not attempt ECH
- "grease": send a GREASE'd ECH extension
- "true": attempt ECH if possible, but don't fail if not
- "hard": attempt ECH and fail if that's not possible
- "ecl:<b64val>": a base64 encoded ECHConfigList that will be used for ECH
- "pn:<name>": a name to use to over-ride the public_name field of an ECHConfigList

When multiple ``--ech`` options are supplied then the most-recent
value for true/false/hard/grease will be used, as will the most-recent
``ecl:<b64string>`` value, and ``pn:<name>`` value, if either of
those were provided.

ECH only works with TLS 1.3 and also requires using
DoH or providing an ECHConfigList on the command line.

Most errors cause error
*CURLE_ECH_REUIQRED* (101).
