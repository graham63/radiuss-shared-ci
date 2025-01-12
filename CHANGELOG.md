# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a
Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [v2022.03.0 - 2023-04-12]

### Added

- Support module specifications in the CI:
  -> Update you build_and_test script to load modules in $MODULE_LIST.

### Changed

- BREAKING: Set the build-and-test script command with a variable.
  -> Specify the build and test command in your .gitlab-ci.yml (see customization/gitlab-ci.yml).
- BREAKING: Machine checks jobs moved to parent pipeline:
  -> Update your .gitlab/subscribed-pipelines.yml w.r.t. customization/subscribed-pipelines.yml.
- BREAKING: Updated shared specs with current toolchains
  -> Update your extra jobs: local overrides will be outdated.

### Fixed

- Allow selected branches to skip the draft test: allow to run CI on develop.
- Restrict tioga CI to tioga11 runner, tioga10 has issues.
- Shorter working dir path in reproducer prevents issues when using local spack.

## [v2022.12.0 - 2022-12-14]

### Added

- Tioga machine.
- A job that tests whether the machine is up, and reports the failure to GitHub otherwise:
  machine is therefore skipped when down. (Assumes oslic is always up).
- Print a complete reproducer of the job.

### Changed

- Speed-up CI by not cloning the project in jobs only reporting to GitHub.
- Improved documentation, fixed links and syntax.
- BREAKING: now require to specify GitHub project name and organization for status reports.
- BREAKING: now require spack@v0.19.0, propagate flags using "==" syntax.

### Fixed

## [v2022.09.0 - 2022-09-09]

### Added

- New HowTo articles in documentation
- build-and-test file for Tioga

### Changed

- Modified file layout to work around issue with variable override
- Update xl compiler
- Update cuda is some xl specs

### Fixed

- Coherent job naming

## [v2022.08.1 - 2022-08-xx]

### Added

- Documentation regarding known issues.
- Report status for each sub-pipeline.
- Project can now specify global (custom) variants and dependencies.
- A How-To about global variants and dependencies.
- A How-To about choosing a spack reference in Uberenv.

### Changed

- Slurm allocation now uses command line option on project side (--overlap)
  instead of environment variable (SLURM_OVERLAP) in shared CI.
- Corona now uses Flux scheduler.

### Fix

- Wrong defaults in custom-variables file.
- Sub-pipeline status report works around Gitlab issue 216629.
- Corona used to include ruby allocation options.

## [v2022.08.0 - 2022-08-03]

### Changed

- Use protected double quotes in Spack specs, see https://github.com/LLNL/uberenv/pull/84.
- Dropped intel 18 compiler.

## [v2022.06.0 - 2022-06-13]

### Added

- Provide configuration for ruby, lassen and corona.

### Documentation

- Provide a first version of the documentation with user and developer guides.
