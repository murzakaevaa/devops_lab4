# Lab 4. Ansible Basics (П04)

## Схема взаимодействия
- **VM-1 (Control node)**: 10.0.2.15 (Ansible)
- **VM-2 (Managed node)**: 10.0.2.16 (nginx)

## Что было сделано (по методичке)
1. Отключен cron-скрипт `weather.sh` из прошлой лабораторной работы.
2. Клонирована первая VM во вторую с опцией «сгенерировать новые MAC-адреса».
3. Создана и настроена общая сеть NAT (NatNetwork) с адресацией 10.0.2.0/24.
4. Заданы статические IP-адреса для обеих машин (10.0.2.15 и 10.0.2.16).
5. Создан пользователь `runner` с правами `sudo` без пароля на обеих VM.
6. Настроен SSH-доступ по ключу с VM-1 на VM-2 (для пользователя `runner`).
7. Установлен Ansible на первую VM (Control node).
8. Написан плейбук `playbook.yml` для установки веб-сервера Nginx.
9. Написан файл `inventory.ini` с адресом второй VM.
10. Создан шаблон `index.html` для деплоя.
11. Выполнен тестовый прогон плейбука (`--check`).
12. Выполнен боевой прогон плейбука.
13. Проверена работа веб-сервера с помощью `curl`.
14. Продемонстрирована идемпотентность Ansible (повторный запуск не вносит изменений).

## Файлы в репозитории
- `inventory.ini` — инвентарный файл со списком хостов.
- `playbook.yml` — плейбук для установки Nginx и копирования HTML.
- `index.html` — стартовая страница.


## Скриншоты выполнения

1. [Проверка crontab и IP на VM-1](screenshots/01-crontab-and-ip-vm1.png)
2. [Пинг с VM-1 до VM-2](screenshots/02-ping-vm1-to-vm2.png)
3. [Пинг в интернет (1.1.1.1)](screenshots/03-ping-internet.png)
4. [Копирование SSH-ключа (ssh-copy-id)](screenshots/04-ssh-copy-id-success.png)
5. [Вход по SSH без пароля](screenshots/05-ssh-login-without-password.png)
6. [Вход по SSH без пароля (повтор)](screenshots/06-ssh-login-without-password.png)
7. [Проверка sudo без пароля на VM-1](screenshots/07-sudo-su-vm1.png)
8. [Проверка sudo без пароля на VM-2](screenshots/08-sudo-su-vm2.png)
9. [Версия установленного Ansible](screenshots/09-ansible-version.png)
10. [Содержимое inventory.ini](screenshots/10-inventory-content.png)
11. [Содержимое playbook.yml (начало)](screenshots/11-inventory-content.png)
12. [Содержимое index.html](screenshots/12-index-html-content.png)
13. [Проверка связи Ansible с VM-2 (ping)](screenshots/13-ansible-ping-test.png)
14. [Удаление nginx на VM-2 перед запуском](screenshots/14-nginx-removed-on-vm2.png)
15. [Тестовый прогон плейбука (--check)](screenshots/15-check-mode-dry-run.png)
16. [Боевой прогон плейбука (установка nginx)](screenshots/16-playbook-deploy-run.png)
17. [Проверка работы веб-сервера (curl)](screenshots/17-curl-web-page-result.png)
18. [Повторный прогон для проверки идемпотентности (changed=0)](screenshots/18-idempotency-run.png)
19. [Результат в браузере - Hello from Ansible playbook!](screenshots/19-browser-hello.png)
