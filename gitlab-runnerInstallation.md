

## To install gitlab runner in ubuntu server
```bash
curl -fsSL https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.deb.sh | sudo bash
sudo apt install -y gitlab-runner
```

## start the gitlab-runner
```bash
sudo gitlab-runner start
```

## To register the gitlab-runner
```bash
gitlab-runner register -n --url https://gitlab-dfxp.hfwds.com/ --registration-token GR13CCCXXXXXXFETsyiNCAch --executor shell --description "Anand_vamsi_runner" --tag-list PRD --tls-ca-file=/home/anand/ca_2025.crt
```

## To List the runners
```bash
gitlab-runner list
```
