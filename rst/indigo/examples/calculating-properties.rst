.. _indigo-example-calculating-properties:

======================
Calculating Properties
======================

This examples shows how to calculate different molecule and reaction properties

.. _indigo-example-canonical-smiles:

----------------
Canonical Smiles
----------------

The following code prints canonical smiles string for a given structure

.. indigorenderer::
    :indigoobjecttype: code
    :indigoloadertype: code
    
    # Load structure
    mol = indigo.loadMolecule('CC1=C(Cl)C=CC2=C1NS(=O)S2')

    #print canonical smiles for a molecule
    print(mol.canonicalSmiles())


The example below prints canonical smiles string for a given reaction

.. indigorenderer::
    :indigoobjecttype: code
    :indigoloadertype: code

    # Load structure
    rxn = indigo.loadReaction('[CH2:1]=[CH:2][CH:3]=[CH:4][CH2:5][H:6]>>[H:6][CH2:1][CH:2]=[CH:3][CH:4]=[CH2:5]')

    #print canonical smiles for a reaction
    print(rxn.canonicalSmiles())


.. _indigo-example-sgroups-search:

--------------
Sgroups search
--------------

The following code prints results of SGroups search requests with different criteria:

.. indigorenderer::
    :indigoobjecttype: code
    :indigoloadertype: code
    :downloads: data/all_features_mol.mol
    
    # Load structure
    indigo.setOption("molfile-saving-mode", "3000")
    file1 = "data/all_features_mol.mol"
    m = indigo.loadMoleculeFromFile(file1)

    sgs = m.findSGroups("SG_TYPE", "SUP")

    for sg in sgs:
       print("Superatom with label %s found" % (m.getSuperatom(sg.getSGroupIndex())).getSGroupName());

    sgs = m.findSGroups("SG_LABEL", "Z")
    print("SGroups with label Z:")
    for sg in sgs:
       print("SGroup Index = %d " % sg.getSGroupIndex() + ", SGroup Type = %s" % sg.getSGroupType());

    sgs = m.findSGroups("SG_CLASS", "AA")
    print("SGroups with class AA:")
    for sg in sgs:
       print("SGroup Index = %d " % sg.getSGroupIndex() + ", SGroup Type = %s" % sg.getSGroupType());

    sgs = m.findSGroups("SG_DISPLAY_OPTION", "0")
    print("SGroups expanded:")
    for sg in sgs:
       print("SGroup Index = %d " % sg.getSGroupIndex() + ", SGroup Type = %s" % sg.getSGroupType());

    sgs = m.findSGroups("SG_BRACKET_STYLE", "0")
    print("SGroups with square brackets:")
    for sg in sgs:
       print("SGroup Index = %d " % sg.getSGroupIndex() + ", SGroup Type = %s" % sg.getSGroupType());

    sgs = m.findSGroups("SG_DATA", "Selection")
    print("SGroups with data contains Selection:")
    for sg in sgs:
       print("SGroup Index = %d " % sg.getSGroupIndex() + ", SGroup Type = %s" % sg.getSGroupType());

    sgs = m.findSGroups("SG_DATA_NAME", "comment")
    print("SGroups with data field name comment:")
    for sg in sgs:
       print("SGroup Index = %d " % sg.getSGroupIndex() + ", SGroup Type = %s" % sg.getSGroupType());

    sgs = m.findSGroups("SG_DATA_DISPLAY", "detached")
    print("SGroups with detached data field:")
    for sg in sgs:
       print("SGroup Index = %d " % sg.getSGroupIndex() + ", SGroup Type = %s" % sg.getSGroupType());

    sgs = m.findSGroups("SG_DATA_LOCATION", "relative")
    print("SGroups with relative data field:")
    for sg in sgs:
       print("SGroup Index = %d " % sg.getSGroupIndex() + ", SGroup Type = %s" % sg.getSGroupType());

    sgs = m.findSGroups("SG_ATOMS", "103, 104")
    print("SGroups with atoms 103 and 104:")
    for sg in sgs:
       print("SGroup Index = %d " % sg.getSGroupIndex() + ", SGroup Type = %s" % sg.getSGroupType());

    sgs = m.findSGroups("SG_BONDS", "249, 245")
    print("SGroups with bonds 245 and 249:")
    for sg in sgs:
       print("SGroup Index = %d " % sg.getSGroupIndex() + ", SGroup Type = %s" % sg.getSGroupType());


