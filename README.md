# HELENA-resources

Versioned precomputed response resources for HELENA. HELENA software is distributed separately.

## BH C513 responses v1

The [bh-c513-v1 release](https://github.com/LiYangji/HELENA-resources/releases/tag/bh-c513-v1)
provides three precomputed Bethe--Heitler pair-response tensors and their
metadata as one six-file ZIP. These are numerical response resources, not
observational data or a fitted source solution.

Compatibility is exact: cache format 1, physics response
`ka2008_born_omega_lt_600_v1`, grid
`c513_daughter513_proton441_targets64-86-96_v1`, float64 (`<f8`).
Tensor layout is (proton, target photon, daughter), with shapes
(441, 64, 513), (441, 86, 513), and (441, 96, 513).
The [manifest](bh-c513-v1.json) records all six filenames and checksums.
These responses apply to the implemented Born domain, omega < 600 in
electron-rest-energy units; they are not a replacement for other grids or physics versions.

ZIP: `helena_bethe_heitler_c513_responses_ka2008_born_omega_lt_600_v1.zip`  
Size: 445,233,688 bytes  
SHA256: `a3abbcf77452bcc5015e848130a463e691d717954150611b47f8f19569bd88d4`

## Cache installation

With a HELENA installation whose official resource descriptor is bound to this release:

```bash
helena cache path
helena cache fetch
helena cache status
```

All three commands accept `--cache-dir PATH`. Resolution is explicit
`cache_dir`/`--cache-dir`, then `HELENA_CACHE_DIR`, then the platform default.
For later model runs, set `HELENA_CACHE_DIR` or pass `cache_dir` to the model;
a one-time fetch with `--cache-dir` does not persist that selection.

For manual/offline installation, download the ZIP and its `.sha256` attachment.
Verify the complete ZIP against the SHA256 above (for example,
`sha256sum -c helena_bethe_heitler_c513_responses_ka2008_born_omega_lt_600_v1.zip.sha256`).
Extract the six files directly into the directory resolved by `helena cache path`,
without an enclosing folder, then run `helena cache status`.
Normal HELENA model loading uses compatible local responses without downloading
or silently rebuilding them.

## Attribution and licensing

The existing HELENA BSD-3-Clause notice is reproduced unchanged in [LICENSE](LICENSE).
It does not license the cited publications or other third-party material.
The tensors are generated numerical responses, not copies of publication tables.

The implemented pair-response formalism is attributed to
[Kelner & Aharonian (2008), Physical Review D, 78, 034013](https://doi.org/10.1103/PhysRevD.78.034013)
([published erratum, 2010, 82, 099901](https://doi.org/10.1103/PhysRevD.82.099901))
and [Blumenthal (1970), Physical Review D, 1, 1596](https://doi.org/10.1103/PhysRevD.1.1596).
Citation identifies the physical basis; it is not an endorsement by these authors.
