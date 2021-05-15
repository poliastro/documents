---
geometry: margin=2.5cm
output: pdf_document
colorlinks: true
---

<!-- Build PDF using pandoc: $ pandoc report.md -o report.pdf -->

# Report for the NumFOCUS small development grants program


## Abstract

All the work performed during the lasts months regarding the [NumFOCUS Small
Development Grants Program 2020 3rd
round](https://numfocus.org/programs/small-development-grants) for
[poliastro](https://www.poliastro.space/) is collected and presented within this
document. A quick review on the original proposed objectives followed by the
problems encountered during their implementation together with the solutions
devised are explained. Links to all contributions are provided at the end of the
paper.


## Review of the original proposal

The main goal of the original proposal was to implement a validation framework
for testing all poliastro's capabilities for which no literature examples were
available. These capabilities included planetary reference frames transformations
and three-dimensional impulsive maneuvers, although orbital elements conversion 
and Keplerian propagation were also considered.

After a quick study on the possible solutions, validation against similar
software was selected as the best approach to solve for the problem. These
software were Orekit, GMAT and STK.

The following timeline of deliverables was devised for the whole program:

* The first two weeks would be devoted to get familiar with previous software
  and implement simple two-body problem validation cases (orbit element
  conversion and Keplerian propagation).

* First month fully devoted to the 3D impulsive maneuvers validation.

* The goal for the second was to simplify and reformat previous implementation
  (if required) in order to emulate poliastro's API.

* During the third month, all the effort would be directed towards the
  validation of planetary frames transformations.

* Last month was set with the idea of being used as a time-margin resource in
  case some of the previous points would take more than expected.


## Issues encountered and alternative approaches

During the first weeks of the program, it became evident that some of the
original proposed goals would required a different approach to be accomplished:

* **STK implementation.** We decided not to implement the validation against
  this software due to its lack of Linux compatibility. The GMAT and Orekit
  software were considered enough for the purposes of the validation work.

* **Suppression of poliastro's API emulation**. Trying to replicate the logic
  used by poliastro using the Orekit wrapper introduced an extra layer of
  complexity within the validation implementation. Therefore, this approach was
  deprecated in favor of direct comparison between pure Orekit API based tests
  and poliastro's ones.

* **GMAT not included in CI**. Although a solution for including this software
  within the continuous integration workflow was devised, it was rejected
  because its excessive complexity. Including GMAT meant downloading more than
  300MB every time the CI was triggered and building a Python wrapper to manage
  GMAT outputs. Therefore, only validation scripts were included as part of the
  testing process.

## Enhancements to the original proposal

In addition to the initial objectives, some others were also implemented:

* **Continuous integration setup**. By making use of GitHub's actions, it was
  possible to introduced a CI workflow within the main poliastro's repository
  which triggers the whole validation cases every time a new piece of code is
  merged into the main branch.


## Obtained results and benefits

Once all required poliastro's features were validated, the following results
arose:

* An error was detected in the Moon's rotational elements, which
  which introduced numerical differences of the order of 1E-5. These proved the
  frame validation logic to be successful.

* The frame logic inside poliastro's API was proof to be right. This logic could
  be expanded to the Astropy project, so other projects might benefit from
  this.

* Auxiliary frames, such us planetary-fixed non-parallel to ICRF, can be
  implemented.

* Groundtrack plots can be now extended to the rest of planets of the Solar
  System.


## Associated pull requests 

All the pull requests generated as a result of this work are listed down below,
being classified according to the repository in which they originated.


**validation repository**: https://github.com/poliastro/validation

* [Orekit validation first approach:](https://github.com/poliastro/validation/pull/4)
  https://github.com/poliastro/validation/pull/4

* [Create ci_actions.yml:](https://github.com/poliastro/validation/pull/7)
  https://github.com/poliastro/validation/pull/7

* [Stop tracking orekit-data.zip:](https://github.com/poliastro/validation/pull/9)
  https://github.com/poliastro/validation/pull/9

* [Enable repository dispatch from poliastro:](https://github.com/poliastro/validation/pull/11)
  https://github.com/poliastro/validation/pull/11

* [Maneuvers validation against Orekit:](https://github.com/poliastro/validation/pull/15)
  https://github.com/poliastro/validation/pull/15

* [Get rid of Orekit-based API:](https://github.com/poliastro/validation/pull/16)
  https://github.com/poliastro/validation/pull/16

* [Fix order of magnitudes:](https://github.com/poliastro/validation/pull/17)
  https://github.com/poliastro/validation/pull/17

* [Validate Hohmann 3D maneuver:](https://github.com/poliastro/validation/pull/18)
  https://github.com/poliastro/validation/pull/18

* [Bielliptic 3D maneuvers validation:](https://github.com/poliastro/validation/pull/19)
  https://github.com/poliastro/validation/pull/19

**poliastro repository**: https://github.com/poliastro/poliastro

* [Fix MoonFrame W angle value:](https://github.com/poliastro/poliastro/pull/1193)
  https://github.com/poliastro/poliastro/pull/1193

* [Add GitHub actions for triggering validation repo:](https://github.com/poliastro/poliastro/pull/1051)
  https://github.com/poliastro/poliastro/pull/1051

* [Disable validation trigger in PR:](https://github.com/poliastro/poliastro/pull/1181)
  https://github.com/poliastro/poliastro/pull/1181


## Future work

Regarding planetary frames validation, the rotational elements implemented in
Orekit software were taken from the [IAU WGCCRE 2009
report](https://astropedia.astrogeology.usgs.gov/download/Docs/WGCCRE/WGCCRE2009reprint.pdf)
while the ones from poliastro do from [IAU WGCCRE 2015
one](https://astropedia.astrogeology.usgs.gov/download/Docs/WGCCRE/WGCCRE2015reprint.pdf).
In issue to the official [Orekit's
repository](https://gitlab.orekit.org/orekit/orekit/) was opened to
suggest to update their rotational elements, see:

* [Update pole definitions to IAU WGCCRE 2015 report:](https://gitlab.orekit.org/orekit/orekit/-/issues/778)
  https://gitlab.orekit.org/orekit/orekit/-/issues/778

Finally, this validation approach might also be applied to test future
poliastro's capabilities. For example, propagation in non-inertial frames can
lead to [halo orbit's
implementation](https://github.com/poliastro/poliastro/issues/981) and
three-body sub-package enhancements. 
