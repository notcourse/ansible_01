# Ansible Basics Practice: Variables and Playbook Run

## Цель
Научиться:
- запускать playbook;
- изменять переменные в inventory;
- понимать разницу между файлами в директории`group_vars`;
- проверять результат выполнения;
- получать требуемый итог по условию задачи.

## Что уже есть в проекте
- `site.yml` - playbook, который выводит `Hello, {{ who_am_i }}!`
- `inventory/hosts.yml` - inventory с хостами `test_01` и `test_02`
- `group_vars/all.yml` - общая переменная в корневом `group_vars`
- `group_vars/group_one.yml` - переменная для группы `group_one` в корневом `group_vars`
- `group_vars/group_two.yml` - переменная для группы `group_two` в корневом `group_vars`

Важно: в этом упражнении нужно осознанно проверять обе директории (`inventory/group_vars` и корневой `group_vars`) и фиксировать, какое значение реально применилось.

## Команды для поиграться
```bash
pip3 install ansible
ansible-playbook -i inventory/hosts.yml site.yml
ansible -m setup localhost
ansible -m ping localhost
```

## Практика
1. Запусти playbook и зафиксируй вывод для `test_01` и `test_02`.

2. Измени `group_vars/all.yml` (`who_am_i`) и проверь влияние на оба хоста.

3. Добавь `group_two` в `inventory/hosts.yml`, включи туда `test_02`, проверь, что теперь получается в выводе.

4. Измени `group_vars/all.yml` и `group_vars/group_one.yml` в корне. Зафиксируй, где они влияют, а где перекрываются более приоритетными источниками.

5. Добавь третий хост в inventory по аналогии с остальными, не добавляй его в группы и повтори запуск.

## Ожидаемый результат
Ты должен уметь:
- запустить playbook без подсказок;
- осознанно менять переменные в `group_vars`;
- объяснить, почему конкретный хост получил конкретное значение.

## Проверка себя
- Playbook отрабатывает без ошибок.
- Изменения в переменных дают предсказуемый эффект.
- Объяснен приоритет: `group_vars/group_<number>` выше `group_vars/all.yml`.
