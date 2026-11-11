# Security Policy

## Reporting

Report vulnerabilities privately through
[GitHub Security Advisories](https://github.com/unmapz/simple-make/security/advisories/new).

You can also email artemystudio.co@gmail.com.

Include the affected version, what happened and reproduction steps
if possible.

## Security model

simple-make downloads third-party source code and runs its build system.
Build scripts can execute arbitrary code with the invoking user's
privileges and network access. Builds are not sandboxed.

The project takes the following precautions:

- Cloning, extraction, configuration and compilation run without root.
- Elevated privileges are only used for the final copy to a
  system-wide install prefix.
- Dynamic shell arguments are quoted.
- Ownership changes do not follow symlinks.

These precautions do not make untrusted build scripts safe.
Only install projects you trust.

Package discovery does not verify repository ownership, source signatures
or checksums. Use a direct URL or your system package manager when
the source must be unambiguous.

## Supported versions

Only the latest release is supported. Fixes are made on `master`.
