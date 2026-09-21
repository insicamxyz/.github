# İnsicam

İnsicam is a free and open-source operating system project based on a microkernel architecture. Its goal is to build an inspectable and adaptable system with clear boundaries between the kernel, core system components, user space, and drivers.

## Project principles

- **Free software:** The source code can be studied, modified, copied, and redistributed.
- **Microkernel approach:** The kernel carries only the essential responsibilities. Drivers, file systems, networking components, and other services should run in user space as separate processes whenever practical.
- **IPC boundaries:** System components and drivers communicate through interprocess communication (IPC). This boundary supports reliability, fault isolation, and distinct licensing models.
- **Central development, free forking:** İnsicam is coordinated as a central project, while anyone may fork it, study it, or create a derivative. The main development center, direction, and community coordination remain maintained by the İnsicam project.
- **Open investigation:** We study open-source projects, their derivatives, and different operating-system designs, then bring compatible technical knowledge and free-software practices into the project.

## Operating-system architectures

We do not reduce operating-system design to a single pattern. We compare several major approaches:

- **Monolithic kernels:** Drivers, file systems, networking, and other services run in kernel space. Linux and the BSD family are proven production examples. They offer performance and direct access, while a kernel-space fault can have a wider impact.
- **Microkernels:** The kernel is limited to essential mechanisms such as scheduling, address spaces, basic memory management, interrupts, and IPC. Other services run as isolated processes. This is İnsicam's primary direction. GNU Hurd is an important free-software example of the broader microkernel idea, with a different design.
- **Hybrid kernels:** These combine aspects of microkernel and monolithic designs; some services may remain in kernel space for performance or practicality. Apple's Darwin/XNU system and the Windows NT family are commonly discussed examples of a hybrid approach.
- **Modular and unikernel approaches:** Modular kernels can add and remove components at runtime. Unikernels produce a narrow system image tailored to one application. These approaches are useful design areas when evaluating İnsicam's component boundaries and distribution options.

### Systems we study

İnsicam studies the architecture, licensing, toolchains, and community practices of Linux, the BSD family (FreeBSD, OpenBSD, NetBSD, and others), GNU Hurd, macOS, Darwin, XNU, and Windows. Experimental and educational operating systems are also valuable sources of design ideas. This research is not intended to copy code or incompatible licensed material; it is intended to understand technical knowledge and approaches compatible with free software.

## Licensing model

İnsicam's core operating-system components, including the kernel and microkernel infrastructure, will be licensed under the **GNU Affero General Public License v3.0 or later (AGPLv3-or-later)**.

For system services and user space, we aim for a dual licensing direction:

1. **AGPLv3-or-later** for free-software development that requires copyleft.
2. **MIT, BSD, Apache-2.0, ISC**, or other suitable free/permissive licenses for proprietary code, internet services, and integrations that require a permissive license.

Drivers running as separate processes and communicating through IPC may be proprietary software, subject to the applicable technical and legal conditions. For example, an NVIDIA GPU driver could provide a service through defined IPC protocols instead of being linked into the İnsicam kernel as open-source code. This is not legal advice; each component must be evaluated separately based on its license, source code, linking model, and distribution method.

## Early toolchain and languages

The initial stages of the operating system will use GNU Assembler (GAS), C, and C++ among other low-level and systems-programming languages. Additional languages may be considered for suitable components. Our criteria include:

- compatibility of compiler, runtime, and library licenses with copyleft or permissive licensing,
- sufficient control and predictability on target architectures,
- maintainability, auditability, and long-term reproducibility.

## Code and content hosting

We plan to store İnsicam source code, technical documentation, and community content across these centers:

- [GitHub](https://github.com/insicamxyz)
- [Codeberg](https://codeberg.org/insicamxyz)
- [Masscollabs source server](https://source.masscollabs.xyz/insicamxyz)

These centers may be synchronized; the current project status and contribution instructions will be announced in the relevant repository on each platform.

## Logo

The project uses [Yeşil Mavi](https://openclipart.org/detail/330390/ye%C5%9Fil-mavi) as its public-domain logo. The artwork is hosted by Openclipart; when using or redistributing it, checking the source's current public-domain status remains good practice.

## Contributing

Design discussions, code, documentation, testing, toolchain work, and architectural research are all valuable contributions. Before submitting a contribution, review the license, contribution, and code-of-conduct files in the relevant repository.

İnsicam aims not only to produce a working operating system, but also to build a transparent, learnable, freely forkable, and sustainable systems community.

## License

Copyright (C) 2026-2027 PSD Authors

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published
by the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
