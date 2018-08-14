[![Build Status](https://travis-ci.org/scivision/igrf12.svg?branch=master)](https://travis-ci.org/scivision/igrf12)
[![Coverage Status](https://coveralls.io/repos/github/scivision/igrf12/badge.svg?branch=master)](https://coveralls.io/github/scivision/igrf12?branch=master)
[![Python versions (PyPI)](https://img.shields.io/pypi/pyversions/igrf12.svg)](https://pypi.python.org/pypi/igrf12)
[![Distribution format (PyPI)](https://img.shields.io/pypi/format/igrf12.svg)](https://pypi.python.org/pypi/igrf12)
[![PyPi Download stats](http://pepy.tech/badge/igrf12)](http://pepy.tech/project/igrf12)

# IGRF 2012 in Python

International Geomagnetic Reference Field IGRF12 and IGRF11...in simple, object-oriented Python >= 3.6.

![image](tests/incldecl.png)

![image](tests/vectors.png)

## Install

To get the development version, `git clone` and then:

    python -m pip install -e .

Otherwise, for the latest release from PyPi:

    python -m pip install igrf12

Optionally, test the install with:

    pytest

## Example
To make the plots in this readme:
```sh
python RunIGRF.py
```

using as a Python module at geodetic coordinates 65N, 148W:
```python
import igrf12

mag = igrf12.igrf('2010-07-12', glat=65, glon=-148, alt_km=100)
```
returns an `xarray.Dataset`:
```
<xarray.Dataset>
Dimensions:  (alt_km: 1)
Coordinates:
  * alt_km   (alt_km) int64 100
Data variables:
    north    (alt_km) float64 1.122e+04
    east     (alt_km) float64 4.148e+03
    down     (alt_km) float64 5.302e+04
    total    (alt_km) float64 5.436e+04
    incl     (alt_km) float64 77.29
    decl     (alt_km) float64 20.29
```

The IGRF model may be specified with the `model=12` option, where `11` enacts IGRF11.

## Reference

If you only want the plain Fortran program, you can do:

```sh
cd bin

cmake ../src
cmake --build .

./testigrf
```

### References

-   [IGRF12 Fortran code](http://www.ngdc.noaa.gov/IAGA/vmod/igrf12.f)
-   [IGRF11 Fortran code](http://www.ngdc.noaa.gov/IAGA/vmod/igrf11.f)
-   WMM2015 [inclination map](https://www.ngdc.noaa.gov/geomag/WMM/data/WMM2015/WMM2015_I_MERC.pdf)
-   WMM2015 [declination map](https://www.ngdc.noaa.gov/geomag/WMM/data/WMM2015/WMM2015_D_MERC.pdf)