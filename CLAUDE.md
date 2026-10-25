# Working on this repository

These rules apply to anyone — human or agent — **editing this repository**. They are not
instructions for using the skill on your own projects, where your files are your own.

## This repository is public

`github.com/SionVerhoef/ethercat-esi` is world-readable, mirrored by anyone who clones it,
and installed into other people's setups. Assume every commit is permanent and already read
by a stranger.

## Vendor ESI files are not ours to ship

An ESI file is freely downloadable, but it is still the vendor's copyrighted work. **Never
commit a vendor's ESI file, or a trimmed or edited copy of one.** What a device *is* — its
vendor ID, product code, PDO entries, object indices — is fact and may be stated; the file's
own XML is expression and may not be copied.

Test fixtures and examples are **hand-written ESI for a fictional device**, with the vendor
named `Example Vendor` and device names that cannot be mistaken for a real product. CI fails
on any committed `.xml` ESI file that does not name that vendor.

## Treat real project data as if it were under NDA

Configurations and custom device descriptions come from real machines belonging to real
customers. Handle all of it as confidential by default — not only what someone explicitly
marked as such.

**Never commit anything that identifies a customer, a site, a machine or a controller.**
That includes, in files *and* in commit messages, changelog entries, eval transcripts and
issue text:

- **Customer, site or end-user names**, machine and serial numbers, project codes —
  including inside device names, comments and file paths
- **ESI files for in-house or customer-specific devices** — they can describe a product that
  is unreleased or under NDA
- **ENI files and `.xti` / `.tsproj` exports** — they carry MAC addresses, serial numbers
  and the full topology of one plant. Never commit them raw.
- **AMS NetIDs, IP addresses, MAC addresses, hostnames, credentials, licence keys**
- **Process data, setpoints, cycle times** — commercially sensitive

## Anonymise by substitution, not by deletion

The point is to remove identity while keeping the teaching value. Renaming a customer to
`Customer_A` and a device to `Term 3` costs nothing and keeps every signal that matters —
which PDO did not match, which object the startup list wrote, why the slave refused PREOP.

**Names are stand-ins; structure is real.** If a finding only makes sense with the original
names in place, describe it in prose instead. Naming a *product* is fine and often
necessary: "EL7201", "EK1100", "TwinCAT 4024" describe things anyone can buy. Naming *whose*
machine it is, is not.

**Use placeholders that identify nothing:** AMS NetId `1.2.3.4.1.1`, IP addresses from
`192.0.2.0/24`, MAC addresses from `00:00:5E:00:53:xx`. CI runs `scripts/check_private.py`
and fails on any other NetId, IP or MAC it finds. It cannot recognise a customer name — that
part is on you.

## What you may use, and what you may not

**Research is not redistribution.** Read any source you lawfully can — vendor ESI files, the
ETG ESI specification and schema, device manuals. Copyright protects expression, not facts:
state which element carries the sync manager configuration; do not paste the
specification's text, tables or schema.

- **Permissive** (MIT, BSD, Apache-2, 0BSD) — may ship. Copy the upstream `LICENSE` next to
  it and record the source in the same commit.
- **Copyleft** (GPL/LGPL) — do not vendor; it would relicense this skill. Ask first.
- **Proprietary** (vendor ESI files, InfoSys, manuals, forums) — research only. Cite and
  link; reproduce no passages, tables, diagrams, screenshots or XML.
- **Member-only specs and schemas** (ETG) — the technical facts can be stated
  independently; the document's text, tables, figures and `.xsd` files cannot, and they
  never land here.

Read the licence from the upstream `LICENSE` file, never a GitHub badge. A citation is not
permission. Vendor ESI files, specs and real projects stay in `research/` (gitignored) or
outside the repo.

## Everything here must apply to everybody

This is a general-purpose skill for any vendor's devices and any EtherCAT master. Rules and
examples must make sense to a reader with no connection to the project they came from. Don't
present one configuration tool's behaviour as the specification, and don't write a
preference as a rule without saying so.

## If something private has already been committed

**Stop and tell the maintainer.** Do not quietly delete it in a follow-up commit: on a public
repo the old blob stays reachable in history on every clone and fork. Removing it needs a
history rewrite and a force-push, which is the maintainer's decision.
