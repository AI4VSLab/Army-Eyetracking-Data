this is how to decode the struct files for the RVSMS 3.0 Gripper study

subjID = is the subject id number
each gripper condition has its own struct

near vs far viewing distance
no toe in vs toe in camera angle
3x vs 8x hyperstereo 

those structs consist of a new entry for every trial that occured in that session. for each of those there is:

ET - eye tracking data that is an n x 4 matrix. rows are each time point. columns are left horizontal, left vertical, 
        right horizontal, vertical eye position in degrees
pupil size - left and right eye pupil size in microns (divide by 1000 to get to mms)
leftSacc & rightSacc - detected saccade metrics
gripper - a struct that contains the timing and the individual dynamics of the gripper behavior 
gripper.data is a n x 9 matrix, the columns are:
        joyAz - these three are behavior of the joystick and i think they can be ignored
        joyEl - "
        joyExt - "
        ballX - horizontal position of the ball (should be redundant with gripX)
        ballY - down range position of the ball (should be redundant with gripY)
        ballZ - height of the ball (doesn't appreciably change)
        gripX - horizontal position of the gripper
        gripY - down range position of the gripper
        gripZ - height of the gripper (doesn't appreciably change)
summary is a 1x18 table of the summary performance data, relevant variables are:
        x, y, z = horizontal, down range, vertical position of the target
        xobj, yoby, zobs = same for the final release point of the gripper
        error, dx, dy = total error, horizontal error and down range error 
        trialStart and trialEnd = more precise timing of the trial


okay, back up to the top
neuroFit are the results of the neuroFit protocol, relevant variables are:
    neurofit.saccadometry.metrics
    neurofit.COBRA.metrics

AVT are each of the entries in the AVT battery

FusionRange is the fusion range battery from the old AVT

Optec are classic optometry values

ETParams are the parameters used for the automated saccade detection
        


