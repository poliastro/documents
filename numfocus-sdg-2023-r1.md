The NumFOCUS small development grants program
=============================================

1 - Name of the submitter
---------------------

Jorge Martínez Garrido


2 - E-mail direction
--------------------

contact@jorgemartinez.space


3 - Nature of the software
--------------------------

Affiliated -> Other -> poliastro


4 - Proposal title
------------------

Enhancing the visualization capabilities of poliastro


5 - Two-sentence summary
------------------------

Implement a powerful and customizable visualization backend based on PyVista and
provide plotting animation capabilities to poliastro.


6 - Description of the proposal
-------------------------------

poliastro is an open source (MIT) pure Python library for interactive
Astrodynamics and Orbital Mechanics, with a focus on ease of use, speed, and
quick visualization. It provides a simple and intuitive API, and handles
physical quantities with units.

Visualizing astronomical objects together with their path and motion is a key
feature of any Astrodynamics library, including poliastro.

At the moment, poliastro supports two backends built on top of the Matplotlib
library and the Plotly library. Although these libraries provide support for
three-dimensional visualization, their capabilities are limitied. For example,
texturing or lightning are not supported.

A solution proposed during the SciPy 2022 conference was to create a new backend
based on PyVista. This library provides a Pythonic high-level API to The
Visualization Toolkit (VTK) library.

Cesium was also considered for precise visualization. However, this software
only supports the Earth as the main attractor. The reason is that Cesium focuses
on geospatial activities. In addition, Cesium requires from a web interface or
Jupyter notebook whereas PyVista can also be executed locally in a dedicated
window, alleviating the number of dependencies. PyVista also integrates with
various graphic user interfaces frameworks such us PyQT and PySide.

Another desired feature in poliastro is animated plots. This feature becomes
essential when simulating the evolution of a system. With animated plots, users
would be able to have better understanding on how the system evolves over time.

This last feature is supported by Matplotlib, Plotly and the new proposed
PyVista backends.


7 - Benefit to project and community
-------------------------------------

The coding sprints that took place at SciPy 2022 conference turned out to be an
excellent place to discuss with PyVista maintainers about using their library as
a new plotting backend for poliastro.
 
This proposal can generate the following benefits to the project and the
community:

* Users can generate and customize powerful and accurate visualizations and
  animations of their simulations using poliastro. This would bring poliastro a
  new 

* poliastro would still remain as a pure Python, as PyVista is a high-level
  Python wrapper of VTK. No need for maintainers and contributors to learn other
  programming languages or complex graphics APIs. Everything is implemented
  using Python.

* Generic features can be implemented upstreamed to PyVista so their users can
  benefit without requiring to install poliastro.
  
* Since PyVista is an affiliated NumFOCUS project, all the community can benefit
  from the grant in one way or another.

* The testing of the new backend can be performed using the pytest-pyvista
  plugin for pytest. The adoption of this plugin in poliastro can generate
  useful feedback for enhancing the plugin.

All the proposed features would allow poliastro to be closer to commercial
software while still remaining open-source and a reference project in the Python
scientific community.


8 - Amount requested
--------------------

Total amount requested: 4500$


9 - Budget justification
------------------------

The project, as depicted in the "Timeline" section of this proposal, is expected
to be completed within the course of 5 months. Starting date would be May 2023
and the project would be completed by the end of September 2023.

The grant is used as hourly rates and number of work hours for contractors. The
requested budget is justified as follows:

4500$ = 5 [month] * 15 [day / month] *  3 * [hour / day] * 20.00 [$ / hour] 


10 - Timeline of deliverable
-----------------------------

* The first month is devoted to implement the PyVista backend. The new backend
  must support Solar System textured bodies and loading of custom object models
  within the graphics scene. Tests for the new backend are required too.

* The second month and third month focus on the implementation of plotting
  animations. This is expected to be a more intensive workload, as it requires
  implementing this feature across three different backends, each one with its
  own architecture.

* With the new features, the next month is used to implement miscellaneous
  PyVista backend features and utilities like visualization of celestial frames,
  planes of reference and the celestial sphere containing an accurate
  representation of far stars.

* The last month is used in case some difficulties arise during the
  implementation of any of the previously proposed features.
