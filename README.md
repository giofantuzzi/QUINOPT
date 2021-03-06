# QUINOPT (QUadratic INtegral OPTimisation)
An open-source add-on for YALMIP to solve optimisation problems with polynomial quadratic integral inequality constraints. Below is a quick guide to QUINOPT, but details, examples, and much more can be found in the [full online documentation](http://quinopt.readthedocs.io/).

* **Latest release:** 2.2
* **Release date:** 04 May 2018
* **Release notes:**
	- Fixed bug preventing the solution of problems with inhomogeneous inequalities
	- Minor improvements to problem formulation
* **Known bugs in version 2.2:**
    - Outer approximation for integral inequalities with derivatives appearing only in the boundary conditions fail to compile. This issue affects [example09.m](https://github.com/aeroimperial-optimization/QUINOPT/blob/master/examples/example09.m), see the note at the bottom of [this doc page](https://quinopt.readthedocs.io/04_examples/planeCouetteBF.html).
      Fixed on 28 May 2019, please update to v 2.2.1 or download the latest version of the file [expandBoundaryVals2.m](https://github.com/aeroimperial-optimization/QUINOPT/blob/master/utils/LegendreExpansion/private/expandBoundaryVals2.m).

## Contents
- [System requirements](#Requirements)
- [License](#License)
- [Installation](#Install)
- [Getting started](#GettingStarted)
- [How to cite](#Cite)
- [Copyright](#Copyright)

## System requirements<a name="Requirements"></a>

In order to use QUINOPT, you will need:

1. A working version of [YALMIP](https://yalmip.github.io/), the MATLAB optimization modelling software by J. L&ouml;fberg. It is recommended that you use our own in-house fork, [aeroimperial-yalmip](https://github.com/aeroimperial-optimization/aeroimperial-yalmip)
2. A suitable SDP solver. Choices include [SeDuMi](https://github.com/sqlp/sedumi), [SDPT3](http://www.math.nus.edu.sg/~mattohkc/sdpt3.html), [SDPA](http://sdpa.sourceforge.net/), [Mosek](https://www.mosek.com/) (free for
    users in academia).

Instructions on how to obtain YALMIP and an SDP solver are given in the [Installation](#Installation) section below.

**Note:** QUINOPT has been successfully tested on MATLAB 7.10  (R2010a) and higher. If you have a different version of MATLAB, use at your own risk!

## License<a name="License"></a>

QUINOPT is distributed under the [Apache 2.0 licence](http://www.apache.org/licenses/LICENSE-2.0):

Copyright 2016, G. Fantuzzi, A. Wynn, P. Goulart, A. Papachristodoulou

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

## Installation<a name="Install"></a>

To install QUINOPT:

1. Install [aeroimperial-yalmip](https://github.com/aeroimperial-optimization/aeroimperial-yalmip)
2. Install a semidefinite programming (SDP) solver compatible with YALMIP. [Click here for a complete list of YALMIP-compatible SDP solvers](https://yalmip.github.io/allsolvers/).  
3. Install QUINOPT by running the MATLAB installer:

```Matlab
>> installQUINOPT
```

The installer should compile the required files, add the required folders to the MATLAB path, and run some test problems to make sure everything is working.
Please report any installation problems to Giovanni Fantuzzi (gf910[at]ic.ac.uk).

**NOTES:**
1. During installation, you may receive the following warning:
	_Warning: Compilation of mex files by installQUINOPT failed.
	QUINOPT will still work without compiled mex files, but
	it will be slower. To resolve the issue, make sure that
	a supported compiler is installed and re-run the installer._
	QUINOPT should still work, but you may wish to resolve the issue with the
	mex file compilation. You can find a list of supported compilers for
	MATLAB's latest version
	[here](https://uk.mathworks.com/support/compilers.html); for all other
	versions of MATLAB please [look at this page](https://uk.mathworks.com/support/sysreq/previous_releases.html).
2. QUINOPT has been tested with
  [SeDuMi](https://github.com/sqlp/sedumi),
  [SDPT3](http://www.math.nus.edu.sg/~mattohkc/sdpt3.html),
  [SDPA](http://sdpa.sourceforge.net/) and [Mosek](https://www.mosek.com/) (free for users in academia). Any other YALMIP-compatible SDP solver should work, but use them at your own risk!

## Getting started<a name="GettingStarted"></a>

To get started with QUINOPT, please look at the sample scripts provided the folder "./examples/". A step-by-step description of the examples can be found in the [online documentation](http://quinopt.readthedocs.io/04_examples/index.html).

For more information on the main functions in QUINOPT, please consult the documentation or type

```Matlab
>> help quinopt
>> help indvar
>> help depvar
>> help parameters
```

at MATLAB's command prompt.


## How to cite<a name="Cite"></a>

If you find QUINOPT useful, or have used it in your own work, please reference
it by citing the following papers:

* G. Fantuzzi, A. Wynn, P. Goulart, A. Papachristodoulou (2017). _Optimization
with affine homogeneous quadratic integral inequality constraints_. IEEE Transactions on Automatic Control 62(12), 6221-6236 . DOI: [10.1109/TAC.2017.2703927](https://doi.org/10.1109/TAC.2017.2703927).

 ```
 @article{FWGP2017TAC,
   author = {Fantuzzi, Giovanni and Wynn, Andrew and Goulart, Paul J. and Papachristodoulou, Antonis},
   doi = {10.1109/TAC.2017.2703927},
   journal = {IEEE Transactions on Automatic Control},
   number = {12},
   pages = {6221--6236},
   title = {{Optimization with affine homogeneous quadratic integral inequality constraints}},
   url = {https://doi.org/10.1109/TAC.2017.2703927},
   volume = {62},
   year = {2017}
   }
 ```

* G. Fantuzzi, A. Wynn (2016). _Semidefinite relaxation of a class of quadratic
 integral inequalities_. In: Proceedings of the 55th IEEE Conference on Decision and Control, Las Vegas (USA), 12-14 December 2016.
 DOI: [10.1109/CDC.2016.7799221](https://doi.org/10.1109/CDC.2016.7799221).

 ```
@inproceedings{FW2016CDC,
    address = {Las Vegas, USA},
    author = {Fantuzzi, G. and Wynn, A.},
    booktitle = {Proc. 55th IEEE Conf. Decis. Control},
    doi = {10.1109/CDC.2016.7799221},
    pages = {6192--6197},
    publisher = {IEEE},
    title = {{Semidefinite relaxation of a class of quadratic integral inequalities}},
    url = {http://dx.doi.org/10.1109/CDC.2016.7799221},
    volume = {2},
    year = {2016}
	}
 ```

Should you wish to cite the code directly, please use the following BibTeX entry, replacing ``X.X.X`` with the appropriate version of QUINOPT:

```
@misc{QUINOPTvX.X.X,
    author       = {Fantuzzi, Giovanni and Wynn, Andrew and Goulart, Paul and Papachristodoulou, Antonis},
    title        = {{QUINOPT}, version X.X.X},
    howpublished = {\url{https://github.com/aeroimperial-optimization/QUINOPT}},
    year         = 2017
    }
```

## Copyright<a name="Copyright"></a>
- Giovanni Fantuzzi (Department of Aeronautics, Imperial College London, UK. Email: giovanni.fantuzzi10[at]ic.ac.uk)  
- Andrew Wynn (Department of Aeronautics, Imperial College London, UK. Email: a.wynn[at]imperial.ac.uk)
- Paul Goulart (Department of Engineering Science, University of Oxford, UK. Email: paul.goulart[at]eng.ox.ac.uk)
- Antonis Papachristodoulou (Department of Engineering Science, University of Oxford, UK. Email: antonis[at]eng.ox.ac.uk)
