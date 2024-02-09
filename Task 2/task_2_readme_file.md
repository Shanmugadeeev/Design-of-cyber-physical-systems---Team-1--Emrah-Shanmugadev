# Data Structure Documentation

## Overview

This Python script simulates a paper folding process using the SimPy library. The simulation models the workflow of a paper folding through various stages, including folding, quality checks, and handovers between workstations.

## Components

### Paper

The Paper class represents individual sheets of paper in the simulation.Each sheet can be marked as defective during quality checks.

### PaperLoadingstation

Simulates a station where paper is loaded. It has methods to check paper availability, pick paper, and restock.

### Robot

The Robot class is a robotic arm central to paper processing.It performs actions like  loading paper, Folding paper and passing papers to the next workstation.

### Operator

The Operator class represents a human operator overseeing quality checks.It checks paper quality after folds, responding appropriately to defective papers.

### Workstation1

Represents the first workstation in the paper folding process, interacting with the Robot, Operator, and other components.

### Workstation2

It stands for the second workstation in the sequence. It has no unique functionality at the moment and only acts as a placeholder.

### WasteStation

Simulates a station for disposing of defective papers.

### Usage

paper = Paper(env, workstation1)
paperLoadingstation = PaperLoadingstation(env,workstation1)
robot = Robot(env, workstation1)
operator = Operator(env, workstation1, folded_papers)
workstation1 = Workstation1(env)
workstation2 = Workstation2(env)
waste_station1 = WasteStation1(env)
waste_station2 = WasteStation2(env) 

## Key Processes

- **Paper Loading:** Papers are loaded into the process from the PaperLoadingstation.
- **Robot Operations:** The Robot performs tasks such as loading, folding, and handover to the next station.
- **Quality Checks:** The Operator conducts quality checks on folded papers, identifying defects.
