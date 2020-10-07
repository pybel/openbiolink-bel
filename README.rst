BEL Export of OpenBioLink
=========================
This repository used to contain exports of `OpenBioLink <https://github.com/openbiolink/openbiolink>`_
as `Biological Expression Language (BEL) <http://cthoyt.gitbook.io/bel>`_. Now, the exports are
available directly through their Zenodo page |zenodo|. The research article describing
OpenBioLink is:

  `OpenBioLink: A benchmarking framework for large-scale biomedical link prediction <https://doi.org/10.1093/bioinformatics/btaa274>`_
  Breit, A., Ott, S., Agibetov, A., & Samwald, M.
  *Bioinformatics* (2020)

BEL is a domain specific language that enables the expression of biological relationships
in a machine-readable format. It is supported by the `PyBEL <https://github.com/pybel/pybel>`_
software ecosystem.

Download OpenBioLink as BEL
---------------------------
The network is available in two BEL formats:

- **BEL Script** - see description `below <https://github.com/pybel/openbiolink-bel#bel-script>`_
- **Nodelink JSON** - see description `below <https://github.com/pybel/openbiolink-bel#nodelink-json>`_

Format Descriptions
-------------------
BEL Script
~~~~~~~~~~
BEL Script is the *de facto* standard for BEL, which all BEL-aware applications should be able to consume.
It contains information about the nodes, edges, and their biological context in a domain-specific language.
It can be parsed with PyBEL or other BEL parsers.

The BEL Script is available from this URL: https://zenodo.org/record/3834052/files/openbiolink.bel.gz.
If there's an update on Zenodo, update the record accordingly.

Example opening BEL Script using `pybel.from_bel_script_gz() <https://pybel.readthedocs.io/en/latest/reference/io.html#pybel.from_bel_script_gz>`_:

.. code-block:: python

    from pybel import from_bel_script_gz
    graph = from_bel_script_gz('openbiolink.bel.gz')

Nodelink JSON
~~~~~~~~~~~~~
Node-link is the format popularized by Javascript frameworks like D3 for representing network
information. Since the main data structire in PyBEL is a network, it often makes sense to use
Nodelink JSON as a pre-compiled data structure for BEL (since parsing/compiling BEL takes a
lot longer than JSON). The schema is specific to PyBEL, but this is the fastest to load.

The BEL Script is available from this URL: https://zenodo.org/record/3834052/files/openbiolink.bel.nodelink.json.gz?download=1.
If there's an update on Zenodo, update the record accordingly.

Example opening Nodelink JSON using `pybel.from_nodelink_gz()
<https://pybel.readthedocs.io/en/latest/reference/io.html#pybel.from_nodelink_gz>`_:

.. code-block:: python

    from pybel import from_nodelink_gz
    graph = from_nodelink_gz('openbiolink.bel.nodelink.json.gz')
    
.. |zenodo| image:: https://zenodo.org/badge/DOI/10.5281/zenodo.3834052.svg
   :target: https://doi.org/10.5281/zenodo.3834052
