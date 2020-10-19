The NumFOCUS small development grants program
=============================================

1 - Name of the submitter
---------------------

Jorge Martínez Garrido


2 - E-mail direction
--------------------

jorge@on-orbit.dev


3 - Nature of the software
--------------------------

Affiliated -> Other -> poliastro


4 - Proposal title
------------------

New validation framework for poliastro


5 - Two-sentence summary
------------------------

Design and build a validation framework in order to test and compare poliastro
against similar astrodynamics and orbital mechanics software.


6 - Description of the proposal
-------------------------------

poliastro is an open source (MIT) Python library for interactive
Astrodynamics and Orbital Mechanics, focusing on interplanetary applications. It
provides a simple and intuitive API and handles physical quantities with units.

As it happens with many other scientific packages, it relies on unit tests to
ensure accuracy of numerical results. Those expected values come from a variety
of literature resources: manuals, books, journals, articles... However, some
routines can not be tested because their complexity is out of the scope of
academical materials: validation of spacecraft 3-D maneuvers, testing of
planetary reference frames...

This testing complexity can be addressed by designing and building a validation framework
against similar software. This testing environment can lead to an increase
of numerical accuracy while adding a complete new set of unit and integration tests for core
astrodynamics routines.
 
Among similar software candidates, we find GMAT, Orekit, and STK. All of
them can be used through script files and provide custom API interfaces for
Python, which makes them ideal for the generation of new test cases and their
validation against poliastro.
All of them are free to use and OS-independent except for STK, which
requires a Windows system.

This new validation framework would not be included within actual software but
in a separate repository inside the poliastro GitHub organization.
Results obtained from it will yield insightful information about the current code
and bug fixes will be made directly to poliastro.

Not only that, by generating a custom testing framework, more complex routines
could be implemented in a faster and reliable way such us Earth focused
capabilities, restricted three-body problem, relative motion, halo-orbits,
low-thrust maneuvers, and more.


7 - Benefit to project and community
-------------------------------------

The poliastro project is a well known orbital mechanics software in the
open-source community because its participation in different congresses and coding
internship programmes. Each day, more users and companies benefit from its open-source
nature by building custom applications on top of poliastro's API. However, some
of them require from high accurate results and cannot afford failure. This
implies robust testing background cases if poliastro wants to maintain its
code-quality within the scientific community.

From previous situation different benefits arise to community and the project:

- Users can rely on output computations and expect from those huge accuracy.

- poliastro can get code coverage closer to 100% and maintain this ratio in
  the long term. For example, future
  Earth focused routines or restricted 3-body problem implementations could be
  easily shipped and tested. 

- Process followed in this framework can be adapted to similar scientific
  packages, so more projects can benefit from its development.


8 - Amount requested
--------------------

Total amount requested: 3000$


9 - Budget justification
------------------------

The project, as depicted in the "Timeline" section of this proposal, is expected
to be completed within 4 months, from December'20 until the end of March'21. The
grant will be used as student stipend, which is expected to assume a workload
of:

3000 USD = 16 [weeks] * 12.5 * [hour / week] * 15.00 [USD / hour]


10 - Timeline of deliverable
-----------------------------

* The first two weeks are devoted to the collection and design of the validation
  framework from the theoretical point of view. The project is expected to start
  either with Orekit or STK, being this last one the most preferred because of
  its importance in the industry.

* Once the framework has been theoretically defined, the rest of first month is
  devoted to the validation and testing of 3D maneuvers. By starting with this
  simple task, developers can get used to work with previous software: GMAT,
  Orekit or STK, building the first layers of the testing application.

* Workload during the second month is oriented towards the growth and maturity
  of the framework. Similar software APIs are simplified with new classes and
  objects which emulate poliastro's main ones: GmatOrbit, OrekitOrbit and
  StkOrbit might be implement similarly as poliastro's Orbit core class. 

* Third month is devoted to validation of reference frames and velocity
  transformations testing. This is a quite heavy which not only requires
  software knowledge but also a deep research on the topic. Failures or bugs might
  be expected during this big task, that is the reason behind the amount of time
  devoted to it.

* Last month is set as margin in case previous tasks took more time to
  implement, fixing of critical bugs and other critical and unexpected reasons.
  Code-coverage can also be implemented directly into poliastro's software.

