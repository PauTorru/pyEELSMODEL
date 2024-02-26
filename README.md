# pyEELSMODEL
pyEELSMODEL is a electron energy loss spectroscopy software based on the former [c++ software](https://github.com/joverbee/eelsmodel).
This software uses the model-based approach to quantify EEL spectra. 

Installing
----------
The easiest way is installing pyEELSMODEL via pip:
```bash
pip install pyEELSMODEL
```
If you want to install the development version of pyEELSMODEL, you can 
install it from source. The first step is to clone the repository using:
``` bash
git clone https://github.com/joverbee/pyEELSMODEL.git
```
Navigate to the pyEELSMODEL directory and install pyEELSMODEL:
``` bash
pip install -e .
```
After installation, the generalized oscillator strengths (GOS) tables should be imported.
The GOS tables are necessary to perform EEL quantification since they are used
to calculate the atomic cross sections. Two different GOS tables can be used for quantification:
1. The GOS calculated by Zhang Z. *et al.* which can be found at doi:[10.5281/zenodo.7729585](https://doi.org/10.5281/zenodo.7729585).
2. The GOS calculated by Segger L. *et al.* which can be found at doi:[10.5281/zenodo.7645765](https://doi.org/10.5281/zenodo.7645765).

#### Setting up GOS array from Zhang Z.
Following steps explain on how the properly setup the GOS array of 
Zhang Z. 
1. Download the Dirac_GOS_database.zip file
2. Unzip the file
3. Copy the *.hdf5 files in the folder to .\database\Zhang folder which is found in the pyEELSMODEL folder

**The GOS tables from Zhang are used as default in the quantification workflows so they are necessary to run the example notebooks.**

#### Setting up GOS array from Segger L.
Following steps explain on how the properly setup the GOS array of 
Segger L.
1. Download the Segger_Guzzinati_Kohl_1.5.0.gosh (depends on version) file
2. Copy the .gosh file to .\database\Segger_Guzzinati_Kohl folder which is found in the pyEELSMODEL folder


Using
-----
```python
import pyEELSMODEL.api as em
import numpy as np

size=1024
offset = 100 #[eV]
dispersion = 0.5 #[eV]

specshape = em.Spectrumshape(dispersion, offset, size)
data_array = np.random.random(size)

s = em.Spectrum(specshape, data=data_array)
s.plot() 
```
For more examples on how to use pyEELSMODEL, check the ./examples folder. 

License
-------
The project is licensed under the GPLv3 license
































