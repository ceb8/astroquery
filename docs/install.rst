
Installation
============

Uniquely in the Astropy ecosystem, Astroquery is operating with a **continuous deployment model**.
It means that a release is instantaneously available after a pull request has been merged. These
releases are automatically uploaded to `PyPI <https://pypi.org/project/astroquery/#history>`__,
and therefore the latest version of astroquery can be pip installed.
The version number of these automated releases contain the ``'dev'`` tag, thus pip needs to be told
to look for these releases during an upgrade, using the ``--pre`` install option. If astroquery is
already installed, please make sure you use the ``--upgrade`` install option as well.

Installing with pip
-------------------

.. code-block:: bash

    $ pip install --pre astroquery

To install all the mandatory and optional dependencies add the ``[all]``
identifyer to the pip command above (or use ``[docs]`` or ``[test]`` for the
dependencies required to build the documentation or run the tests):

.. code-block:: bash

    $ pip install --pre astroquery[all]

In addition to the automated releases, we also keep doing regular, tagged version for maintenance
and packaging purposes. These can be ``pip`` installed without the ``--pre`` option and
are also available from the ``conda-forge`` conda channel.

.. code-block:: bash

    $ conda install -c conda-forge astroquery

To review recent changes and fixes, please have a look at the changelog:

.. toctree::
   :maxdepth: 1

   changelog


Building from source
--------------------

The development version can be obtained and installed from github:

.. code-block:: bash

    $ # If you have a github account:
    $ git clone git@github.com:astropy/astroquery.git
    $ # If you do not:
    $ git clone https://github.com/astropy/astroquery.git
    $ cd astroquery
    $ python setup.py install

Requirements
------------

Astroquery works with Python 3.7 or later.

The following packages are required for astroquery installation & use:

* `numpy <http://www.numpy.org>`_ >= 1.18
* `astropy <http://www.astropy.org>`__ (>=4.2.1)
* `pyVO`_ (>=1.1)
* `requests <https://requests.readthedocs.io/en/latest/>`_
* `keyring <https://pypi.python.org/pypi/keyring>`_
* `Beautiful Soup <https://www.crummy.com/software/BeautifulSoup/>`_
* `html5lib <https://pypi.python.org/pypi/html5lib>`_

and for running the tests:

* `curl <https://curl.haxx.se/>`__
* `pytest-astropy <https://github.com/astropy/pytest-astropy>`__
* `pytest-rerunfailures <https://github.com/pytest-dev/pytest-rerunfailures>`__

The following packages are optional dependencies and are required for the
full functionality of the `~astroquery.cds` module:

* `astropy-healpix <http://astropy-healpix.readthedocs.io/en/latest/>`_
* `regions <https://astropy-regions.readthedocs.io/en/latest/>`_
* `mocpy <https://cds-astro.github.io/mocpy/>`_ >= 0.9

For the `~astroquery.vamdc` module:

* `vamdclib <https://github.com/VAMDC/vamdclib/>`_  install version from
  personal fork: ``pip install git+https://github.com/keflavich/vamdclib-1.git``

The following packages are optional dependencies and are required for the
full functionality of the `~astroquery.mast` module:

* `boto3 <https://boto3.readthedocs.io/>`_
