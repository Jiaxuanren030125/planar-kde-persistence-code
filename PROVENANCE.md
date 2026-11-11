# Data and source provenance

This archive separates scientific source, saved data, and reproduction/presentation tools. It contains no new experiment.

## Distribution copies and original snapshots

The Gaussian-difference source contains the 22 files bound by the historical freeze. The angular source contains seven frozen science files and the storage/analysis modules. Headers and administrative metadata have been normalized for distribution. The mathematical algorithms and analysis bodies are unchanged; these edited copies are not described as byte-identical originals.

The original attributed snapshots and detailed editing map are retained separately. `PROVENANCE.json` records original and current distributed hashes. `FILE_MANIFEST.json` verifies the current files. Historical hashes in `frozen_metadata.json` refer to the original snapshots; they are not current distribution checksums. Local freeze timestamps are not externally timestamped preregistrations.

## Saved records

The Gaussian-difference archive contains all 160 original JSON blocks (3,200 rows), byte for byte. The angular archive contains all 16,800 saved JSON objects (2,400 final result rows plus sample records, commits, states, and progress). Its administrative run identifier is normalized, with dependent JSON commit hashes and the member manifest regenerated. Every numerical observation, seed, design parameter, array descriptor, and omitted-array hash is preserved. The ZIP member manifest describes the distributed bytes, not historical bytes.

## Reproduction tools

The portable analysis modules retain the computational bodies of the original saved-data functions, with relative imports and minimal surrounding constants. The file/identity/hash wrappers operate only on saved JSON records. CSV extracts retain all rows. The portrait plotting tools use saved observations and analytic curves; changing figure layout does not change data or methods.

The historical full-run launchers retain environment-specific requirements. The current convenience layer supports saved-result reproduction; it does not claim a portable new simulation command or exact floating-point replay across systems. See README for the original environment requirements.

## Scope

`NUMERIC_SCOPE_LIMITED` is unchanged. These records describe numerical finite-sample behavior under the fixed designs. They do not certify exact continuous KDE events or establish mathematical theorems. Private correspondence, handoffs, manuscripts, credentials, local binaries, and large NPZ arrays are excluded.
