Using astroquery
================

All astroquery modules are supposed to follow the same API.  In its simplest form, the API involves
queries based on coordinates or object names.  Some simple examples, using SIMBAD:

.. doctest-remote-data::

    >>> from astroquery.simbad import Simbad
    >>> result_table = Simbad.query_object("m1")
    >>> result_table.pprint()
    MAIN_ID    RA      DEC    ... COO_WAVELENGTH COO_BIBCODE SCRIPT_NUMBER_ID
            "h:m:s"  "d:m:s"  ...
    ------- -------- -------- ... -------------- ----------- ----------------
      M   1 05 34 32 +22 00.8 ...              R                            1

All query tools allow coordinate-based queries:

.. doctest-remote-data::

    >>> from astropy import coordinates
    >>> import astropy.units as u
    >>> # works only for ICRS coordinates:
    >>> c = coordinates.SkyCoord("05h35m17.3s -05d23m28s", frame='icrs')
    >>> r = 5 * u.arcminute
    >>> result_table = Simbad.query_region(c, radius=r)
    >>> result_table.pprint(show_unit=True, max_width=80, max_lines=5)
            MAIN_ID               RA      ...     COO_BIBCODE     SCRIPT_NUMBER_ID
                               "h:m:s"    ...
    ----------------------- ------------- ... ------------------- ----------------
            NAME Ori Region   05 35 17.30 ...                                    1
                        ...           ... ...                 ...              ...
    2MASS J05353573-0525256 05 35 35.7755 ... 2020yCat.1350....0G                1
               V* V2114 Ori 05 35 01.6720 ... 2020yCat.1350....0G                1
    Length = 3273 rows

For additional guidance and examples, read the documentation for the individual services below.

.. _default_config:

Default configuration file
--------------------------

To customize this, copy the default configuration to ``$HOME/.astropy/config/astroquery.cfg``,
uncomment the relevant configuration item(s), and insert your desired value(s).

.. toctree::
  :maxdepth: 1

  configuration

Caching
-------

By default Astroquery employs query caching with a timeout of 1 week.
The user can clear their cache at any time, as well as suspend cache usage,
and change the cache location. Caching persists between Astroquery sessions.
If you know the service you are using has released new data recently, or if you believe you are
not recieving the newest data, try clearing the cache.


The Astroquery cache location is divided by service, so each service's cache should be managed invidually,
however whether the cache is active and the expiration time are controlled centrally through the
astroquery ``cache_conf`` module. Astroquery uses the Astropy configuration infrastructure, information about
temporarily or permanently changing configuration values can be found
`here <https://docs.astropy.org/en/latest/config/index.html>`_.

Shown here are the cache properties, using Simbad as an example:

.. code-block:: python

  >>> from astroquery import cache_conf
  >>> from astroquery.simbad import Simbad
  ...
  >>> # Is the cache active?
  >>> print(cache_conf.cache_active)
  True
  >>> # Cache timout in seconds
  >>> print(cache_conf.cache_timeout)
  604800
  >>> # Cache location
  >>> print(Simbad.cache_location)   # doctest: +IGNORE_OUTPUT
  /Users/username/.astropy/cache/astroquery/Simbad


To clear the cache:

.. code-block:: python

    >>> Simbad.clear_cache()
