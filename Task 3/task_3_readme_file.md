# Paper Folding Simulation Model

## Overview
This simulation model represents a paper folding process involving a workstation with operators, robots, and various stages such as paper loading, alignment verification, folding, and quality checking.

## Simulation Components
- **WorkStation1 Class:** Represents the main workstation with operators, robots, and associated metrics tracking.
- **Operator Class:** Models the behavior of the operator during different stages of the process.
- **Robot Class:** Represents the robotic system involved in paper handling.
- **Paper Class:** Represents the paper object with properties and characteristics.

## Theoretical Parameters

- **Paper Loading Time:** Random between 2 to 4 seconds.
- **Folding Time:** Random between 4 to 7 seconds.
_ **Quality Check Time:** random between 3 to 4 seconds.
- **Interarrival Time: Random:** between 2 to 5 seconds.

## # Paper Folding Simulation Model

## Overview
This simulation model uses SimPy to simulate a paper folding process in a workstation, involving operators, robots, and various stages such as paper loading, alignment verification, folding, and quality checking.

## Paper Folding Process

### 1. Paper Loading
- **Operator Action:** The operator initiates the process by loading a paper into the robot.
- **Simulation Step:** The simulation tracks the time it takes for the operator to load the paper into the robot.

### 2. Paper Loading Verification
- **Operator Action:** The operator checks the loaded paper for any loading errors.
- **Simulation Step:** The simulation records the time taken for the operator to verify the paper loading.

### 3. Paper Alignment Verification
- **Operator Action:** The operator checks the alignment of the paper.
- **Simulation Step:** The simulation records the time taken for the operator to verify paper alignment.

### 4. Folding Operation
- **Robot Action:** The robot initiates the folding process.
- **Operator Action:** The operator may assist in certain folding steps.
- **Simulation Step:** The simulation tracks the time taken for the robot and operator during the folding process.

### 5. Quality Check
- **Operator Action:** The operator checks the folded paper for quality.
- **Simulation Step:** The simulation records the time taken for the operator to perform the quality check.

### 6. Handover to Next Station
- **Robot Action:** The robot hands over the folded paper to the next station (Workstation2).
- **Simulation Step:** The simulation logs the time of handover.

### 7. Operator Idle Time and Robot Return
- **Operator Action:** The operator may be idle during various stages.Those times are recorded for our results.
- **Robot Action:** The robot returns to the start position after completing the process.
- **Simulation Step:** The simulation records the idle time of the operator and the time taken for the robot to return.

## Execution Example
```python
# Import necessary modules and classes
import simpy
from your_simulation_file import WorkStation1, Operator, Robot, Paper, paper_generator

# Create a SimPy environment
env = simpy.Environment()

# Initialize simulation components
paper_list = []
folded_papers = 0
operator = Operator(env, WorkStation1, folded_papers)
workstation1 = WorkStation1(env, paper_list, Robot, Workstation2, Operator, folded_papers)

# Run the simulation
print("Simulation started...")
env.process(paper_generator(env, workstation1, paper_list))
env.run(until=28800)  
print("Simulation completed.")

# Display simulation results
print("The number of produced papers is " + str(workstation1.folded_papers - 1) + ".")
print("The simulation duration is " + str(env.now) + " seconds.")

# Calculate and display average processing times, defective papers, and generate visualizations
print ("The average process time of the produced papers is {:.2f} seconds.".format(average_process_time))

print ("The average Folding process time is {:.2f} seconds.".format(average_folding1_time))
print ("The average Quality check time is {:.2f} seconds.".format(average_quality_check_time))
print ("The average paper loading verification time is {:.2f} seconds.".format(average_paper_loading_verification_time))
print ("The average paper alignment verification time is {:.2f} seconds.".format(average_paper_alignment_verification_time))
print ("The number of defective papers is "+str(workstation1.defective_papers)+".")
print ("The average operator idle time is {:.2f} seconds.".format(average_operator_idle_time))

## The simulation provides information about the folding process of paper, such as the number of papers produced, average processing times, defective papers, and visualizations for better analysis.

All the metrics are included in the table
# Production Metrics Summary

| Metric                                   | Value                                |
|------------------------------------------|--------------------------------------|
| Produced Papers                          | {produced_papers}                    |
| Simulation Duration                      | {simulation_time} seconds            |
| Average Process Time (Cycle Time)         | {:.2f} seconds                      |
| Average Folding Time                     | {:.2f} seconds                       |
| Average Paper Loading Verification Time  | {:.2f} seconds                       |
| Average Paper Alignment Verification Time| {:.2f} seconds                       |
| Average Quality Check Time               | {:.2f} seconds                       |
| Defective Papers                         | {workstation1.defective_papers}      |
| Average Operator Idle Time during Process| {:.2f} seconds                       |


Note : This documentation provides a comprehensive overview of the simulation model, execution, and key results.All the theortical parameters are editable for the future needs .
