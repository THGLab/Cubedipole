# Cubedipole.x
The code can calculate the bond dipole moment, starting from the charge density and electron density cube files that were produced using CP2K software.

The steps to perform the calculation are as below:
1. Using CP2K software to perform a static calculation that produce both charge density (PROJECT-TOTAL_DENSITY-1_0.cube) and electron density (PROJECT-ELECTRON_DENSITY-1_0.cube) cube files. The corresponding CP2K input is "CP2K_INPUT / FORCE_EVAL / DFT / PRINT / TOT_DENSITY_CUBE" and "CP2K_INPUT / FORCE_EVAL / DFT / PRINT / E_DENSITY_CUBE".
2. Download the Bader code from http://theory.cm.utexas.edu/henkelman/code/bader/ and replace the file "" with the modified, and compile the Bader code.
3. Using the Bader to produce the electron partition file "grid_nion.cube" with the command "bader PROJECT-ELECTRON_DENSITY-1_0.cube -p all_atoms"
4. Compile the cubedipole code sucessfully, and then cubedipole.x can be used to perform dipole calculation. One can see the help menu by typing "cubedipole.x -h"
5. To calculate the molecular dipole moment, simply type "cubedipole.x -md -p PROJECT"; To calculate the dipole moment for all bonds within the molecule, simpy type "cubedipole.x -bd_all -p PROJECT"; To calculate the dipole moment for a fragment, prepare a file "fragment_groups" in the executive path and type "cubedipole -fd -p PROJECT".
