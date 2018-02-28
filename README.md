# Nucbox - home media and utility server

Deploy debug

# Install
ansible-playbook -i .inventory orchestration/deploy.yml --extra-vars "override_hosts=dev deploy_current_dir=1"

# Deploy
ansible-playbook -i .inventory orchestration/deploy.yml --extra-vars "override_hosts=dev deploy_current_dir=1"

# Remove
ansible-playbook -i .inventory orchestration/remove.yml --extra-vars "override_hosts=dev remove_completely=1" -K -vv