# Ansible Basics Practice: Variables and Playbook Run

## Цель
Научиться:
- запускать playbook;
- изменять переменные в inventory;
- понимать разницу между `inventory/group_vars` и `group_vars` в корне;
- проверять результат выполнения;
- получать требуемый итог по условию задачи.

## Что уже есть в проекте
- `site.yml` - playbook, который выводит `Hello, {{ who_am_i }}!`
- `inventory/hosts.yml` - inventory с хостами `test_01` и `test_02`
- `inventory/group_vars/all.yml` - общая переменная для всех хостов
- `inventory/group_vars/group_two.yml` - переменная для группы `group_two`
- `inventory/host_vars/test_01.yml` - переменная для хоста `test_01`
- `group_vars/all.yml` - общая переменная в корневом `group_vars`
- `group_vars/group_one.yml` - переменная для группы `group_one` в корневом `group_vars`
- `group_vars/group_two.yml` - переменная для группы `group_two` в корневом `group_vars`

Важно: в этом упражнении нужно осознанно проверять обе директории (`inventory/group_vars` и корневой `group_vars`) и фиксировать, какое значение реально применилось.

## Команды для поиграться
```bash
ansible-playbook -i inventory/hosts.yml site.yml
ansible -m setup localhost
ansible -m ping localhost
```

## Практика
1. Запусти playbook и зафиксируй вывод для `test_01` и `test_02`.

2. Измени `inventory/group_vars/all.yml` (`who_am_i`) и проверь влияние на оба хоста.

3. Создай `inventory/host_vars/test_02.yml` с `who_am_i` и проверь, что для `test_02` побеждает host-level переменная.

4. Добавь `group_two` в `inventory/hosts.yml`, включи туда `test_02`, затем сравни влияние:
- `inventory/group_vars/group_two.yml`
- `group_vars/group_two.yml`

5. Измени `group_vars/all.yml` и `group_vars/group_one.yml` в корне. Зафиксируй, где они влияют, а где перекрываются более приоритетными источниками.

6. Удали/переименуй `inventory/host_vars/test_02.yml` и повтори запуск, чтобы проверить fallback на group-level.

## Ожидаемый результат
Ты должен уметь:
- запустить playbook без подсказок;
- осознанно менять переменные в `group_vars` и `host_vars`;
- объяснить, почему конкретный хост получил конкретное значение.

## Проверка себя
- Playbook отрабатывает без ошибок.
- Изменения в переменных дают предсказуемый эффект.
- Объяснен приоритет: `host_vars` выше `group_vars`.
- Объяснено влияние `inventory/group_vars` и корневого `group_vars`.

## Задание для смелых
Нужно добавить хосты, которые смогут использовать максимальное количество переменных из group и host_vars. Возможно, для этого придётся сделать несколько разных инвентори.
