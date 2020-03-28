---
section: 32
x-masysma-name: masysmaci/pkgsync
title: Package Synchronization Job
date: 2020/03/28 20:55:50
lang: en-US
author: ["Linux-Fan, Ma_Sys.ma (Ma_Sys.ma@web.de)"]
keywords: ["masysmaci", "debian", "package", "reprepro", "ci", "mdpc2"]
x-masysma-version: 1.0
x-masysma-repository: https://www.github.com/m7a/co-pkgsync
x-masysma-website: http://masysma.lima-city.de/32/masysmaci_pkgsync.xhtml
x-masysma-owned: 1
x-masysma-copyright: |
  Copyright (c) 2019, 2020 Ma_Sys.ma.
  For further info send an e-mail to Ma_Sys.ma@web.de.
---
Description
===========

The Ma_Sys.ma CI Package Synchronization Job is used in conjunction with
[masysmaci/main(32)](masysmaci_main.xhtml) to synchronize generated packages
with a reprepro-Repository.

It automatically creates a new repository if it does not already exist.

The configured default values are expected to work out of the box in conjunction
with Ma_Sys.ma CI's default values. However, they are most likely insufficent
for productive non-Ma_Sys.ma use. See the next section for details that might
need changing.

Configuration
=============

This job is configured by various `mdpc` properties and other aspects defined
in `build.xml`. The details are explained in the following with default values
given after `=`.

`mdpc.repo=/data/programs/repo`
:   Configures the path of the repository to use.
    For Docker use, the default value is sufficent; for local use, it likely
    requires changing.

`mdpc.dist=squeeze`
:   A distribution name to use for the newly created repository. As this job
    only supports a single distribution, the use of distribution names is
    largely arbitrary. `squeeze` was Debian stable when the first version of
    MDPC (which this job originates from) was created.

`mdpc.version=6.0.6`
:   The version associated with the distribution. See `mdpc.dist`.

`mdpc.pubkey=/home/masysmaci/.gnupg/pubkey`
:   Location of the repository's public key.
    For Docker use, the default value is sufficent; for local use, it likely
    requires changing.

`mdpc.architectures=i386 amd64 armhf`
:   List of architectures contained in the repository. Must be a superset of
    the package's architectures that are to be included.

In addition to the properties, file `conf/distributions` contains interesting
properties like a label, description and suite for the repository to be created.
In case you want to customize the values prior to repository creation, edit them
in the respective `<echo>` tag in `build.xml`.

Requirements
============

This job works on Linux only and requires `reprepro` and `ant` to be present
and working. To add packages to the repository, the private GPG key used for
signing needs to be imported. Ma_Sys.ma CI's Docker container and default
configuration satisfy all of these dependencies.

License
=======

	Ma_Sys.ma CI Package Synchronization Job 1.0,
	Copyright (c) 2019, 2020 Ma_Sys.ma.
	For further info send an e-mail to Ma_Sys.ma@web.de.
	
	This program is free software: you can redistribute it and/or modify
	it under the terms of the GNU General Public License as published by
	the Free Software Foundation, either version 3 of the License, or
	(at your option) any later version.
	
	This program is distributed in the hope that it will be useful,
	but WITHOUT ANY WARRANTY; without even the implied warranty of
	MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
	GNU General Public License for more details.
	
	You should have received a copy of the GNU General Public License
	along with this program.  If not, see <http://www.gnu.org/licenses/>.
