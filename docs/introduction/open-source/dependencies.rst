.. _introduction_open-source_deps:

Open Source dependencies
========================

Open Zaak would not be possible without a number of other Open Source dependencies.

Most notably, the backend is written in the Python_ programming language. We use the
Django_ framework to build the web-application (which includes the API of course) that
is Open Zaak.

The core elements for the API implementation are:

* `Django REST framework`_ (DRF), to implement the RESTful API
* `drf-yasg`_ to generate the API documentation in the form of OAS 3.0 specification
* `VNG-API-common`_, a re-usable library with some specific VNG/Dutch API tooling, built
  on top of DRF and drf-yasg

.. _Python: https://www.python.org/
.. _Django: https://www.djangoproject.com/
.. _Django REST framework: https://www.django-rest-framework.org/
.. _VNG-API-common: https://vng-api-common.readthedocs.io/en/latest/
.. _drf-yasg: https://drf-yasg.readthedocs.io/en/stable/

What about the dependencies that don't have a 1.0.0 version (yet)?
------------------------------------------------------------------

Good question!

Most libraries follow semantic versioning, which takes the form of ``A.B.c`` version
numbering. In this pattern, ``A`` is the major version, ``B`` is the minor version and
``c`` is the patch version. Roughly speaking, if ``A`` increments, you can expect
breaking changes. If ``B`` increments, the changes are backwards compatible fixes and
new features, and if ``c`` changes, it's purely a bugfix release.

Libraries with a version like ``0.x.y`` are usually considering not-stable yet - as long
as no ``1.0.0`` release has happened, the internal API can change, or the project may
never reach that "maturity" you'd want.

If you look at our requirements_, you will see a couple of libraries that don't have a
1.0.0 version (yet). So, why do we depend on them, and is there a risk of depending on
them? Below, you can find the mitigations/reasoning why we decided to depend on them
anyway, in alphabetical order.


* ``cmislib-maykin==0.7.4`` - this package is a fork of a Python 2 library implementing
  the CMIS bindings. Maykin Media (one of the Open Zaak service providers) ported it to
  Python 3 and maintains this fork.

* ``coreschema==0.0.4`` is a transitive dependency of ``coreapi`` and ``drf-yasg``,
  which are both well-maintained. It is made by the same author as DRF itself.

* ``dictdiffer==0.8.0`` is not mission-critical and can easily be swapped out if needed.
  It's currently used to visualize changes obtained from audit trail records in the
  admin interface. The library is Open Source on Github, and could be forked if needed.

* ``django-auth-adfs-db==0.2.0`` is an add-on for ``django-auth-adfs``. Maykin Media is
  one of the maintainers.

* ``django-db-logger==0.1.7`` is a package authored and maintained by Maykin Media, and
  used in various other projects.

* ``django-extra-views==0.13.0`` is a popular Django package with a large community
  behind it. The original author is still active as well.

* ``django-loose-fk==0.7.1`` is a package authored by Maykin Media to serve Open Zaak. It
  can be considered an integral part of Open Zaak, but the code was separated out in a
  standalone package for easier maintenance.

* ``django-sendfile2==0.6.0`` is a fork of django-sendfile, focusing on Python 3 support.
  The core functionality is very stable and unlikely to cause problems.

* ``djangorestframework-camel-case==0.2.0`` is a fairly popular and standard DRF add-on.
  Schema generators like drf-yasg, drf-spectacular and DRF even have explicit support
  for this package.

* ``djangorestframework-gis==0.14`` is used for the GeoJSON serialization. We only use
  a small set of features, but it's the go-to GIS library in combination with DRF, and
  very stable despite the version numbering.

* ``drf-nested-routers==0.90.2`` sees regular maintenance and activity on Github, with
  high popularity.

* ``drf-writable-nested==0.4.3`` TODO

* ``gemma-zds-client==0.13.0``

* ``httplib2==0.18.1``

* ``humanize==0.5.1``

* ``inflection==0.3.1``

* ``iso-639==0.4.5``

* ``iso8601==0.1.12``

* ``isodate==0.6.0``

* ``nlx-url-rewriter==0.1.2``

* ``oyaml==0.7``

* ``python-dotenv==0.8.2``

* ``ruamel.yaml.clib==0.2.2``

* ``ruamel.yaml==0.16.7``

* ``sentry-sdk==0.16.5``

* ``sqlparse==0.3.0``

* ``zgw-consumers==0.12.2``

.. _`requirements`: https://github.com/open-zaak/open-zaak/blob/master/requirements/base.txt
