# Ansible Basics Practice: Variables and Playbook Run

## Goal
Learn to:
- run a playbook;
- change variables in inventory;
- understand the difference between `inventory/group_vars` and root `group_vars`;
- verify execution results;
- get the required outcome according to the task condition.

## What is already in the project
- `site.yml` - a playbook that outputs `Hello, {{ who_am_i }}!`
- `inventory/hosts.yml` - inventory with hosts `test_01` and `test_02`
- `inventory/group_vars/all.yml` - a common variable for all hosts
- `inventory/group_vars/group_two.yml` - a variable for group `group_two`
- `inventory/host_vars/test_01.yml` - a variable for host `test_01`
- `group_vars/all.yml` - a common variable in root `group_vars`
- `group_vars/group_one.yml` - a variable for group `group_one` in root `group_vars`
- `group_vars/group_two.yml` - a variable for group `group_two` in root `group_vars`

Important: in this exercise, you need to intentionally check both directories (`inventory/group_vars` and root `group_vars`) and record which value was actually applied.

## Commands to play with
```bash
ansible-playbook -i inventory/hosts.yml site.yml
ansible -m setup localhost
ansible -m ping localhost
```

## Practice
1. Run the playbook and record the output for `test_01` and `test_02`.

2. Change `inventory/group_vars/all.yml` (`who_am_i`) and check the impact on both hosts.

3. Create `inventory/host_vars/test_02.yml` with `who_am_i` and verify that the host-level variable wins for `test_02`.

4. Add `group_two` to `inventory/hosts.yml`, include `test_02` there, then compare the impact of:
- `inventory/group_vars/group_two.yml`
- `group_vars/group_two.yml`

5. Change `group_vars/all.yml` and `group_vars/group_one.yml` in the root. Record where they apply and where they are overridden by higher-priority sources.

6. Delete/rename `inventory/host_vars/test_02.yml` and rerun to check fallback to group-level.

## Expected result
You should be able to:
- run the playbook without hints;
- intentionally change variables in `group_vars` and `host_vars`;
- explain why a specific host got a specific value.

## Self-check
- The playbook runs without errors.
- Variable changes produce a predictable effect.
- Priority is explained: `host_vars` is higher than `group_vars`.
- The impact of `inventory/group_vars` and root `group_vars` is explained.

## Task for the brave
You need to add hosts that can use the maximum possible number of variables from group and host_vars. It may require creating several different inventories.
