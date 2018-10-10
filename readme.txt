1. Use this URL to create a GCP Service Account and Download JSON credentials
https://docs.ansible.com/ansible/devel/scenario_guides/guide_gce.html

2. Go to createinstance > inventory hosts.gcp.yml and update project with the GCP Project name
plugin: gcp_compute
projects:
  - <your GCP project name>
filters:
auth_kind: serviceaccount #enter account type
service_account_file: /home/ansible/my_account.json #path to your json service account file

3. Go to ../GCPnewInstanceRole/roles/onboardingBIGIP/defaults/main.yml >  and update following variables
	a. admin_1 #bigip admin account username
	b. password_1 #bigip admin account password
	c. password_2
	d. root_1 # root password
	e. banner_text
	f. hostname_1 #bigip hostname
	g. server_1   #bigip hostname
	h. license_1  #license registration keys

	Also review and update application information


4. Go to ../GCPnewInstanceRole/createbigip.yaml and update following variables
    a. gcp_project: my-gcp-1234-xy-z-consult #enter your gcp project name
    b. gcp_cred_kind: serviceaccount
    c. gcp_cred_file: /home/ansible/my_account.json # path to your json credentials file you downloaded earlier
    d. zone: "zone_info"  #type your new gcp ve zone information
    e. region: "region_info" #type your new gcp ve region information
    f. ve_name: nonprod-bigip1  #Type your VE name
    g. disk_instance: nonprod-bigip1
    h. test_address: nonprod-bigip1
    i. service_account_email: user@developer.account.com #type your service account email
    j. tags: allowhttpsfrom #enter any pertinent tags for bigip build

5. Go to createinstance > roles > onboardingBIGIP > tasks > main.yml and review and update tasks

6. run playbook ansible-playbook createbigip.yaml
