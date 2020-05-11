BEL Export of Hetionet
======================
This repository contains exports of `OpenBioLink <https://github.com/openbiolink/openbiolink>`_
as `Biological Expression Language (BEL) <http://cthoyt.gitbook.io/bel>`_. The research article describing
OpenBioLink is:

  `OpenBioLink: A benchmarking framework for large-scale biomedical link prediction <https://doi.org/10.1093/bioinformatics/btaa274>`_
  Breit, A., Ott, S., Agibetov, A., & Samwald, M.
  *Bioinformatics* (2020)

BEL is a domain specific language that enables the expression of biological relationships
in a machine-readable format. It is supported by the `PyBEL <https://github.com/pybel/pybel>`_
software ecosystem.

Download Hetionet as BEL
------------------------
The network is available in three BEL formats:

- **BEL Script** - see description `below <https://github.com/pybel/openbiolink-bel#bel-script>`_
- **Nodelink JSON** - see description `below <https://github.com/pybel/openbiolink-bel#nodelink-json>`_

Cloning
~~~~~~~
Large files in this repository are stored using `Git LFS <https://git-lfs.github.com/>`_.
When cloning this repository, please make sure that Git LFS is installed on your system.
Otherwise, git will checkout text pointers for large files rather than the large files
themselves!

License
-------
This repository redistributes content from `openbiolink/openbiolink <https://github.com/openbiolink/openbiolink>`_
and is licensed in the same way. See the `License <https://github.com/openbiolink/openbiolink#source-databases-and-their-licenses>`_
section of the original OpenBioLink repository.

Format Descriptions
-------------------
BEL Script
~~~~~~~~~~
BEL Script is the *de facto* standard for BEL, which all BEL-aware applications should be able to consume.
It contains information about the nodes, edges, and their biological context in a domain-specific language.
It can be parsed with PyBEL or other BEL parsers.

Example opening BEL Script using `pybel.from_bel_script() <https://pybel.readthedocs.io/en/latest/reference/io.html#pybel.from_bel_script>`_:

.. code-block:: python

    import gzip
    from pybel import from_bel_script
    with gzip.open('hetionet-v1.0.bel.gz') as file:
        graph = from_bel_script(file)

Nodelink JSON
~~~~~~~~~~~~~
Node-link is the format popularized by Javascript frameworks like D3 for representing network
information. Since the main data structire in PyBEL is a network, it often makes sense to use
Nodelink JSON as a pre-compiled data structure for BEL (since parsing/compiling BEL takes a
lot longer than JSON). The schema is specific to PyBEL, but this is the fastest to load.

Example opening Nodelink JSON using `pybel.from_nodelink_gz()
<https://pybel.readthedocs.io/en/latest/reference/io.html#pybel.from_nodelink_gz>`_:

.. code-block:: python

    from pybel import from_nodelink_gz
    graph = from_nodelink_gz('hetionet-v1.0.bel.nodelink.json.gz')
