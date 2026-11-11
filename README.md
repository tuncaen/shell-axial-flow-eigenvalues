# Eigenvalues of a cylindrical shell conveying axial flow: the interactive companion

Interactive pages and data for the paper

> E. Tunca and B. Uğurlu, *An Isogeometric Approach to the Flow-Induced Vibration of Cylindrical Shells Conveying Internal Axial Flow*
> (manuscript; the reference will be completed on publication).

The modes of one circumferential wavenumber *n* form a family. The paper shows the eigenvalues of the family *n* = 5
on two far fields: the rigidly extended shell and the periodically supported shell. The pages show the same diagram for the families *n* = 4
to 7 on both far fields. At each of the 328 velocity stations they also show the axial composition and the shape of
each mode. The per-station records behind the pages are included.

**Open the pages:** <https://tuncaen.github.io/shell-axial-flow-eigenvalues/>. Each page is a single HTML file and
needs no server.

## The diagram and the windows

- **The diagram** plots the imaginary part of the non-dimensional eigenvalue Ω of each mode in the family of one
  circumferential wavenumber *n* against the flow velocity *V*, with the real part dashed where it is not zero. Each mode carries the marker and color of its
  leading axial wavenumber, and is drawn in gray where no wavenumber holds half the profile. Rings mark divergence,
  restabilization, merging and splitting. Gray dots are the computed eigenvalues of *n* ≥ 1. The colors are chosen
  for light and dark grounds, so they differ from the printed figure.
- **Zoom.** The wheel or a pinch zooms, a drag pans, and Shift with a drag zooms into a box. *Paper view*, or a double
  click, returns to the range of the printed diagram.
- **The windows** show every mode at each of the 328 velocity stations: the axial profile of its radial displacement
  at five instants of one period, its composition over the axial wavenumbers *m* = 1 to 10, and its state. *Play one
  period* animates the profiles.
- **3D.** The *3D* button of a window draws its mode on the shell, moving through one period: the radial displacement,
  enlarged, on the cylinder. A drag turns the shell and the wheel zooms; *Pause* and the slider hold any instant. A
  diverged mode does not oscillate and is drawn at t = 0.
- **The leading wavenumber** follows the rule of the paper. Three other rules can be switched on for comparison.

## The pages

| Page | Far field | Realization | *n* |
| --- | --- | --- | --- |
| `pages/rigid_fin_PC00_n4.html` … `n7.html` | the rigidly extended shell | the finite extension, *L*<sub>e</sub> = 2*L* | 4, 5, 6, 7 |
| `pages/periodic_PC00_n4.html` … `n7.html` | the periodically supported shell | the single span with the symmetry closure | 4, 5, 6, 7 |
| `pages/rigid_inf_PC00_n5.html` | the rigidly extended shell | the mapped patch | 5 |

The shell is the shell of the paper: simply supported, *L* = 2 m, *R* = 1 m, *h* = 0.01 m, steel, conveying water.
Its cross-section representation is PC00, of degree 5 in both directions, with 40 elements around the circumference
and 7 along the span. The two realizations of the rigidly extended shell give almost the same results, and their
modes coincide at the scale of the diagram.

## The data

`data/<page>.npz` (NumPy) holds the velocity stations `V` and the axial sample points `xi` (from 0 to 1 along the
shell), and the record of each tracked mode `mode<i>`:

| Key | Content |
| --- | --- |
| `mode<i>_k` | the stations at which the mode is tracked, as indices into `V` |
| `mode<i>_lam`, `mode<i>_mu` | the non-dimensional eigenvalue λ and λ²; the four roots ±λ, ±λ̄ of a mode are one point in λ² |
| `mode<i>_is_real` | λ² is real: the mode oscillates or has diverged; otherwise it has merged with another mode |
| `mode<i>_ambiguous` | the identification could not separate the mode from a neighbor at that station |
| `mode<i>_P` | the share of each axial wavenumber *m* = 1 to 10 in the profile |
| `mode<i>_c` | the complex coefficients of the projection on the half-wave profiles |
| `mode<i>_w` | the complex axial profile of the radial displacement at the points `xi` |
| `mode<i>_m_lead` | the leading axial wavenumber by the rule of the paper; 0 where the identification is ambiguous |

`data/<page>.json` names the far field, the realization, *n* and the counts, and gives the wavenumbers (*m*, *n*) of
each mode at rest.

## Provenance

The eigenvalues and eigenvectors were computed with HELIST (pronounced *HEL-ist*), the authors' hydroelastic
isogeometric simulation tool, which couples finite and boundary elements. The build
used is `97d717ad` of 2026-10-08. The records and the pages were produced from the solver's output by the
authors' post-processing, and they show the same velocity stations as the printed diagrams.

## Citing

Please cite the paper, and this dataset by its Zenodo DOI: <https://doi.org/10.5281/zenodo.23970033>.
`CITATION.cff` carries both references.

## License

The data and the pages are released under the
[Creative Commons Attribution 4.0 International license](LICENSE) (CC BY 4.0).

## Credits

The data and the design of the pages are the work of the authors, Enes Tunca and Bahadır Uğurlu. Claude (Anthropic) assisted in
writing the post-processing scripts and the code of the pages, under the direction of Enes Tunca.
