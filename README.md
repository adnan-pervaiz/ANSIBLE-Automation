# ANSIBLE-Automation

[Adnan@Ansible-Testing~]$ more sip_config.yaml
-
   name: Entices Sip server configuration
   hosts: "{{ hostname }}"
   become: true
   become_user: root
   tasks:
      - name: before check line count
        command: wc -l /etc/init.d/firewall_entice_local
        register: before_check
      - debug: var=before_check.stdout_lines

      - include_tasks: step1_iptables.yaml

      - name: after check line count
        command: wc -l /etc/init.d/firewall_entice_local
        register: after_check
      - debug: var=after_check.stdout_lines

      - include_tasks: step2_script_firewall.yaml
        when: before_check.stdout_lines != after_check.stdout_lines

      - include_tasks: step3_RG_group.yaml
        when: ansible_host =='10.148.129.37' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.129.53' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.129.133' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.129.149' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.129.197' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.129.213' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.97.37' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.97.53' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.97.133' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.97.149' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.84.37' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.84.53' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.84.133' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.84.149' and ( before_check.stdout_lines != after_check.stdout_lines )

      - name: before check line count grafana
        command: wc -l /export/home/ens/scripts/RG_names_list.txt
        register: before_check_grafana
        when: ansible_host =='10.148.129.37' or
              ansible_host =='10.148.129.53' or
              ansible_host =='10.148.129.133' or
              ansible_host =='10.148.129.149' or
              ansible_host =='10.148.129.197' or
              ansible_host =='10.148.129.213' or
              ansible_host =='10.148.97.37' or
              ansible_host =='10.148.97.53' or
              ansible_host =='10.148.97.133' or
              ansible_host =='10.148.97.149' or
              ansible_host =='10.148.84.37' or
              ansible_host =='10.148.84.53' or
              ansible_host =='10.148.84.133' or
              ansible_host =='10.148.84.149'
      - debug: var=before_check_grafana.stdout_lines
        when: ansible_host =='10.148.129.37' or
              ansible_host =='10.148.129.53' or
              ansible_host =='10.148.129.133' or
              ansible_host =='10.148.129.149' or
              ansible_host =='10.148.129.197' or
              ansible_host =='10.148.129.213' or
              ansible_host =='10.148.97.37' or
              ansible_host =='10.148.97.53' or
              ansible_host =='10.148.97.133' or
              ansible_host =='10.148.97.149' or
              ansible_host =='10.148.84.37' or
              ansible_host =='10.148.84.53' or
              ansible_host =='10.148.84.133' or
              ansible_host =='10.148.84.149'

      - include_tasks: step4_RG_names.yaml
        when: ansible_host =='10.148.129.37' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.129.53' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.129.133' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.129.149' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.129.197' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.129.213' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.97.37' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.97.53' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.97.133' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.97.149' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.84.37' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.84.53' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.84.133' and ( before_check.stdout_lines != after_check.stdout_lines ) or
              ansible_host =='10.148.84.149' and ( before_check.stdout_lines != after_check.stdout_lines )

      - name: after check line count grafana
        command: wc -l /export/home/ens/scripts/RG_names_list.txt
        register: after_check_grafana
        when: ansible_host =='10.148.129.37' or
              ansible_host =='10.148.129.53' or
              ansible_host =='10.148.129.133' or
              ansible_host =='10.148.129.149' or
              ansible_host =='10.148.129.197' or
              ansible_host =='10.148.129.213' or
              ansible_host =='10.148.97.37' or
              ansible_host =='10.148.97.53' or
              ansible_host =='10.148.97.133' or
              ansible_host =='10.148.97.149' or
              ansible_host =='10.148.84.37' or
              ansible_host =='10.148.84.53' or
              ansible_host =='10.148.84.133' or
              ansible_host =='10.148.84.149'
      - debug: var=after_check_grafana.stdout_lines
        when: ansible_host =='10.148.129.37' or
              ansible_host =='10.148.129.53' or
              ansible_host =='10.148.129.133' or
              ansible_host =='10.148.129.149' or
              ansible_host =='10.148.129.197' or
              ansible_host =='10.148.129.213' or
              ansible_host =='10.148.97.37' or
              ansible_host =='10.148.97.53' or
              ansible_host =='10.148.97.133' or
              ansible_host =='10.148.97.149' or
              ansible_host =='10.148.84.37' or
              ansible_host =='10.148.84.53' or
              ansible_host =='10.148.84.133' or
              ansible_host =='10.148.84.149'

      - include_tasks: step5_grafana.yaml
        when: ansible_host =='10.148.129.37' and ( before_check_grafana.stdout_lines != after_check_grafana.stdout_lines ) or
              ansible_host =='10.148.129.53' and ( before_check_grafana.stdout_lines != after_check_grafana.stdout_lines ) or
              ansible_host =='10.148.129.133' and ( before_check_grafana.stdout_lines != after_check_grafana.stdout_lines ) or
              ansible_host =='10.148.129.149' and ( before_check_grafana.stdout_lines != after_check_grafana.stdout_lines ) or
              ansible_host =='10.148.129.197' and ( before_check_grafana.stdout_lines != after_check_grafana.stdout_lines ) or
              ansible_host =='10.148.129.213' and ( before_check_grafana.stdout_lines != after_check_grafana.stdout_lines ) or
              ansible_host =='10.148.97.37' and ( before_check_grafana.stdout_lines != after_check_grafana.stdout_lines ) or
              ansible_host =='10.148.97.53' and ( before_check_grafana.stdout_lines != after_check_grafana.stdout_lines ) or
              ansible_host =='10.148.97.133' and ( before_check_grafana.stdout_lines != after_check_grafana.stdout_lines ) or
              ansible_host =='10.148.97.149' and ( before_check_grafana.stdout_lines != after_check_grafana.stdout_lines ) or
              ansible_host =='10.148.84.37' and ( before_check_grafana.stdout_lines != after_check_grafana.stdout_lines ) or
              ansible_host =='10.148.84.53' and ( before_check_grafana.stdout_lines != after_check_grafana.stdout_lines ) or
              ansible_host =='10.148.84.133' and ( before_check_grafana.stdout_lines != after_check_grafana.stdout_lines ) or
              ansible_host =='10.148.84.149' and ( before_check_grafana.stdout_lines != after_check_grafana.stdout_lines )

