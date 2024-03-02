## exfortables_py: An EXFORTABLES-Inspired Structured Database Created by EXFOR_Parser
### About

This repository contains tabulated format (x, dx, y, dy) of a directory-structured projectile/nuclide/reaction/ database, `exfortables_py` which is inspired by [EXFORTABLES](https://nds.iaea.org/talys/tutorials/exfortables.pdf). The datasets are extracted from Experimental Nuclear Reaction Database ([EXFOR](https://nds.iaea.org/exfor/)) using [EXFOR_Parser](https://github.com/IAEA-NDS/exforparser) originating from [EXFOR Master Files](https://github.com/IAEA-NDS/exfor_master) for making retrieval and utilization of EXFOR data more straightforward for users. The new version of [IAEA Nuclear Reaction Dataexplorer](https://nds.iaea.org/dataexplorer/) will be built on top of this database.

### Download formatted datasets

In order to download the entire repository from the terminal, you can invoke
```bash
git clone https://github.com/IAEA-NDS/exfortables_py.git
```

Since the repository contains large amount of files, it will take a while to get entire files to download. If you aim to clone a particular folder, i.e, projectile or projectile/nuclide, then the `sparse-checkout` command should be used. It works on git version above 2.25.0, so please make sure you have your git version updated. The following is the example to download n/Al-27 reaction datasets only.

```bash
git clone --filter=blob:none --no-checkout https://github.com/IAEA-NDS/exfortables_py.git
cd exfortables_py
git sparse-checkout set --cone
git checkout main
git sparse-checkout set n/Al-27
```

### About Dataset
The root directory's name corresponds to the projectile, with `0` indicating a spontaneous reaction involving the target nuclide, formatted as `Al-27`, for example. In this format, `0` represents the mass number of the target nuclide, such as `Ag-0`, indicating natural abundance. Currently, datasets are available only for cross sections (`xs`), fission yields (`fission/yield`), and certain neutron observables (`neutron`). Below is a preview of the repository's directory structure. 
> Please note that the `angle` and `energy` directories contain the working versions of the datasets.
```
exfortables_py
 ├──  0
 |     └── Pu-240
 |          └── 0-f
 |               └── fission
 |                   └── yield
 |                        ├── cumulative
 |                        ├── independent
 |                        |    ├── Pu-240_0-f_Bushuev-41499-002-0-2007.txt
 │                        │    ├── ....
 |                        |    └── Pu-240_0-f_Laidler-21482-002-0-1962.txt
 |                        └── primary
 ├──  a
 ├──  d
 ├──  e
 ├──  g
 ├──  i
 ├──  n
 |    └── Al-27
 │         ├── n-el
 │         │    ├── angle
 │         │    └── xs
 │         ├── n-inl-L1
 │         │    ├── angle
 │         │    └── xs
 │         │        ├── Al-27_n-inl-L1_Al27_Almen-Ramstrom-20788-002-0-1975.txt
 │         │        ├── ....
 │         │        └── Al-27_n-inl-L1_Al27_Whisnant-12875-005-0-1984.txt
 │         └── n-x
 ├──  p
 ├──  t
 ├──  LICENSE.md
 └──  README.md
```

### File format
An example of the file format for `n/Al-27/n-inl-L1/xs/Al-27_n-inl-L1_Almen-Ramstrom-20788-002-0-1975.txt` is provided below.
```
# entry-subent-pointer  : 20788-002-0 
# EXFOR reaction        : ['13-AL-27', ['N,INL'], '13-AL-27,PAR,SIG'] 
# incident energy       : 2.0200e+00 MeV - 4.5000e+00 MeV 
# target                : Al-27 
# product               : Al-27 
# level energy          : 8.4200e-01 MeV 
# MF-MT number          : 3 - 51 
# first author          : E.Almen-Ramstrom 
# institute             : (2SWDAE ): Studsvik Energiteknik AB 
# reference             : (R,AE-503,197504) 
# year                  : 1975 
# facility              : (VDG): Van de Graaff 
# git                   : https://github.com/IAEA-NDS/exfor_master/blob/main/exforall/207/20788.x4 
# nds                   : https://nds.iaea.org/EXFOR/20788
#
#       E_in(MeV)       dE_in(MeV)            XS(B)           dXS(B)
      2.02000E+00      0.00000E+00      8.00000E-02      1.20000E-02
      2.27000E+00      0.00000E+00      6.60000E-02      1.00000E-02
      2.50000E+00      0.00000E+00      5.80000E-02      9.00000E-03
      2.77000E+00      0.00000E+00      1.05000E-01      1.60000E-02
      3.01000E+00      0.00000E+00      5.80000E-02      9.00000E-03
      3.29000E+00      0.00000E+00      5.10000E-02      8.00000E-03
      3.52000E+00      0.00000E+00      4.90000E-02      7.00000E-03
      3.78000E+00      0.00000E+00      8.50000E-02      1.30000E-02
      4.02000E+00      0.00000E+00      4.90000E-02      7.00000E-03
      4.26000E+00      0.00000E+00      6.60000E-02      1.00000E-02
      4.50000E+00      0.00000E+00      5.00000E-02      8.00000E-03
```


### Citations
For this database:
* **S. Okumura, G. Schnabel, and A. Koning** - “Development of an EXFORTABLES-Inspired Structured Database through EXFOR Parser” - [*Proceedings of the Joint Symposium on Nuclear Data and PHITS in 2023, November 15-17, 2023, Tokai, Japan*](https://jopss.jaea.go.jp) (Submitted)

For [EXFOR_Parser](https://github.com/IAEA-NDS/exforparser) and [IAEA Nuclear Reaction Dataexplorer](https://nds.iaea.org/dataexplorer/):
* **S. Okumura, G. Schnabel, and A. Koning** - “Developing a New Web Service for Experimental Nuclear Reaction Database (EXFOR) Using RESTful API and JSON” - [*Proceedings of the 16th International Conference on Nuclear Reaction Mechanisms, 11–16 Jun 2023, Varenna, Italy, EPJ Web of Conf.*](https://www.epj-conferences.org/) (Accepted)

### License and Disclaimer
* This project is licensed under the CC BY-SA License - see the [LICENSE.md](LICENSE.md) file for details.
* Changes: The developers of this repository reserve the right to modify or update datasets at any time without prior notice.

### Get in touch
To report a bug, error, or feature request, please open an [issue](https://github.com/IAEA-NDS/exfortables_py/issues).

## The original EXFORTABLES
aThe original EXFORTABLES is actively used for the [TENDL library](https://tendl.web.psi.ch/) and is also downloadable from [here](https://nds.iaea.org/talys/) as a compressed package.