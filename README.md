# GMI_report
GMI_report_exec.py Usage SOP

Author: Jiawei Shen

Version: 1.2

1. Download the GMI_report_exec.py to your desired location via aws cli command. The s3 link of the script is s3://zymo-files/jshen/gut_report/automation_scripts/GMI_report_exec.py .

2. Go to the s3 folder s3://zymo-microbiomics-service/epiquest_tmp/GMI_patient_info/ and create a folder with the format {project_id}.{rundate} . Then place the patient_info.csv (filename must be exact) there. Make sure that the number of samples and sample IDs in the patient_info.csv file must match with those in the project_id. Click here to download an example patient_info.csv patient_info.csv file to figure out the required format of it.

3. To run the GMI_report_exec.py with already generated BI results stored on S3, here are the four required parameters:

a. project_id

b. rundate

c. random_string

d. report_tag (the BI results zip file has the filename format {project_id}.{report_tag}.report.zip . Please check the filename for the BI results zip file to figure the report_tag parameter.)

4. Once everything is set up properly. Run the script with the command docker run -v /home/ubuntu/:/home/ubuntu/ -w $(pwd) -v /home/ubuntu/.aws/:/root/.aws/ -it jiaweishenzrc/gut_report:v1.1 python3 GMI_report_exec.py -p {project_id} -t {report_tag} -r {random_string} -d {rundate} -g 1 . Note that to run the GMI_report_exec.py with already generated BI results stored on S3, the -g option is required and must be set to 1.
