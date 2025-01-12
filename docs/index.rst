.. ## Copyright (c) 2019-2022, Lawrence Livermore National Security, LLC and
.. ## other RADIUSS Project Developers. See the top-level COPYRIGHT file for details.
.. ##
.. ## SPDX-License-Identifier: (MIT)
.. ##

#################
RADIUSS Shared CI
#################

Here, we give an overview of the RADIUSS Shared CI project, which
contains CI infrastructure developed for RADIUSS projects.  RADIUSS
Shared CI is a sub-project of the LLNL RADIUSS project focusing on
sharing resource and documentation for Continuous Integration (CI) among
RADIUSS projects.

.. note::
   LLNL's RADIUSS project (Rapid Application Development via an Institutional
   Universal Software Stack) aims to broaden usage across LLNL and the open 
   source community of a set of libraries and tools used for HPC scientific 
   application development.

For more detailed information, please see the following documentation.

=======================================
RADIUSS Shared CI User Documentation
=======================================

  * :doc:`RADIUSS Shared CI User Guide <sphinx/user_guide/index>`

============================================
RADIUSS Shared CI Developer Documentation
============================================

  * :doc:`RADIUSS Shared CI Developer Guide <sphinx/dev_guide/index>`

=========================
Background and Motivation
=========================

Projects in the RADIUSS effort target the same machines and use the
`Spack packaging system <https://spack.io>`_ to ensure that they
build successfully with similar toolchains.

We designed an automated *CI infrastructure based on GitLab* that we meant to
sufficiently flexible to be shared among RADIUSS projects. The infrastructure
involves *using Spack to setup the project dependencies and generate build
configuration files*. This allows projects to easily *share the full context of
their builds*. The project is then built and tested as usual and most of *the
CI infrastructure is shared* to avoid duplication and reduce maintenance cost.

===========================================
Cool features provided by RADIUSS Shared CI
===========================================

* A shared configuration, for reduced maintenance.
* A core set of specs to build coherently with other projects.
* Ability to add extra specs.
* Uses GitLab child pipelines to keep the pipeline readable.
* Each child pipeline reports independently to GitHub.
* Project can extend their pipeline at will.

========
Overview
========

We organize the documentation around the three steps necessary to adopt
the RADIUSS Shared CI methodology. These steps are documented in
the :doc:`RADIUSS Shared CI User Guide <sphinx/user_guide/index>`.

1. **Use Spack to install dependencies and configure the project build.**
   Spack provides a single context to express *toolchains*, *machine
   setup*, and *build sequence*. Spack is increasingly used to install the
   dependency tree of large simulation codes.
2. **Build and test without breaking your habits.**
   We do not require the adoption of Spack to build your code but we require
   that your build system accepts the configuration file generated by Spack as
   an input (``CMakeCache.txt`` for a CMake build system). That way,
   dependencies and options are set coherently with the spec provided to build
   the dependency tree.
3. **Setup the CI using the shared template.**
   Once you have put in the effort to implement the first two steps, you should
   be able to benefit from the shared CI infrastructure. In a very complex
   scenario, you would still be able to use the RADIUSS Shared CI template as a
   starting point for a custom implementation.

In the  :doc:`RADIUSS Shared CI Developer Guide <sphinx/dev_guide/index>`,
we discuss the layout of the RADIUSS Shared CI infrastructure and how the
different pieces work together. Technical choices are also explained there.

.. toctree::
   :hidden:
   :caption: User Documentation

   sphinx/user_guide/index

.. toctree::
   :hidden:
   :caption: Developer Documentation

   sphinx/dev_guide/index