=============

[Adnan@Ansible-Testing~]$  more inventory.txt
uka01 ansible_host=10.148.129.37 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

uka02 ansible_host=10.148.129.38 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

ukb01 ansible_host=10.148.129.53 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

ukb02 ansible_host=10.148.129.54 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

ukc01 ansible_host=10.148.129.133 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

ukc02 ansible_host=10.148.129.134 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

ukd01 ansible_host=10.148.129.149 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

ukd02 ansible_host=10.148.129.150 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

uke01 ansible_host=10.148.129.197 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

uke02 ansible_host=10.148.129.198 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

ukf01 ansible_host=10.148.129.213 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

ukf02 ansible_host=10.148.129.214 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

hka01 ansible_host=10.148.97.37 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

hka02 ansible_host=10.148.97.38 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

hkb01 ansible_host=10.148.97.53 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

hkb02 ansible_host=10.148.97.54 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

hkc01 ansible_host=10.148.97.133 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

hkc02 ansible_host=10.148.97.134 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

hkd01 ansible_host=10.148.97.149 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

hkd02 ansible_host=10.148.97.150 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

owba01 ansible_host=10.148.84.37 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

owba02 ansible_host=10.148.84.38 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

owbb01 ansible_host=10.148.84.53 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

owbb02 ansible_host=10.148.84.54 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

owbc01 ansible_host=10.148.84.133 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

owbc02 ansible_host=10.148.84.134 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

owbd01 ansible_host=10.148.84.149 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

owbd02 ansible_host=10.148.84.150 ansible_connection=ssh ansible_user=chrisb ansible_password=nO1967*1!X9U

[uka]
uka01
uka02

[ukb]
ukb01
ukb02

[ukc]
ukc01
ukc02

[ukd]
ukd01
ukd02

[uke]
uke01
uke02

[ukf]
ukf01
ukf02

[hka]
hka01
hka02

[hkb]
hkb01
hkb02

[hkc]
hkc01
hkc02

[hkd]
hkd01
hkd02

[owba]
owba01
owba02

[owbb]
owbb01
owbb02

[owbc]
owbc01
owbc02

[owbd]
owbd01
owbd02

=======
  [Adnan@Ansible-Testing~]$ more step1_iptables.yaml
  - name: sip firewall configuration
blockinfile:
  path: /etc/init.d/test
  marker: "# {mark} TNZI Customer {{ admin_code }}-{{ ipadd }}-{{ sip }}-{{ rg1 }}-{{ rg2 }}"
  insertbefore: "## TO HERE"
  block: |
    $IPTABLES -A LOCALLY_MANAGED_RULES_INPUT -p udp -s {{ ipadd }} --sport 5060 -d $SIP_SERVER_{{ sip }}_IP_ADDRESS --dport $SIP_PORT -m string --string "INVITE sip:" --algo kmp --to 400 -m limit
  --limit 30/sec --limit-burst 10 -m comment --comment "{{ rg1 }}-{{ rg2 }}-{{ admin_code }}-{{ ipadd }}" -j ACCEPT
    
  $IPTABLES -A LOCALLY_MANAGED_RULES_INPUT -p udp -s {{ ipadd }} --sport 5060 -d $SIP_SERVER_{{ sip }}_IP_ADDRESS --dport $SIP_PORT -m string --string "OPTIONS sip:" --algo kmp --to 400 -m limi
  t --limit 10/sec --limit-burst 10 -j ACCEPT
  
  $IPTABLES -A LOCALLY_MANAGED_RULES_INPUT -p udp -s {{ ipadd }} --sport 5060 -d $SIP_SERVER_{{ sip }}_IP_ADDRESS --dport $SIP_PORT -m string --string "INVITE sip:" --algo kmp --to 400 -m limit
  --limit 30/sec --limit-burst 10 -m comment --comment "{{ rg1 }}-{{ rg2 }}-{{ admin_code }}-{{ ipadd }}" -j DROP
  
  $IPTABLES -A LOCALLY_MANAGED_RULES_INPUT -p udp -s {{ ipadd }} --sport 5060 -d $SIP_SERVER_{{ sip }}_IP_ADDRESS --dport $SIP_PORT -m string --string "OPTIONS sip:" --algo kmp --to 400 -j DROP
  
  $IPTABLES -A LOCALLY_MANAGED_RULES_INPUT -p udp -s {{ ipadd }} --sport 5060 -d $SIP_SERVER_{{ sip }}_IP_ADDRESS --dport $SIP_PORT -j ACCEPT
  
  $IPTABLES -A LOCALLY_MANAGED_RULES_OUTPUT -p udp -s $SIP_SERVER_{{ sip }}_IP_ADDRESS --sport $SIP_PORT -d {{ ipadd }} -j ACCEPT
  
