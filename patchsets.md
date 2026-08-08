# RGLoader Patchsets Specification & Eligibility Matrix

This document defines the eligibility and mapping of all **Patchsets** combining **2BL Patches**, **4BL Patches**, and **KHV (Kernel/Hypervisor) Patches** across supported build folders with `-dev` defined in [`xebuild-folders/`](file:///home/e3xp0/Projects/rgloader-patches/xebuild-folders), [`bootloaders.ini`](file:///home/e3xp0/Projects/RGLoader-Patches/builds/defaults/bootloaders.ini), and available patch sources in [`src/`](file:///home/e3xp0/Projects/rgloader-patches/src).

---

## Qualification Criteria

A **Patchset** is defined per kernel build version and `bootloaders.ini` motherboard section. To qualify as eligible:

1. **Build Folder & KHV Qualification**: The kernel version must be present in [`xebuild-folders/`](file:///home/e3xp0/Projects/rgloader-patches/xebuild-folders) with the `-dev` suffix, and must have a matching KHV patch directory in [`src/KHV/`](file:///home/e3xp0/Projects/rgloader-patches/src/KHV).
2. **Bootloader Patch Qualification**: Each section in [`bootloaders.ini`](file:///home/e3xp0/Projects/RGLoader-Patches/builds/defaults/bootloaders.ini) must have a matching patch source file for its specified **2BL** version in [`src/2BL/`](file:///home/e3xp0/Projects/rgloader-patches/src/2BL) and **4BL** version in [`src/4BL/`](file:///home/e3xp0/Projects/rgloader-patches/src/4BL).

---

## 1. KHV & Build Folder Qualification

The criteria is slimmed down to folders in [`xebuild-folders`](file:///home/e3xp0/Projects/rgloader-patches/xebuild-folders) containing the `-dev` suffix. All **5 matching build folders** qualify with matching KHV patch sources in [`src/KHV`](file:///home/e3xp0/Projects/rgloader-patches/src/KHV):

- **`13599-dev`** ([src/KHV/13599-dev](file:///home/e3xp0/Projects/rgloader-patches/src/KHV/13599-dev))
- **`14699-dev`** ([src/KHV/14699-dev](file:///home/e3xp0/Projects/rgloader-patches/src/KHV/14699-dev))
- **`14719-dev`** ([src/KHV/14719-dev](file:///home/e3xp0/Projects/rgloader-patches/src/KHV/14719-dev))
- **`15574-dev`** ([src/KHV/15574-dev](file:///home/e3xp0/Projects/rgloader-patches/src/KHV/15574-dev))
- **`17489-dev`** ([src/KHV/17489-dev](file:///home/e3xp0/Projects/rgloader-patches/src/KHV/17489-dev))

*(Note: `17489` in `xebuild-folders` is excluded as it lacks the `-dev` suffix).*

---

## 2. Bootloader Section Qualification

All sections in `bootloaders.ini` specify `4BL = CD.9452.bin`, which is satisfied by [`src/4BL/9452/9452.S`](file:///home/e3xp0/Projects/rgloader-patches/src/4BL/9452/9452.S). Eligibility depends on the availability of the matching 2BL patch source in [`src/2BL`](file:///home/e3xp0/Projects/rgloader-patches/src/2BL).

### Eligible Sections (7 Sections)

| Section Name | Required 2BL | Required 4BL | 2BL Patch File | 4BL Patch File | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`[FalconRGH2]`** | CB 5772 | CD 9452 | [`src/2BL/5772.S`](file:///home/e3xp0/Projects/rgloader-patches/src/2BL/5772.S) | [`src/4BL/9452/9452.S`](file:///home/e3xp0/Projects/rgloader-patches/src/4BL/9452/9452.S) | **Eligible** |
| **`[JasperRGH2]`** | CB 6752 | CD 9452 | [`src/2BL/6752.S`](file:///home/e3xp0/Projects/rgloader-patches/src/2BL/6752.S) | [`src/4BL/9452/9452.S`](file:///home/e3xp0/Projects/rgloader-patches/src/4BL/9452/9452.S) | **Eligible** |
| **`[ZephyrRGH2]`** | CB 4577 | CD 9452 | [`src/2BL/4577.S`](file:///home/e3xp0/Projects/rgloader-patches/src/2BL/4577.S) | [`src/4BL/9452/9452.S`](file:///home/e3xp0/Projects/rgloader-patches/src/4BL/9452/9452.S) | **Eligible** |
| **`[TrinityRGH]`** | CB 9188 | CD 9452 | [`src/2BL/9188.S`](file:///home/e3xp0/Projects/rgloader-patches/src/2BL/9188.S) | [`src/4BL/9452/9452.S`](file:///home/e3xp0/Projects/rgloader-patches/src/4BL/9452/9452.S) | **Eligible** |
| **`[TrinityRGH2]`**| CB 9188 | CD 9452 | [`src/2BL/9188.S`](file:///home/e3xp0/Projects/rgloader-patches/src/2BL/9188.S) | [`src/4BL/9452/9452.S`](file:///home/e3xp0/Projects/rgloader-patches/src/4BL/9452/9452.S) | **Eligible** |
| **`[CoronaRGH]`**  | CB 13121 | CD 9452 | [`src/2BL/13121.S`](file:///home/e3xp0/Projects/rgloader-patches/src/2BL/13121.S) | [`src/4BL/9452/9452.S`](file:///home/e3xp0/Projects/rgloader-patches/src/4BL/9452/9452.S) | **Eligible** |
| **`[CoronaRGH2]`** | CB 13121 | CD 9452 | [`src/2BL/13121.S`](file:///home/e3xp0/Projects/rgloader-patches/src/2BL/13121.S) | [`src/4BL/9452/9452.S`](file:///home/e3xp0/Projects/rgloader-patches/src/4BL/9452/9452.S) | **Eligible** |

### Ineligible Sections (3 Sections)

| Section Name | Required 2BL | Required 4BL | Missing File | Reason | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`[FalconRGH]`** | CB 5771 | CD 9452 | `src/2BL/5771.S` | Missing 2BL patch source for RGH1 CB 5771 | **Ineligible** |
| **`[JasperRGH]`** | CB 6750 | CD 9452 | `src/2BL/6750.S` | Missing 2BL patch source for RGH1 CB 6750 | **Ineligible** |
| **`[ZephyrRGH]`** | CB 4578 | CD 9452 | `src/2BL/4578.S` | Missing 2BL patch source for RGH1 CB 4578 | **Ineligible** |

---

## 3. Patchset Totals

- **Eligible Patchsets**: **35 total** (5 build versions × 7 eligible sections)
- **Ineligible Patchsets**: **15 total** (5 build versions × 3 ineligible sections)

---

## 4. Eligible Patchset Reference List

Each eligible kernel build version supports the 7 eligible motherboard sections:

### Supported Sections per Build Version:
1. `<kernel>-rgh2-falcon` (2BL `5772.S` + 4BL `9452.S` + KHV `<kernel>-dev.S`)
2. `<kernel>-rgh2-jasper` (2BL `6752.S` + 4BL `9452.S` + KHV `<kernel>-dev.S`)
3. `<kernel>-rgh2-zephyr` (2BL `4577.S` + 4BL `9452.S` + KHV `<kernel>-dev.S`)
4. `<kernel>-rgh-trinity` (2BL `9188.S` + 4BL `9452.S` + KHV `<kernel>-dev.S`)
5. `<kernel>-rgh2-trinity` (2BL `9188.S` + 4BL `9452.S` + KHV `<kernel>-dev.S`)
6. `<kernel>-rgh-corona` (2BL `13121.S` + 4BL `9452.S` + KHV `<kernel>-dev.S`)
7. `<kernel>-rgh2-corona` (2BL `13121.S` + 4BL `9452.S` + KHV `<kernel>-dev.S`)

### Supported Kernel Versions:
- **17489-dev**
- **15574-dev**
- **14719-dev**
- **14699-dev**
- **13599-dev**
