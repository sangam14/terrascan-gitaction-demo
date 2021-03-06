# Terrascan Github Action 


# vulnerabilities 

```
on: [push]

jobs:
  terrascan_job:
    runs-on: ubuntu-latest
    name: terrascan-action-terraform
    steps:
    - name: Checkout repository
      uses: actions/checkout@v2
    - name: Scan Terraform 
      id: terrascan
      uses: tenable/terrascan-action@main
      with:
        iac_type: 'terraform'
        iac_version: 'v14'
        policy_type: 'aws'
        only_warn: true
        sarif_upload: true
        #non_recursive:
        iac_dir: 'test_dirs/fail/'
        #policy_path:
        #skip_rules:
        #config_path:
        #webhook_url:
        
    - name: Upload SARIF file
      uses: github/codeql-action/upload-sarif@v1
      with:
          sarif_file: terrascan.sarif
    
  terrascan-k8s:
    runs-on: ubuntu-latest
    name: terrascan-action-k8s
    steps:
    - name: Checkout repository
      uses: actions/checkout@v2
    - name: Scan k8s 
      id: terrascan-k8s
      uses: accurics/terrascan-action@main
      with:
        iac_type: 'k8s'
        iac_version: 'v1'
        policy_type: 'k8s'
        only_warn: true
        sarif_upload: true
        #non_recursive:
        iac_dir: 'test_dirs/k8s/vul-k0s-helm-docker/kubeyaml/'
        #policy_path:
        #skip_rules:
        #config_path:
        
    - name: Upload SARIF file
      uses: github/codeql-action/upload-sarif@v1
      with:
        sarif_file: terrascan.sarif
        
  terrascan-docker:
    runs-on: ubuntu-latest
    name: terrascan-action-docker
    steps:
    - name: Checkout repository
      uses: actions/checkout@v2
    - name: Scan docker custom
      id: terrascan-k8s
      uses: accurics/terrascan-action@main
      with:
        iac_type: 'docker'
        iac_version: 'v1'
        policy_type: 'docker'
        only_warn: true
        sarif_upload: true
        #non_recursive:
        iac_dir: 'test_dirs/custom-policies/'
        policy_path: 'test_dirs/custom-policies/'
        #skip_rules:
        #config_path:
        
    - name: Upload SARIF file
      uses: github/codeql-action/upload-sarif@v2
      with:
        sarif_file: terrascan.sarif
  ```






# Remedies 

```
on: [push]

jobs:
  terrascan_job:
    runs-on: ubuntu-latest
    name: terrascan-action-terraform
    steps:
    - name: Checkout repository
      uses: actions/checkout@v2
    - name: Scan Terraform 
      id: terrascan
      uses: tenable/terrascan-action@main
      with:
        iac_type: 'terraform'
        iac_version: 'v14'
        policy_type: 'aws'
        only_warn: true
        sarif_upload: true
        #non_recursive:
        iac_dir: 'test_dirs/fail/'
        #policy_path:
        #skip_rules:
        #config_path:
        #webhook_url:
        
    - name: Upload SARIF file
      uses: github/codeql-action/upload-sarif@v2
      with:
          sarif_file: terrascan.sarif
    
  terrascan-k8s:
    runs-on: ubuntu-latest
    name: terrascan-action-k8s
    steps:
    - name: Checkout repository
      uses: actions/checkout@v2
    - name: Scan k8s 
      id: terrascan-k8s
      uses: tenable/terrascan-action@main
      with:
        iac_type: 'k8s'
        iac_version: 'v1'
        policy_type: 'k8s'
        only_warn: true
        sarif_upload: true
        #non_recursive:
        iac_dir: 'test_dirs/k8s/remediation-kubernetes-helm-docker/kubeyaml'
        #policy_path:
        #skip_rules:
        #config_path:
        
    - name: Upload SARIF file
      uses: github/codeql-action/upload-sarif@v2
      with:
        sarif_file: terrascan.sarif
        
  terrascan-docker:
    runs-on: ubuntu-latest
    name: terrascan-action-docker
    steps:
    - name: Checkout repository
      uses: actions/checkout@v2
    - name: Scan docker custom
      id: terrascan-k8s
      uses: accurics/terrascan-action@main
      with:
        iac_type: 'docker'
        iac_version: 'v1'
        policy_type: 'docker'
        only_warn: true
        sarif_upload: true
        #non_recursive:
        iac_dir: 'test_dirs/custom-policies/'
        policy_path: 'test_dirs/custom-policies/'
        #skip_rules:
        #config_path:
        
    - name: Upload SARIF file
      uses: github/codeql-action/upload-sarif@v2
      with:
        sarif_file: terrascan.sarif
  ```

