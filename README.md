# InsightsForSSFs
Results from "Insights for Estimating Animal Movement Step Selection Functions"

The enclosed repository (ResultsByModel.zip) contains 175 R workspace files (.RData) – one for each of the 25 tracks within each of the 7 track classes discussed in this paper. Each file contains several data objects:


•	Track (data frame): The simulated track is expressed in terms of x- and y- coordinates. For subsequent use as inputs in step selection functions, step length, absolute angle (computed relative to movement in the positive direction along the x-axis), and relative angle (computed relative to the previous step) are also included.


•	ParamList (data frame): The parameters used to simulate the track have been recorded in this data frame.

o	LandscapeNum = index of the landscape on which the track has been simulated (varies from 1 to 5)

o	TrackNum = index of tracks within each class and on each landscape (varies from 1 to 5)

o	Beta1 = the specified effect for the first covariate (set to 4 for all tracks in this study)

o	Beta2 = the specified effect for the second covariate (set to 2 for all tracks in this study)

o	TrackLength = number of steps in the track (set to 500, 1000, or 2000 in this study)

o	CorWindow = smoothing window size that specifies the width of the window used to smooth each grid within the covariate landscape (set to 1, 2, or 4 in this study); the width of the window is equal to 2*CorWindow + 1

o	StepLengthParam = reciprocal of the mean step length for the track (set to 1/8, 1/4, or 1/2 in this study)

o	TurningAngleKappa = parameter that determines the width of the peak of the von Mises distribution from which the relative turning angles of candidate steps are drawn (set to 3 for all tracks in this study); higher values yield tighter peaks


•	ResultsByModel (data frame): The fitted effects for each model from each replicate with different numbers of comparison steps have been recorded in this data frame. There is one entry for each model.

o	LandscapeNum = index of the landscape on which the track has been simulated (varies from 1 to 5)

o	TrackNum = index of tracks within each class and on each landscape (varies from 1 to 5)

o	NumCompSteps = number of comparison steps paired with each observed step

o	Round = replicate number for a given track and a given number of comparison steps

o	PointEstimate1 = point estimate for the first covariate’s effect (from a model fitted without the noise covariate)

o	StandardError1 = standard error for the first covariate’s effect (from a model fitted without the noise covariate)

o	PointEstimate2 = point estimate for the first covariate’s effect (from a model fitted without the noise covariate)

o	StandardError2 = standard error for the first covariate’s effect (from a model fitted without the noise covariate)

o	AIC2 = AIC of a model fitted with only the two true covariates, i.e., without the noise covariate

o	AIC3 = AIC of a model fitted with the two true covariates that influenced the track simulation, as well as the noise covariate

Using the ResultsByModel data frame, the enclosed code (findNumCompStepsNeeded.R) allows the number of CSs needed for each track to be determined

