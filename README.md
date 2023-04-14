# LRGASP Event 2 (challenge 3) OpenEBench workflow
The workflow used to run the [LRGASP event 2 docker](https://github.com/TianYuan-Liu/lrgasp-challenge-3_benchmarking_docker) in the [OpenEBench VRE executor](https://github.com/inab/vre-process_nextflow-executor). 

The repository includes several files:

1. `lrgasp-challenge-3_full_data` folder: An example input dataset.
2. `config.json`:  The workflow configuration file containing various elements under arguments, such as the workflow's git repository, specific commit, community id, participant id, and the parameters for the challenges to compute.
3. `in_metadata.json`: Defines the input files' directories. The file specifies the input files' detailed locations within the  `config.json`.
4. `materalize-data.sh`:  Downloads the required datasets to pre-defined relative paths.
5. `materialize-containers.sh`: Builds the necessary containers for the LRGASP workflow (not currently in use, directly downloads from Docker Hub instead).

## Usage
1. Install [OpenEBench VRE executor](https://github.com/inab/vre-process_nextflow-executor/blob/master/INSTALL.md) and go to the **tests** folder
```
cd vre-process_nextflow-executor/tests
source .py3Env/bin/activate
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
```
4. Run the tests from LRGASP_manatee example
```
cd ../..
./test_VRE_NF_RUNNER.sh LRGASP_manatee
```
