# ACSE 9 Independent Research Project
## Author: Devang Patel
## Supervisors:
- Prof. Dominik Weiss (Imperial College London, UK)
- Dr. James Percival (Imperial College London, UK)
- Prof. Patricia Hunt (Victoria University of Wellington, NZ)

### This code was written for my ACSE MSc research project from 1st June - 27th August 2021. It calculates the reduced partition function ratio between 2 singly substituted isotopologues by extracting their vibrational frequencies from Gaussian log files.

### Layout

#### Modules

`calculations` - module that contains functions to calculate the reduced partition function ratio

`extractions` - module that contains functions that extract frequencies, temperature and isotopic information from a Gaussian log file

`file_io` - module for checking file existence and inspecting files

`isotope_contribution` - module that contains functions to ascertain isotope vibrations for frequencies, and a csv file `atomic_number.csv` used as a lookup table for atomic numbers of elements,

#### Folders
`input_files` - folder to store input files

`output_files` - folder to store output files

`tests` - contains log files, command line outputs, and an excel spreadsheet `calculations.xlsx` used in testing extraction, calculation + `script.py` functionality.

#### Files
`environment.yml` - depedency installation file for Anaconda

`requirements.txt` - dependency installation file for Pip

#### Scripts
`scripts.py` - Main script for calculation of the reduced partition function. See below for usage instructions.

`tests.py` - Script to run extraction and calculation tests with ZnCl4 and ZnH2O log files.

### Installation / Usage Instructions

To download the code, either download as a .zip file, or if you have Git installed, run:
```
git clone https://github.com/endevor-music/rpfr_calculator.git
```

To be on the safe side, ensure you are in the root directory before creating/activating a virtual environment.

### Windows

#### Pip

To create and activate the virtual environment (venv) and install the required packages WITHIN the root directory, run:

```
python -m venv venv 
venv\Scripts\activate.bat
pip install -r requirements.txt
```

To deactivate, run:
```
venv\Scripts\deactivate.bat
```

#### Anaconda - https://www.anaconda.com/

Once Anaconda is installed, ensure the Anaconda Prompt terminal, indicated by `(base)` is running.

To create a virtual environment, install the required packages and activate the environment run:

```
conda env create --name venv --file environment.yml
conda activate venv
``` 

To deactivate run
```
conda deactivate
```

### Linux - Ubuntu

#### Pip

Installing Pip and the venv module:
```
$ sudo apt install python3-pip
$ sudo apt install python3.8-venv
```

Installing and activating the virtual environment:
```
$ python3 -m venv venv
$ source venv/bin/activate
$ pip install -r requirements.txt
```
Deactivating the virtual environment:
```
$ deactivate
```
### Running the script

To run the python script, run 
```
(venv) python script.py arg1 arg2 arg3 arg4 arg5
```

with the argument list as follows:
- `arg1` - path to light isotopic log file e.g. `./tests/log_files/zinc/ZNCL4_B_64.log`
- `arg2` - path to heavy isotopic log file e.g. `./tests/log_files/zinc/ZNCL4_B_66.log`
- `arg3`
  - `y` if the molecule is linear
  - `n` if the molecule in non-linear
- `arg4` - path to output file e.g. `./output_files/file.txt` - can be anything the user wishes
- `arg5` - print variable
  - `False`: prints out just basic information (input filenames, temperature, reduced partition function ratio)
  - `True`: prints out basic info + extra information (item convergence table, low frequencies)

For example, running the following:

```
python script.py tests/log_files/zinc/ZNCL4_B_64.LOG tests/log_files/zinc/ZNCL4_B_66.LOG n ./output_files/file.txt True
```

would run the program on the input files (`tests/log_files/zinc/ZNCL4_B_64.LOG` and `tests/log_files/zinc/ZNCL4_B_66.LOG`), and calculate the expected frequencies given the molecule is non-linear (due to `n`), and output all extracted data (`True`) to the output file `./output_files/file.txt`.

#### Running tests

To run basic tests, simply run `tests.py`. Currently the test functions for extractions and calculations are run using the ZnCl4 ans ZnH2O log files in `./tests/test_files`.

A collection of files to view the functionality of `script.py` with respect to the presence/absence of temperature, isotopic information and frequencies in log files is available to view in `tests\log_files\water\`.

To save the command line output of the tests to a file to view at a later time (e.g. `tests\log_files\water\frequency\outputs\H2O_both_freq_cmd.txt`), run:

```
python script.py <argument list> > <path_to_file>
```

### Licensing

MIT License
