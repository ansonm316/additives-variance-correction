# Additives Variance Correction Project

### Project Description

This project is to identify the reason behind extreme variance between expected and actual quantities of additives being used in the extruders, which will then be used to formulate a method to correct such behaviour.

## Findings

The reason for the abnormal variances between expected and actual quantities of additives being used in the extruders is due to the inaccurate ways that data has been collected and presented in the operations dashboard.

### Process

Under each job number, a selected amount of scrap will be used in the extruders to produce the desired results. However, each job may use scrap with different specifications. For example, some scrap materials may be of higher melt than others. These scrap materials are placed randomly in an allocated area, which results in the usage of a mix of lower melt and higher melt scrap materials used on the extruders as forklifts randomly retrieve materials from that allocated area. Consequently, each shift will use a different ratio of higher melt and lower melt scrap materials. For example, shift A may use approximately 70% higher melt and 30% lower melt material, where less additives may be required than in shift B, where 80% higher melt and 20% lower melt scrap materials are being used, where more additives may be required. This is particularly problematic as the ERP has only one column attributed to entering the quantity of additives per pound of products desired. For example, a quantity of 0.02 with a desired production quantity of 40,000 lbs results in an 800 lbs of additives expected to be used for the entire job.

Since differing ratios of scrap materials are used throughout the job on a shiftly-basis, the quantity of additives per pound of desired product will change accordingly. For example, shift A may use an additive quantity of 2% of the total desired production amount while shift B and C may use 5% due to the higher amount of low-melt material being present in the overall scrap materials used for production. The extra 3% of additives unaccounted for is directly responsible for the extreme variances between the expected and actual quantities of additives being used.

The differing ratio of scrap materials used throughout production dynamically changes the amount of additives used on a per-box basis. When a production job is initialized, the operator first set a tentative dosage percentage, which is the dosage percentage specified in the job details. For each box, a sample is sent to the lab for analysis to see whether it meets all of the customer specifications. If the sample fails, the lab sends back instructions through the ERP to communicate with the operator about actions that needs to be taken, such as whether to increase or decrease the dosage percentage of the additives.

To summarize, the current method is as follows:

1. Operator receives a job that specifies the type and amount of additives used.
2. Operator weighs the additives at the start of the shift when the job is assigned and notes it down.
3. The sample of the first box produced is sent to the quality control lab to test if it meets all customer specifications.
4. Based on the test results, the operator adjusts the dosing percentage of the additives.
5. At the end of the operator's shift, the additives are weighed again and the difference between the weight at the beginning and the end of their shift is recorded into the "Additives Log Sheet".
6. Operator justifies the increase or decrease of the dosage percentage of the additives to the supervisor.

### Conclusion

The maintenance lead and lab technicians concluded that the dosage unit and the samples of a specific production job satisfies its customer specifcations respectively. Therefore, possibilities that the dosage unit is malfunctioning or the products produced are out-of-spec are ruled out. Therefore, the reason why the variance between the expected and actual quantity can be deducively concluded as a misrepresentation due to how the data is being handled and presented on the operations dashboard.

## Solutions Proposal

### Dynamic "Expected Quantity" Recalculation

The change in dosage percentage initialized by the lab must be recorded into the ERP at real time. The expected quantity is calculated as follows:

$\text{Total Quantity Produced}\cdot\text{Dosage Percentage = Expected Quantity}$

The actual quantity can be tracked using the same process currently deployed.
 
|Time|Dosage %|Dosage % Change|Total Quantity Produced (lbs)|Comments|
|----|--------|---------------|-----------------------------|--------|
|ex. 8:15 a.m.|2%|-|5,000|-|
|ex. 10:00 a.m.|-|2% --> 5%|-|Refer to Lab Comment #[Lot Number]|
|ex. 3:45 p.m.|5%|-|20,000|-|

In this case, the expected amount of additives used for the total quantity produced before change #1 is:

$5000\cdot2\% = 100\text{ lbs}$

And between change #1 and #2:

$20000\cdot5\% = 1000\text{ lbs}$

Therefore, the total amount of additives used for shift A is 1100 lbs.

This way, the expected quantity is no longer misrepresented by a single value dictacted in the ERP at the beginning of the shift without accounting for the dynamic changes that happen on the floor. 

### Material Sorting System (Long-term Solution)

Once the lab tested the scrap material has high-melt, low-melt, or a specific characteristic, it should be labelled with a sticker or some type of physical indentification for the forklift operators to visually understand the type of materials being fed into the extruders. 

A standardized recipe should be determined. For example, a two rolls of high-melt scrap material and one roll of low-melt scrap material should use a specified amount of additives to achieve the desired result.

Through a standardized recipe, the dynamic recalculations will be rendered obsolete.




