## Scenario 1:
  
   In this scenario, the key parameter under consideration is the density of paper, which represents the mass or thickness of the paper being processed. Notable changes include adjustments to the probabilities of loading errors and misalignments due to varying paper sizes. These changes aim to reflect the variability encountered in real-world scenarios.

## Updated Parameters :

## PaperLoadingStation
Loading Error Probability: 32% (previously 30%)
Misalignment Probability: 32% (previously 30%)

## Operator
Loading Error Adjustment Probability: 32% (previously 30%)
Misalignment Adjustment Probability: 32% (previously 30%)

## Robot
No significant changes in robot behavior.

## Quality Check
Defective Paper Probability: 10%

## Simulation Execution :

The simulation runs for a duration of 28,800 seconds (8 hours) and tracks the production process, including paper loading, alignment verification, folding, quality checks, and waste disposal.

## Scenario 2 :

Quality checks are now conducted in parallel with the paper loading process. The operator checks the quality of the previously folded paper while the robot loads the next paper.



## Changes :
The quality_check_fold method is introduced to perform quality checks in parallel with the loading process.
The dispose method is used to send defective papers to the WasteStation.

    def workstation1_process(self,operator,paper,robot):
        
        #The paper is loaded into the robot
        yield self.env.process(self.robot.load_paper(paper,PaperLoadingstation))
        print("The Paper " +str(self.folded_papers)+" has been loaded into the robot at "+str(self.env.now)+" seconds.")
        
         #Quality check of the previous  by the operator during the paper loading process
        yield self.env.process(self.operator.quality_check_fold(paper))
        if paper.is_defective:
            self.defective_papers += 1

## Simulation Execution :

The simulation runs for a duration of 28,800 seconds (8 hours) and tracks the production process, including paper loading, alignment verification, folding, quality checks, and waste disposal.

## Scenario 3 : (critical path)

The removal of unnecessary loops and steps, as well as the consolidation of specific tasks to enhance efficiency in the paper folding process. In our case , steps like Paper Loading checking and Paper alignment check are removed.

## Changes :

Paper Loading Verification Removed: In this scenario, the paper loading verification step has been removed from the process. The focus is on evaluating the impact of this change on the overall performance and efficiency of the paper folding system.

Alignment Verification Removed: Similar to paper loading verification, the paper alignment verification step has been removed from the process. This change aims to assess the effects of eliminating alignment checks on the system.

## Simulation Execution :

The simulation runs for a duration of 28,800 seconds (8 hours) and tracks the production process, including paper loading, alignment verification, folding, quality checks, and waste disposal.
