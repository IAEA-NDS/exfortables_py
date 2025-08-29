# exfortables\_py: An EXFORTABLES-Inspired Structured Database

## About

**Note:** This repository is under active development and testing (as of April 2025).

`exfortables_py` provides tabulated datasets in the format `(x, dx, y, dy)` organized in a directory structure by **projectile / nuclide / reaction**. It is inspired by [EXFORTABLES](https://nds.iaea.org/talys/tutorials/exfortables.pdf) and built using [EXFOR\_Parser](https://github.com/IAEA-NDS/exforparser) to extract data from [EXFOR Master Files](https://github.com/IAEA-NDS/exfor_master).

The goal is to make retrieval and utilization of EXFOR data more straightforward. The upcoming version of the [IAEA Nuclear Reaction Data Explorer](https://nds.iaea.org/dataexplorer/) will be based on this database.

---

## Downloading Datasets

To download the entire repository:

```bash
git clone https://github.com/IAEA-NDS/exfortables_py.git
```

Since this repository contains a large number of files, cloning may take a while.
If you only need a specific folder (e.g., `n/Al-27`), use **sparse-checkout** (requires Git ≥ 2.25.0):

```bash
git clone --filter=blob:none --no-checkout https://github.com/IAEA-NDS/exfortables_py.git
cd exfortables_py
git sparse-checkout set --cone
git checkout main
git sparse-checkout set n/Al-27
```

---

## Dataset Structure

* Root directories are named after the projectile.
* `0` indicates a spontaneous reaction with a target nuclide (e.g., `Al-27`).
* Natural abundance is denoted with `-0` (e.g., `Ag-0`).
* Currently available datasets:

  * Cross sections (`xs`)
  * Fission yields (`fission/yield`)
  * Selected neutron observables (`neutron`)

> Note: The `angle` and `energy` directories contain working versions of datasets.

**Example structure:**

```
exfortables_py
 ├──  0
 |     └── Pu-240
 |          └── 0-f
 |               └── fission
 |                   └── yield
 |                        ├── cumulative
 |                        ├── independent
 │                        │    ├── Pu-240_0-f_Bushuev-41499-002-0-2007.txt
 │                        │    └── ...
 |                        └── primary
 ├──  n
 |     └── Al-27
 │          ├── n-el
 │          │    ├── angle
 │          │    └── xs
 │          ├── n-inl-L1
 │          │    ├── angle
 │          │    └── xs
 │          │        ├── Al-27_n-inl-L1_Almen-Ramstrom-20788-002-0-1975.txt
 │          │        └── ...
 │          └── n-x
 ├──  LICENSE.md
 └──  README.md
```

---

## File Format

Example file:
`n/Al-27/n-inl-L1/xs/Al-27_n-inl-L1_Almen-Ramstrom-20788-002-0-1975.txt`

```txt
# Header:
#   Title: 26-FE-56(N,P) Cross section
#   Source: EXFOR
#   Date created: 2025-08-29
# Target:
#   Z: 26
#   A: 56
#   Nuclide: 26-FE-56
# Reaction:
#   Process: N,P
#   MF-MT number: 3 - 103
#   Incident energy:  1.3560e+01 MeV - 1.4610e+01 MeV
# Residual:
#   Z: 25
#   A: 56
#   Nuclide: 25-MN-56
# EXFOR BIB:
#   Entry id: 41614-019-0
#   Reaction code: (26-FE-56(N,P)25-MN-56,,SIG)
#   First author: A.A. Filatenkov
#   Institute: (4RUSRI) Khlopin Radievij Institute, St. Petersburg
#   Reference: (R,INDC(CCP)-0460,2016)
#   Year: 2016
#   Facility: (CCW) Cockcroft-Walton accelerator
#   Master file: https://github.com/IAEA-NDS/exfor_master/blob/main/exforall/416/41614.x4
#   NDS: https://nds.iaea.org/EXFOR/41614
#
#   E_in(MeV)    dE_in(MeV)    XS(B)    dXS(B)
    1.3560E+01   0.0000E+00    1.1580E-01   4.0183E-03
    1.3740E+01   0.0000E+00    1.1610E-01   4.1448E-03
    ...
```

---

## Citations

If you use this database, please cite:

* **S. Okumura, G. Schnabel, and A. Koning**
  *Development of an EXFORTABLES-Inspired Structured Database through EXFOR Parser*
  Proceedings of the Joint Symposium on Nuclear Data and PHITS, Nov 15–17, 2023, Tokai, Japan. [JOPSS](https://jopss.jaea.go.jp) (submitted)

For [EXFOR\_Parser](https://github.com/IAEA-NDS/exforparser) and [IAEA Data Explorer](https://nds.iaea.org/dataexplorer/):

* **S. Okumura, G. Schnabel, and A. Koning**
  *Developing a New Web Service for Experimental Nuclear Reaction Database (EXFOR) Using RESTful API and JSON*
  16th Int. Conf. on Nuclear Reaction Mechanisms, Jun 11–16, 2023, Varenna, Italy. [EPJ Web of Conferences](https://www.epj-conferences.org/) (accepted)

---

## License & Disclaimer

* Licensed under **CC BY-SA** — see [LICENSE.md](LICENSE.md).
* The developers reserve the right to modify or update datasets at any time without prior notice.

---

## Contact

* To report a bug, error, or request a feature, please open an [issue](https://github.com/IAEA-NDS/exfortables_py/issues).

---

## Original EXFORTABLES

The original **EXFORTABLES** is actively used in the [TENDL library](https://tendl.web.psi.ch/) and can be downloaded as a compressed package from [IAEA TALYS](https://nds.iaea.org/talys/).