backup: yes

==========

[Adnan@Ansible-Testing~]$ more step2_script_firewall.yaml
- name: Run script to save iptables
  command: sh /etc/init.d/firewall_entice_local
  register: myoutput
- debug: var=myoutput.stdout_lines

==========

[Adnan@Ansible-Testing~]$  more step3_RG_group.yaml
- lineinfile:
    path: /export/home/ens/scripts/RG_group_list.txt
    line: 'TNZI_{{ admin_code }}:{{ rg1 }},{{ rg2 }}'
==========

[Adnan@Ansible-Testing~]$ more step4_RG_names.yaml
- name: RG names list
  blockinfile:
    path: /export/home/ens/scripts/RG_names_list.txt
    marker: "# {mark} {{ admin_code }}-{{ ipadd }}-{{ rg1 }}-{{ rg2 }}"
    block: |
      {{ rg1 }}:{{ admin_code }}-PUB-IN-{{ ipadd }}
      {{ rg2 }}:{{ admin_code }}-PUB-OUT-{{ ipadd }}

----

    - name: RG names list
      lineinfile:
         path: /export/home/ens/scripts/RG_names_list.txt
         line: '{{item.rg}}:{{ admin_code }}-{{ pub_pvt }}-{{item.direction}}-{{ ipadd }}'
      with_items:
        - { rg: "{{ rg1 }}", direction: 'IN' }
        - { rg: "{{ rg2 }}", direction: 'OUT' }


============

[Adnan@Ansible-Testing~]$ more step5_grafana.yaml
- name: Run script for Grafana
  become: yes
  become_method: sudo
  become_user: ens
  command: sh /export/home/ens/scripts/parse_walkcp_output.sh
  register: myoutput
- debug: var=myoutput.stdout_lines
- debug: var=myoutput.stderr_lines

===========

ansible-playbook sip_config.yaml -i inventory.txt -e "hostname=hkd01 admin_code=test1 ipadd=1.1.1.12 sip=70 rg1=RG0015 rg2=RG016 pub-pri=PUB" -u chrisb -K

===========

[Adnan@Ansible-Testing~]$ more sip_entice.yaml
-
   name: Entices Sip server configuration
   hosts: "{{ hostname }}"
   become: true
   become_user: root
   gather_facts: true
   tasks:
      - name: before check line count
        command: wc -l /etc/init.d/firewall_entice_local
        register: before_check
      - debug: var=before_check.stdout_lines

      - include_tasks: step1_iptables.yaml

      - name: after check line count
        command: wc -l /etc/init.d/firewall_entice_local
        register: after_check
      - debug: var=after_check.stdout_lines

      - include_tasks: step2_script_firewall.yaml
        when: before_check.stdout_lines != after_check.stdout_lines

      - include_tasks: step3_RG_group.yaml
        when: "'servera01' in ansible_facts['hostname'] and ( before_check.stdout_lines != after_check.stdout_lines )"

      - name: before check line count grafana
        command: wc -l /export/home/ens/scripts/RG_names_list.txt
        register: before_check_grafana
        when: "'servera01' in ansible_facts['hostname']"
      - debug: var=before_check_grafana.stdout_lines
        when: "'servera01' in ansible_facts['hostname']"

      - include_tasks: step4_RG_names.yaml
        when: "'servera01' in ansible_facts['hostname'] and ( before_check.stdout_lines != after_check.stdout_lines )"

      - name: after check line count grafana
        command: wc -l /export/home/ens/scripts/RG_names_list.txt
        register: after_check_grafana
        when: "'servera01' in ansible_facts['hostname']"
      - debug: var=after_check_grafana.stdout_lines
        when: "'servera01' in ansible_facts['hostname']"

      - include_tasks: step5_grafana.yaml
        when: "'servera01' in ansible_facts['hostname'] and ( before_check_grafana.stdout_lines != after_check_grafana.stdout_lines )"
