---
name: ethercat-esi
description: "Use to look up exact facts about an EtherCAT device from the ESI device description files already installed on the user's machine (TwinCAT or CODESYS): which CoE objects a drive or terminal has, with data type, access, default and range; its default and selectable PDO mappings; the CiA 402 modes it supports (0x6502); what changed between two devices or firmware revisions; and whether the ESI folder holds the revision a project uses. Use it instead of guessing an object index or a process-data layout. Not for live network faults or slaves stuck below OP (use ethercat-diagnostics), the CiA 402 state machine (use cia402-motion) or NC axis configuration (use twincat-motion). DRAFT: under development."
---

# ethercat-esi

> **Draft.** This skill is under development and not ready to install.

## Goal

Answer exact device questions — objects, data types, process data, supported modes — from
the ESI files on the user's own machine, so the agent stops guessing them. It reads those
files; it never edits, moves or distributes them.
