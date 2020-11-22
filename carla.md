Getting ScenarioRunner up and ready:

- Set up Carla precompiled
- set up an environment e.g. with anaconda, check Carla/PythonAPI (.egg file) for python version!
- install carla python requirements.txt
- Get ScenarioRunner package with **same version** as Carla 
- https://github.com/carla-simulator/scenario_runner/blob/master/Docs/getting_scenariorunner.md
- Set up a python environment that uses the same python version as Carla:
	look at ~/Carla/PythonAPI/dist/carla<Version>.egg
	use for example "Anaconda" to do so
- pip install numpy pygame
- make sure correct version of networkx==2.2 is installed (see scenariorunner docs)
- cd ~/scenariorunner_root
- pip install -r requirements.txt
- shapely problems: https://towardsdatascience.com/install-shapely-on-windows-72b6581bb46c (conda install -c conda-forge geos=3.7.1 solved the issue for me)
- Set up environment variables:
	- https://github.com/carla-simulator/scenario_runner/blob/master/Docs/getting_scenariorunner.md
	- https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#setting-environment-variables

*env vars need are being reset when leaving an environement
-> i had to use absolute paths instead of using variables in paths for PYTHONPATH

conda activate (your env)

conda env config vars set CARLA_ROOT=C:\Users\janosch\Repos\CARLA_0.9.10"
conda env config vars set SCENARIO_RUNNER_ROOT=C:\Users\janosch\Repos\scenario_runner-0.9.10"
conda env config vars set PYTHONPATH=C:\Users\janosch\Repos\CARLA_0.9.10\PythonAPI;C:\Users\janosch\Repos\CARLA_0.9.10\PythonAPI\carla;C:\Users\janosch\Repos\CARLA_0.9.10\PythonAPI\carla\agents;C:\Users\janosch\Repos\CARLA_0.9.10\PythonAPI\carla\dist\carla-0.9.10-py3.7-win-amd64.egg

conda activate (your env)
conda env config vars list

- Run Carla with low graphic mode:
	- cd ~/carla-root
 	- CarlaUE4.exe -carla-server -quality-level=Low
- Run Carla with low graphic mode CarlaUE4.exe -carla-server -quality-level=Low
- check for port in cmd (administrator) : netstat -ab
		=> CarlaUE4 should be running on port 2000
- Run Scenario runner:
	- Start scenario:
	- python scenario_runner.py --scenario FollowLeadingVehicle_1 --reloadWorld
	- Run control:
	- python manual_control.py
- change map: cd ..\PythonAPI\util
		python config.py --map --list
		python config.py --map <MAP>