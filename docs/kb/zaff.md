## Background
Zinc(II) ions are commonly bound by proteins, link to nucleic acid
recognision and binding. Zn<sup>2+</sup> has 10 valence electrons, which
warrants a tetrahedral coordination with four two-electron donors. 
Typically, these are (deprotonated) cysteines or histidines, sometimes
can be alcohol sidechains or water. These moieties are often called 
Zn fingers.

MM force fields generally rely on describing ion binding by non-bonding
interactions, electrostatics and van der Waals. This often breaks down 
with Zn fingers, partly because they do not account for the covalent 
character of the binding and because they ignore the charge transfer 
from Lewis base to acid. Therefore, keeping the formal 2+ charge on the 
zinc creates an electrostatic well polling in negative particles, and
since the size exclusion allows enough space for six ligands, often
results in an octahedral coordination around the metal ion.

## ZAFF
Zinc Amber Force Field (ZAFF) was 
[developed](https://doi.org/10.1021/acs.jctc.7b00773) 
to handle these issues, a useful 
[tutorial](https://ambermd.org/tutorials/advanced/tutorial20/ZAFF.php)
is available for its usage. It describes 12 different Zn fingers, 
varied in the type and protonation of the coordinating residues. Further
combinations can be created either based on these parameters, or by
carrying out QM calculations, especially for getting the (RESP) charges.

## Implementation
There are two major changes that are required for using the modified FF,
apart from the obvious deprotonation of coordinating cysteins (CYS->CYM).
One is the modification of the system topology, including the 2-3-4 atom
interactions involving the zinc. The other one is modifying the charges,
which, depending on the software environment, may require the definition
of one-off residue types, see the amber
[example](https://ambermd.org/tutorials/advanced/tutorial20/files/zaff/ZAFF.prep).

### NAMD
_I discuss the usage in NAMD, as our preferred MD engine, especially with
the CHARMM36m forcefield shipped from CHARMM-GUI_

CHARMM also implemented extra parameters for the Zn fingers, part of the
`toppar_all36_prot_modify_res.str` compilation. Here the bonding, angle
and dihedral parameters are set for S and N atoms, assuming CYM and HIS
(HSD or HSE) coordination. To use these, the `psf` file of the system 
has to be modified: registering the index of the atoms involved, 
doubles, triples and quadrupoles for bonds, angles and dihedrals are to 
be added to their respective sections, so the software will invoke these
parameters.
Although this modification could be scripted, we have not done that as 
it only has to be done once for a `psf`.

_(Some classical MD software register only the parameters which are
used, like amber or gromacs. In NAMD or charmm, one may read in many
redundant paremeters, the necessary ones are employed in runtime based
on the topology.)_

The second modification is swapping the charges to the ones representing
the charge transfer. In NAMD, that can be done in the `psf` as well. I
suggest borrowing them from ZAFF, the minor changes are within the 
errors of the forcefield. For instance, the Zn(CYM)<sub>4</sub> site
assigns a partial charge of `0.52437` to the zinc, and the CYM 
sidechains are modified accordingly to have a net of -2 for the moiety.

<small>_D. Berta, Mar 2024_</small>
