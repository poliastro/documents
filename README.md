The NumFOCUS small development grants program
=============================================

The NumFOCUS project is an organization who's mission is to promote open
practices in research, data and scientific computing by providing economical
support to open-source organizations. This financial help is partially done
trough its [sustainability
programs](https://numfocus.org/programs/sustainability). One of the programs,
the small development grants, calls for proposals three times a year. In
particular, last round deadline proposal is October 19, 2020.

It is possible for poliastro to apply for this third round. Therefore, a project
idea needs to be presented together with several objectives to achieve if
finally selected. Each proposal can obtain up to $5000\$$. This money can be
used for code and documentation development, website maintenance, workshops
and others. Only condition is proposed tasks to be completed before 2021
year. Any person, no matter its nationality or role (student, postdoc...) can
apply for the proposal once selected.

Resolution of accepted proposals will be announced on 27th, November 2020.


Project ideas for poliastro project during third round
======================================================

The [poliastro](https://github.com/poliastro/poliastro/) project is a pure
Python library focused in orbital mechanics computations by providing a simple
and powerful API. It has successfully participated  in other open-source
programs such us [Google Summer of Code](https://summerofcode.withgoogle.com/)
from which new and interesting implementations were merged into main source
code. [Project's documentation](https://docs.poliastro.space/en/latest/)
includes more information including [quick
guides](https://docs.poliastro.space/en/latest/user_guide.html) and a big
[tutorial gallery](https://docs.poliastro.space/en/latest/gallery.html).

<!-- Add example on AGI polistro usage -->
Moreover, different companies are using poliastro's routines into their orbital
mechanics software (orbit elements converters or propagation algorithms). For
example, IBM is using it in its [IBM Space Tech - Space Situational
Awareness](https://github.com/IBM/spacetech-ssa) and AGI **TODO**

In the following subsections, several ideas are presented as proposals for the
small development grants program. Some of them try to continue the actual line
of implementations of the project while other open new ones.


Extending Earth capabilities
----------------------------

At the moment, the project is focused on extending Earth capabilities due to
the interest increase in small satellites and missions which take place in
orbits around the planet. As a continuity of the [GSoC'20
edition](https://summerofcode.withgoogle.com/dashboard/project/6624764354887680/overview/),
the following features could be developed and included within future version of
the software:

* Extend `EarthSatellite` attribute and methods: specific maneuvers, minimum
  altitude variation orbits, rise and set times, close approach analysis...

* Enable poliastro to generate internal orbit objects from TLE. New specific
  propagators such us SGP4 are required for this task.

* Include more gravitational and atmospheric ones.

* Documentation usage on `EarthSatellite` and tutorials on its usage.


Validation and testing
----------------------

Many of the unit tests used by poliastro assume expected results found in
literature. Although most of those are easy to validate, some other routines
might be too complex to be found in introductory academical books or manuals,
imposing the need of alternative testing solutions. 

Different astrodynamics and orbital mechanics softwares are available in the
market but not all of them are open-source and script based. Among those, three
possible options arise: [Orekit](https://www.orekit.org/),
[GMAT](https://sourceforge.net/projects/gmat/) and
[AGI-STK](https://www.agi.com/products/stk).

Both GMAT and STK show a similar custom script syntax while Orekit recently
introduced a [Python
wrapper](https://gitlab.orekit.org/orekit-labs/python-wrapper/-/wikis/installation).
This API can be used to imitate actual poliastro's `Orbit` objects and test, for
example, three-dimensional two-body maneuvers. Only disadvantage is that Orekit
software uses Java as its main programming language being, therefore, not a pure
Python software.

Different tasks to solve and goals to achieve are listed in the following lines:

* Increase coverage by adding unitary tests to untested conditional
  sections in the code.

* Build an Okerkit based testing suite.

* Generate STK wrapper or validation API.


Three-body problem and N-body simulations
-----------------------------------------

At the moment, poliastro does not have any kind of n-body simulator. Although a
`threebody/` module exists, it only contains numerical functions focused on
patched conics and Lagrange points. This proposal would increase the amount of
features related with N-body simulations, and in particular with the three-body
problem. The following tasks might become a good starting point:

* Development of N-body integrator.

* Particular solutions, restricted three-body problem.

* Addition of documentation examples.


Timeline for the projects
=========================

If some of previous proposals is finally accepted, it will be announced 27th,
November. Because estimated time for all projects is 4 months, the NumFOCUS
program can be concatenated with the GSOC'21 edition, which ensures a continues
activity and development inside the poliastro community.
