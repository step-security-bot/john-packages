# Deployments

We use premium build providers like Azure Cloud, Launchpad, and GitLab.

![Donation](https://img.shields.io/badge/Donate-Yes-brightgreen?style=flat&logo=github-sponsors) Please donate. You can make a real difference and help our work by donating to support the infra.

At the time of this writing, `john` is known to build and work on:

* Linux (kernel 6 or later recommended)
* Android NDK r23b (on ARM and X86)
* FreeBSD (tested with 12 and later on X86)
* Solaris (tested with 11 on X86)
* Mac OS (on ARM and X86)

Also in the following Windows environments:
* Microsoft Windows (Windows 10 / Windows Server 2016 or later)
* Mingw + Wine (32-bit and 64-bit), using an ancient Fedora Docker image
* Cygwin

## Release Process

![Release Process](https://mermaid.ink/img/pako:eNp9kltLw0AQhf_KsE8KNlCQIkGUNPFStLYYRaHJw3QzbZcku2Gz663pf3eTFtRS3KfDzvnOYWDWjKuMmM-WGqsVPEWJBPeC2RR5jkshlyn0ehfNqIZwBCq_bGB4dD7XF2OUFguIDWpjq_bH87zjLT1sERj2ZzdkIFZWc4LQ1bSua61KeK5qownLdOfvd0C4nmr1JjLS9WY7CLvuG2Huce76G4hmC_QX2Muozo2qoEss0EwxT38j92glX1WYNXB1AIklVulexa2dQ8CNULJu4PoAFCmek27VqMQl_eGDL6sJInqbTOMGbg_QL0Jm6r1u5eB0LswP7nlu97sZfVSkRUnSYLEb3nXZodC8oG79hwPBY-STuBWvZ4N9Ttu64yb_ccHjOGUnrCRdosjcKazblISZFZWUMN_JjBZoC5OwRG6cFa1R8afkzDfa0gmzVYaGIoHuiErmioqaNt-mCsJW?type=png)

## John the Ripper rolling (1.9.0 Jumbo 1+) release build environments

#### Docker Image

```text
FROM docker.io/library/ubuntu:22.04
```

#### Flatpak

```text
runtime: org.freedesktop.Platform 22.08
```

#### MacOS

```text
Darwin 21.6.0 x86_64 i386
Darwin 22.4.0 arm64 arm
```

#### Snap

```text
runtime: core22
Launchpad --series=jammy
```

#### Windows

```text
OS Name:                   Microsoft Windows Server 2019 Datacenter
OS Version:                10.0.17763 N/A Build 17763
Current image version: '20230417.2'
```

## Deprecation Note (Obsolete Software or Hardware)

We can no longer build and package for these environments:

* Any 32-bit build (e.g. i386, i686, and powerpc);
* Windows 8 or older (64-bit);
* Windows Server 2012 or older (64-bit);

If you need such a build, use a previous stable or rolling release.
