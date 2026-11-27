### Improving astropy VO interoperability, with a focus on VOTable

**Proposal Category**: Innovations

### Project Team
This proposal is endorsed by the `io.votable` and `pyvo` maintainers. It
covers VO/VOTable tasks that have been recognised as important for a long time
but need focused development effort beyond the maintainer role.

The work will be carried out by Adrian Damian (@andamian), a `pyvo`
maintainer with VO and VOTable expertise. The other maintainers (@bsipocz,
@tomdonaldson, @stvoutsin) will help prioritise issues, review the work, and
coordinate it with `pyvo` development.

### Project Description / Scope of Work
`astropy.io.votable` is the foundation for VO data access in the ecosystem
(`pyvo`, `astroquery`, and downstream tools). There are currently 53 open
VOTable-related issues in `astropy`, many dating back to 2013–2019, covering
data loss on round-tripping, wrong dtypes, performance, and missing VO
standard features; `pyvo` has a further 75 open issues. This project makes
focused progress on that backlog, prioritised together with the `io.votable`
and `pyvo` maintainers.

#### High Priority Objectives
- **Ensure progress on longstanding issues that should be high priority**:
  most deliverables below address long-open `io.votable` bugs.
- **Improve and maintain interoperability with performant I/O file formats
  and libraries**: VOParquet support and VOTable read/write performance.
- **Improve the sustainability and maintenance of coordinated and affiliated
  packages**: `pyvo` and `astroquery` depend on `io.votable`; fixing it at the
  source removes workarounds downstream.
- **Provide support for reading and writing spectra using the IVOA
  SpectrumDM in specutils**: SpectrumDM serialisation relies on correct
  VOTable metadata (`GROUP`, `PARAM`, units, utypes), which this work improves.

#### Project / Work / Deliverables
Work is drawn from the [open `io.votable` issues][issues]. The first
priority is bugs that take one to several weeks each, followed by a bundle of
feature requests chosen with the maintainers. An issue triage is attached to
the PR description.

1. **Correctness and round-tripping** (core deliverable):
   - files astropy writes but cannot read back (#20457);
   - masked data handling (#20897, #8995, #18000);
   - wrong column dtypes, e.g. `char` read as `object`
     (#7480, #12892, #14505, #15352, #15394, #9414);
   - FIELD/INFO attribute handling (#11092, #9646, #17949, #8911);
   - duplicate column names (#20741);
   - QTable/mixin round-tripping (#18402, #9960, #6798);
   - booleans written as `bit` (#18277).
2. **Performance and scale**: slow reading/writing (#8191, #6519);
   chunked reading (#14577).
3. **VOParquet and unified I/O**: #18729, #18728, #17257, #20432,
   #15472, #15429.
4. **API consistency**: keyword-only arguments, warning control, and
   validator cleanup (#17224, #16314, #18667, #10389, #8775).
5. **VO metadata, as stretch goals**: `GROUP` support (#8705),
   file-level metadata (#7759), VO vocabularies (#18893),
   DataOrigin (#18059, #18057).
6. **Testing**: regression tests for every fix, plus filling coverage gaps
   (#9433, #15369).

Deliverables: merged PRs to `astropy` covering the items above, with tests and
changelog entries. Issues that turn out to need design discussion will be
written up for the maintainers instead.

[issues]: https://github.com/astropy/astropy/issues?q=is%3Aissue+state%3Aopen+label%3Aio.votable

### Approximate Budget
Currency: US $

The exact scope will be finalised based on availability. The rate is aligned
with other astropy contracts.

- Contractor fees: 1–2 months of full-time effort at $150/h
  (40 h × 4–8 weeks × $150): $24,000 – $48,000
- Travel: attendance at the IVOA Interop meeting (May 2027, Spain) to
  coordinate VOTable/VOParquet work with IVOA and data providers: $7,000
- TOTAL: $31,000 – $55,000

### Period of Performance
Jan 1, 2027 – Dec 31, 2027.
