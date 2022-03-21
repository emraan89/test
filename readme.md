# AppDynamics Agents Deployment

## Installing Ansible Galaxy dependencies

  ```ansible-galaxy install -vv -f -r requirements_galaxy.yml```

## Running Ansible Playbook
  
  For all non-prod-linux
  
  ```ansible-playbook -l nonprod-linux --tags=install -v -T 10 -c smart -i inventory.ini -e 'appd_account_access_key=<Dev_Access_Key>' --user=zID@corp.emirates.com -k java.yml```

  > Set appd_account_access_key for AppDynamics Development access key or for AppDynamics Production access key

  For only one host

  ```ansible-playbook -l doliwwdv426.hq.emirates.com --tags=install -v -T 10 -c smart -i inventory.ini -e 'appd_account_access_key=<Dev_Access_Key>' --user=zID@corp.emirates.com -k java.yml```

## Fixing logs folder permissions using ansible playbook
  
  For all non-prod-linux
  
  ```ansible-playbook -l nonprod-linux --tags=install -v -T 10 -c smart -i inventory.ini  --user=zID@corp.emirates.com -k fix-java-agent-logs.yml```

## Fixing logs folder permissions using ansible standalone mode

  For wladmin user
  
  ```ansible doliwwdv426.hq.emirates.com -vv -i inventory.ini --user=zID@corp.emirates.com -k -b --become-user=wladmin -m command -a 'chmod -R a+w /opt/appdynamics/java-agent/ver21.10.0.33144/logs/'```

  For springadmin user
  
  ```ansible doliwwdv426.hq.emirates.com -vv -i inventory.ini --user=zID@corp.emirates.com -k -b --become-user=springadmin -m command -a 'chmod -R a+w /opt/appdynamics/java-agent/ver21.10.0.33144/logs/'```