# IE7 client JavaScript source restoration

The original checkout contains a damaged JavaScript source distribution:
multiple files in `WebApp/jsCN/source/` and `WebApp/jsCN/source/build/files/`
are identical copies of a non-JavaScript blob. The packed client output is also
not treated as a trustworthy source archive.

This branch restores the readable modules for which we have a defensible
historical source reference:

- 70 modules recovered from the public `pacharanero/openmaxims-linux`
  source archive;
- one recovered navigation mixin copied to the historical filename
  `navigation-collapse-mixin.js`.

Eight additional modules have since been reconstructed from direct regions of
the historical packed bundle. They are documented separately as
bundle-derived reconstructions, not recovered source. The 27 bundle-derived candidate regions have since been promoted in
separately documented reconstruction commits. Four unresolved filenames still
require reconstruction. The
packed `jscn.js` and compressed output are unchanged.

The recovered source is intended to restore the original source layout and
make provenance explicit. It is not a claim that every missing module or
packed artifact has been reconstructed.

## Corroborating public copy

The same readable source archive is also preserved by the public
`ThiyagarajanJayaraman/openMAXIMS` fork. Its archive was first committed there
on 2014-06-13, before the corresponding archive commit in
`pacharanero/openmaxims-linux` on 2014-06-16. The two public ZIP files are
byte-for-byte identical:

```text
Source archive SHA-256:
aa5d3c3ae696d81697ba764b7ffac6f6135baf02c936867fcac37964033e92e8
```

The two public packed clients are also byte-for-byte identical, with
decompressed SHA-256:

```text
839d859c829ab71e56de7cd7138cd0bbd7723d224646b5589b7c7aebee6fbd94
```

This branch retains the valid archive in
`WebApp/jsCN/source/sources.zip` within the preserved
`openmaxims_workspace-archive/` tree. The corrupted upstream
`openmaxims_workspace/WebApp/jsCN/source/sources.zip` remains as evidence and
is not silently replaced.

Public corroborating locations:

- `pacharanero/openmaxims-linux` —
  `openmaxims_workspace/WebApp/jsCN/source/sources.zip`
- `ThiyagarajanJayaraman/openMAXIMS` —
  `Source Library/openmaxims_workspace/WebApp/jsCN/source/sources.zip`

The public `LibreHIS/librehis` fork provides a third corroborating history. It
also carried the same valid 74-module archive under its preserved
`openmaxims_workspace-archive/` tree, although that archive was later removed
from the fork's current working tree. Its history therefore confirms the
archive's wider public provenance, but does not provide additional modules.

LibreHIS also independently repaired `WebApp/jsCN/forminit.js`: commit
`98a7041` replaced a corrupted Java-source blob with the historical JavaScript
bootstrap. This is useful evidence for the bootstrap's provenance, but it is
not a standards-browser port or a complete recovery of the later source tree.

Additional corroborating location:

- [`LibreHIS/librehis`](https://github.com/LibreHIS/librehis) — historical
  `openmaxims_workspace-archive/WebApp/jsCN/source/sources.zip`
- [`forminit.js repair`](https://github.com/LibreHIS/librehis/commit/98a7041e7c8fb1f6524ff33e4afd99d250f41be7)
