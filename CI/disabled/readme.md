# List of Formats Disabled by Test

Problematic formats that need to be disabled during testing:

Platform #0 name: Intel(R) OpenCL, version: OpenCL 3.0 LINUX\
\- Driver version: 2024.18.10.0.08_160000.

```bash
# TS internal (./jtrts.pl -noprelims -internal enabled)
# CPU formats => Error processing POT
# OpenCL formats => Expected count(s) failure

disable_list="
    adxcrypt
    as400-des
    bcrypt
    descrypt
    lm
    net-ah
    nethalflm
    netlm
    pst
    racf
    rvary
    sapb
    tripcode
    vnc
    argon2-opencl
    bcrypt-opencl
    descrypt-opencl
    krb5tgs-opencl
    lm-opencl
    o5logon-opencl
    pgpdisk-opencl
    pfx-opencl
    sha256crypt-opencl
    zip-opencl
"
```

```bash
# TS opencl (./jtrts.pl -noprelims -type opencl)
# => Expected count(s) failure

# OpenCL descrypt builds for all 4096 salts, it is unusable inside CI
disable_list="
    bcrypt-opencl
    descrypt-opencl
    krb5pa-md5-opencl
    lm-opencl
    mscash-opencl
    nt-opencl
    ntlmv2-opencl
    o5logon-opencl
    sha256crypt-opencl
    zip-opencl
"
```

```bash
# TS regular (./jtrts.pl -dynamic none)
# => Expected count(s) failure

disable_list="
    descrypt
    lm
    netlm
    pst
    sapB
    vnc
"
```

Also, in a regular `--test` session or in a cracking session:

Platform #0 name: Intel(R) OpenCL, version: OpenCL 3.0 LINUX\
\- Driver version: 2023.16.10.0.17_160000.

```bash
'RACF-KDFAES'             #SLOW
'RAR'                     #SLOW
'wpapsk-opencl'           #SLOW
'wpapsk-pmk-opencl'       #SLOW
'argon2-opencl'           #SLOW
'bitlocker-opencl'        #SLOW

# Let's say these are fragile
'krb5pa-md5-opencl'
'o5logon-opencl'
'mscash-opencl'
'salted_sha-opencl'

'pgpdisk-opencl'          #FAILED (cmp_all(49)) Intel OpenCL CPU

# Formats failing Intel OpenCL CPU driver
'krb5tgs-opencl'
'pfx-opencl'

#Testing: mscash2-opencl, MS Cache Hash 2 (DCC2) [PBKDF2-SHA1 OpenCL]... run_tests.sh: line 304:  6634 Segmentation fault
#      (core dumped) "$JTR_BIN" -test-full=0 --format=opencl
'mscash2-opencl'

# SunMD5 on aarch64 and M1
# :: Testing: SunMD5 [MD5 128/128 ASIMD 4x2]... (4xOMP) *** stack smashing detected ***: terminated
# :: *** stack smashing detected ***: terminated
# :: *** stack smashing detected ***: terminated
# :: run_tests.sh: line 97: 24449 Aborted                 (core dumped) "$JTR_BIN" -test-full=0 --format=cpu
'SunMD5'

# OpenCL Intel CPU on Azure
# Testing: streebog256crypt-opencl, Astra Linux $gost12256hash$ (rounds=5000) [GOST R 34.11-2012 OpenCL]...
# run_tests.sh: line 304:  6476 Killed                  "$JTR_BIN" -test-full=0 --format=opencl
'streebog256crypt-opencl'
'streebog512crypt-opencl'
'gost94crypt-opencl'
```