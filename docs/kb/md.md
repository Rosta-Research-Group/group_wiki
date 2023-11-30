# (Classical) Molecular Dynamics
This page gives an overview of system setup for classical 
biomolecular MD simulations. It is by no means comprehensive, and it 
relies on the experience of the group.

## Initial structure
Most simulations are based on one or more experimental structures, 
and one may use homology modelling to for certain parts. 
Important to remember that none of these are perfect. Generally, it 
is advisable to collect the structures related to the state the model
is to be created for and determine a consensus structure. Sometimes
certain regions are patched from other, even loosely homologous 
proteins.

## Making an explicit atomistic model
Structures are seldom atomistically explicit, as hydrogens are 
typically resolved. There are multiple aspects of creating a complete
model:
### Proteins, nucleic acids
Biomolecules are heavily studied with molecular mechanics, therefore
force fields and tools are prepared for helping us create an 
atomistic model. Note that these often rely on the residue and atom 
names. Adding missing atoms and explicit hydrogens are usually part
of any software's preparation pipeline.
#### Protonation state
Pay extra attention to protic and polar moieties. Propka is a good
starting point to set up the protonation state, it is advisable to 
inspect the structure wherever a discrepancy is suggested from the 
expected protonation state. Furthermore, histidines have a tiny
difference between the delta and epsilon states, therefore the local
environment is to be studied to decide which is more favourable.
There are more comprehensive tools to optimise the overall H-bonding
network, e.g. the protein preparation wizard of the Schrödinger Suite.
### Ion sites, crystallographic waters
For a correct setup, collecting all available structures are especially
important in this regard. Some ions, like Mg2+ will require an 
octahedral coordination, which may need to be completed by water
molecules. Others, like Zn2+, prefer tetrahedral, which is difficult 
to maintain by formal charge non-bonding interaction setups. Special
force field patches can be employed to address this, e.g. ZAFF. 
Depending on the software, implementing these may require a 
modification to the topology. Also pay attention to other waters, as 
some may have a structural role in positions hardly accessible from 
bulk or for the solvation algorithms.
### Ligands, substrates
Unlike biomolecules, the connectivity is not straightforward from
ligand 3D structures, therefore dedicated attention is needed for 
correct bond orders. Several all atom force fields or parametrisation
options are available. The easiest improvement on these are using QM
calculated (R)ESP charges. It is important to note, that in some cases
molecular symmetry is not automatically considered.
#### Protonation state
Crucially, ligand protonation has to be set up correctly. Beyond 
chemical intuition, pKa estimators for small molecules are available,
e.g. Epik in Schrödinger or a free tool within Marvin sketch.

## Equilibration
The general experience is, the slower, the better. After solvation and
electrolite setup, a minimisation can help to remove a degree of
clashes, a check of the crucial structural details is always advisable.
It is often a good strategy to separate the equilibration of certain
degrees of freedom by applying some extra restraints which are then
gradually released. The decision on this is highly contextual, based 
on the source of the initial structure and the goal of the simulation.
Although simulations often supposed to be ergodic, running replicas is
generally helpful for sampling.

<small>_D. Berta, Nov 2023_</small>