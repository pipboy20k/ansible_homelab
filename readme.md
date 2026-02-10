# First things first

check group_vars/all/vars.yml and modify to your liking
note: *main_network_user* is the same user I use *normally* use, it is being created within *base_config* just to make sure that userids are consistent within my network

some things might need a group_vars/all/secrets.yml, try ansible-vault for that (key location in ansible.cfg), create as needed 


# USAGE


Prerequisites:
 - ~/.ssh/my_homelab_key.pub must exist
 - obiously, the corresponding private key must exist
 - have a debian installer with a preseed cfg that creates **only** user ansible with uid = 1001

1. install debian trixie to target host
2. if needed, update inventory file with new ip
3. make sure to have the new fingerprint by manually connecting to the host with user ansible
4. run ansible-playbook -Kk my_playbook.yml (first run with manual password entry, if the playbook includes the role *base_config*, later runs need to be without *-kK*)
