# MoConVQ Modifications

Modifications to moconvq focus on inserting smpl data and updating file relative paths.

## MoConVQCore/Utils/motion_dataset.py

Main change in this file is the function add_bvh_with_character. Changes include 
- allowing loading a smpl file rather than bvh file.
- getting torque, velocity, and angular velocity

A new Dataset (DPGDataset) is also created for using with moconvq take env in dpg_system.

## MoConVQCore/Env/vclode_track_env.py

This file was updated to pull torque information from moconvq environment. Defines the step functio in usual RL procedures.

## Data/Parameters/bigdata.yml

This file was updated for model parameter files paths to work with dpg system.

## ModifyODESrc/VclSimuBackend.pyx

This file is the internal file for MoconVQ environment. It is compiled to C when you run setup of MoConVQ, specifically the command pip install -e . in the ModifyODESrc directory. 

The function load_amass_npz is what loads the amass file into MoConVQ's data structure, which is called by the initialization of the BVHToTargetBase class in the file MoConVQCore/Utils/motion_dataset.py

## Stubs

Stubs were updated with stubs of new functions. Stub files:
- MoConVQCore/VclSimuBackend.pyi
- MoConVQCore/stubs/VclSimuBackend.pyi
- stubs/VclSimuBackend.pyi

## Added modules in ModifyODESrc

Modules in CharacterAnimationTools (anim and utils) were imported into ModifyoDESrc to help with reading data from amass files and injecting into MoConVQ's data structure. They are imported as ModifyODESrc/anim and ModifyODESrc/Util