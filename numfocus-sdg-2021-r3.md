The NumFOCUS small development grants program
=============================================

1 - Name of the submitter
---------------------

Sebastian M. Ernst


2 - E-mail direction
--------------------

ernst@pleiszenburg.de


3 - Nature of the software
--------------------------

Affiliated -> Other -> poliastro


4 - Proposal title
------------------

Array types for scaling for poliastro


5 - Two-sentence summary
------------------------

At the moment, while excellent for individual computations, `poliastro` does not scale well to many parallel and array-like computations - e.g. propagating many orbits or many transfer solutions - as required by a lot of contemporary research. This will introduce array types and related infrastructure into `poliastro`.


6 - Description of the proposal
-------------------------------

`poliastro` is an open source (MIT) pure Python library for interactive Astrodynamics and Orbital Mechanics, with a focus on ease of use, speed, and quick visualization. It provides a simple and intuitive API, and handles physical quantities with units.

In its current state, next to other closely related features, `poliastro` provides a [broad range of methods or algorithms](https://docs.poliastro.space/en/stable/quickstart.html) for propagating orbits, studying perturbations, studying spacecraft maneuvers and computing transfers. Similar to other open source software in this domain, `poliastro` focuses on individual solutions, e.g. the propagation of one individual orbit to one individual point in time. Until recently, this was good enough for the majority of professionals and students alike in the fields of astrodynamics and mission design.

A lot of contemporary research, however, has began to require a lot of computations of this kind at once. As a simple example, instead of plotting an individual orbit, a potential user may want to plot a large quantity of orbits at once. On a related subject, so called "[porkchop plots](https://docs.poliastro.space/en/stable/examples/Porkchops%20with%20poliastro.html)", a tool common in space mission design, require the computation of many transfers. Taking this one step further, a potential user may require a large quantity of porkchop plots or their underlying data for analysis at once.

Working with `poliastro` in its current form inevitable involves working with iterative processes and loops. Although `poliastro` JIT-compiles most of its performance-critical functions internally by relying on [numba](https://numba.pydata.org/), iterative operations of this kind are rather slow due to `poliastro`'s current internal design.

The proposed work aims to change that. It is intended to re-work `poliastro`'s internals in such a way that array-like operations become feasible. In a subsequent step, at least one new array type, orbit arrays, is introduced. Furthermore, the API of at least one existing type, the `Orbit` class, is also extended to demonstrate the capabilities of the library's internal design changes and to guide other developers in the correct usage of the added capabilities.

The proposal's author has more than one year of experience using `poliastro` professionally. All of the proposed changes have been tested and studied prior to submitting this proposal in a separate, [dedicated Github repository](https://github.com/pleiszenburg/bulk_lambert). Next to significantly improved usability, depending on the algorithm and the size of input data, speedups of one to three orders of magnitude can be expected for relevant computations.

7 - Benefit to project and community
-------------------------------------

Currently highly active topics of research requiring the described ability to scale include the following, among others:

- Studies on the entire populations of Earth satellites, about 7k at the moment, including both operational and inactive ones.
- Analysis of clouds of space debris, both real ones and models of potential satellite collisions. There are an estimated [0.33M objects larger than 1mm orbiting Earth as of August 2021](https://www.esa.int/Safety_Security/Space_Debris/Space_debris_by_the_numbers).
- Studies on the space debris mitigation and its removal, e.g. removing as many pieces of space debris with as little effort as possible
- Models of asteroid or even dust particle populations in the solar system. At the time of writing (September 2021) there have been more than one million unique objects identified in the solar system.
- The ongoing search for machine learning applications in orbit analysis and mission design.

From a technical point of view, the proposed changes will allow `poliastro` to leverage even more features of well-established NumFOCUS projects such as `numpy`. The developers of `poliastro` will be given a new set of internal APIs applying the proposed changes for more algorithms in future. [Early experiments](https://github.com/pleiszenburg/bulk_lambert/tree/master/bulk_lambert/cuda) also show that the proposed work paves the way for `poliastro` to access GPUs for computations in a meaningful and easy way.

The proposed changes will give `poliastro` a rather unique set of features and capabilities in the domain of astrodynamics and mission design. This will furthermore strengthen its position in the ecosystem. It is very likely going to help to attract new users, developers and resources. The proposed changes are already a [much desired](https://github.com/poliastro/poliastro/issues/1008) by the `poliastro` community.


8 - Amount requested
--------------------

Total amount requested: 5k USD


9 - Budget justification
------------------------

The proposed work is expected to require 100 working hours.

`5k USD == 100 * [hours] * 50.00 [USD / hour]`


10 - Timeline of deliverables
-----------------------------

The work will be carried out in a constant dialogue with `poliastro` developers across a time-span of four months, from October 2021 to January 2022.

The following deliverables are covered (with their estimated percentage of required work hours):

* 50%: Re-factoring of existing internal infrastructure.
* 15%: Adding at least one array-like data type to the library, resembling existing ones: from the `Orbit` class to an "Orbit array" class.
* 5%: Adding at least one new method to an existing data type which is returning arrays: `propagate_many` allows a single `Orbit` object to be propagated to many different positions or points in time, respectively.
* 5%: A minimal set of benchmarks for future verification of the performance of the additions.
* 25%: Matching tests for all added features.
