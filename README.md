# A Genetic Algorithm for the Stochastic Resource Constrained Project Scheduling Problem

##Abstract

Scheduling of tasks is one of the most basic, yet most complicated tasks in any production project. The work at hand introduces a real world scheduling problem encountered at exept software AG for which we are introducing a solution approach using a genetic algorithm. The work gives background information on scheduling under resource constraints with deterministic, as well as stochastic processing times. We adopt and benchmark a genetic algorithm described in literature and achieve an improvement of median processing times of 17% as compared to the algorithm which is currently used to solve the problem. The standard deviation of processing times is reduced by 33%.

##About this Repo

This reposity contains the software created during my Masters thesis. This includes the implementation of the genetic algorithm itself, as well as various tools created during the process. However, the parser which can be used to convert XML files to our data model has been removed, since it would expose corporate secrets.
However, I included an anonymized version of the dataset I used to validate my algorithm. The dataset is located in `sampleData/anonymized.pickle`. It is dataset described in my thesis, however UUIDs and names of task, ressources etc. have been replaced by randomly generated strings. This does not affect the functionality of the algorithm, although.
A lot of this software has been developed in a hurry and the documentation / code comments is not always correct / consistent. This also affeced overal code quality.
Please do not hesitate to contact me if you have any questions.

###Installation

	python setup.py install

###Tools

During my Thesis I created several tools which helped me during development. The most important ones can be found in the `bin` folder. All of them can be called with the `-h` parameter to get a list of possible commands.


To get a basic simulation setup running the following steps are required:
		
		cd bin
		./simulator --scheduler PPPolicies --output /tmp/outputfile.pickle ../sampleData/anonymized.pickle
Where 
* `--scheduler` specifies the scheduling policy to be used. All schedulers implemented can be found in `schedulers/`.
* `--output` specifies the file the simulation results should be written to
* The last parameter specifies the for the scheduling problem which should be solved

One manifestation of the best scheduling priority by the simulator can be displayed as Gantt Chart with the `visualizer` tool:

	./visualizer --pdf /tmp/gantt.pdf /tmp/outputfile.pickle

Where `--pdf` specifies where the resulting pdf plot should be written to.

The resulting diagram should look similar to this:

![Image of gantt chart](https://raw.githubusercontent.com/juliusf/Genetic-SRCPSP/master/doc/gantt.png)

The colors of the taks have the following meaning: The 7 most used resources in the scheduling problem are assigned colors. Every task which requires one ore more of the theses ressources is colored respectively. This helps identifying the critical path through the scheduling problem.

If you are interested in how the genetic algorithm performs over time, you can start the `simulator` command with the `--show_gen_log true` parameter which plots the fitness of the best and worst individual over time:

![Image of GA](https://raw.githubusercontent.com/juliusf/Genetic-SRCPSP/master/doc/fitnessOverTime.png)



