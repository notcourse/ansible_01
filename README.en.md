# Ansible Basics Practice: Variables and Playbook Run

## Goal
Learn to:
- run a playbook;
- change variables in inventory;
- understand the difference between files in the `group_vars` directory;
- verify execution results;
- get the required outcome according to the task condition.

## What is already in the project
- `site.yml` - a playbook that outputs `Hello, {{ who_am_i }}!`
- `inventory/hosts.yml` - inventory with hosts `test_01` and `test_02`
- `group_vars/all.yml` - a common variable in root `group_vars`
- `group_vars/group_one.yml` - a variable for group `group_one` in root `group_vars`
- `group_vars/group_two.yml` - a variable for group `group_two` in root `group_vars`

Important: in this exercise, you need to intentionally check both directories (`inventory/group_vars` and root `group_vars`) and record which value was actually applied.

## Commands to play with
```bash
pip3 install ansible
ansible-playbook -i inventory/hosts.yml site.yml
ansible -m setup localhost
ansible -m ping localhost
```

## Practice
1. Run the playbook and record the output for `test_01` and `test_02`.

2. Change `group_vars/all.yml` (`who_am_i`) and check the impact on both hosts.

3. Add `group_two` to `inventory/hosts.yml`, include `test_02` there, and check what now appears in the output.

4. Change `group_vars/all.yml` and `group_vars/group_one.yml` in the root. Record where they apply and where they are overridden by higher-priority sources.

5. Add a third host to inventory by analogy with the others, do not add it to groups, and rerun.

## Expected result
You should be able to:
- run the playbook without hints;
- intentionally change variables in `group_vars`;
- explain why a specific host got a specific value.

## Self-check
- The playbook runs without errors.
- Variable changes produce a predictable effect.
- Priority is explained: `group_vars/group_<number>` is higher than `group_vars/all.yml`.
