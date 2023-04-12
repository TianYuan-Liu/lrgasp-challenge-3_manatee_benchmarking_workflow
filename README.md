# LRGASP Event 2 (challenge 3) OpenEBench workflow
The workflow used to run the [LRGASP event 2 docker](https://github.com/TianYuan-Liu/lrgasp-challenge-3_benchmarking_docker) in the [OpenEBench VRE executor](https://github.com/inab/vre-process_nextflow-executor). 

The repository includes several files:

1. Example input dataset `lrgasp-challenge-3_full_data` folder.
2. `config.json`:  the configuration file of the workflow. It contains different elements under arguments, including the git repository of the workflow, the specific commit to try, the community id, a participant id and the parameter with the challenges to compute. 
3. `in_metadata.json`: define the directories of the input files. The file declares the input files' detail locations inside the `config.json`.
4. `materalize-data.sh`: materialize the datasets needed in pre-defined relative paths
5. `materialize-containers.sh`: building the needed containers for LRGASP workflow 

## Usage
1. Install [OpenEBench VRE executor](https://github.com/inab/vre-process_nextflow-executor/blob/master/INSTALL.md) and go to the **tests** folder
```
cd vre-process_nextflow-executor/tests
```
2. Clone the [LRGASP workflow repository](https://github.com/TianYuan-Liu/lrgasp-challenge-3_manatee_benchmarking_workflow) and rename the folder to  LRGASP_manatee
```
git clone https://github.com/TianYuan-Liu/lrgasp-challenge-3_manatee_benchmarking_workflow.git
mv lrgasp-challenge-3_manatee_benchmarking_workflow LRGASP_manatee
```
3. Materialize both the containers and datasets needed by the LRGASP test:
```
cd LRGASP_manatee
bash ./materialize-data.sh
bash ./materialize-containers.sh
```
4. Run the tests from LRGASP_manatee example
```
cd ../..
./test_VRE_NF_RUNNER.sh LRGASP_manatee
```
