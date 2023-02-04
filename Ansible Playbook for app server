# Create an Ansible playbook for deploying the code

- name: Deploy the code
  hosts: appserver
  become: yes
  tasks:
    - name: Update the codebase
      git:
        repo: https://github.com/example/app.git
        dest: /opt/app
        update: yes

    - name: Install dependencies
      pip:
        name: "{{ item }}"
        state: present
      with_items:
        - Flask
        - Requests

    - name: Start the application
      command: /opt/app/run.sh
      register: result

    - name: Check the application status
      command: ps aux | grep run.sh
      register: status

    - name: Display the application status
      debug:
        var: status.stdout_lines

# Run the playbook

$ ansible-playbook deploy.yml
