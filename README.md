<p align="center">
  <img src="assets/logo.png" alt="Tutor Assistant" width="128" height="128">
</p>

<h1 align="center">Tutor Assistant</h1>

<p align="center">
  Платформа для управления компьютерами в компьютерном классе:
  сервер с панелью управления, Telegram-бот <img src="https://img.shields.io/badge/в_разработке-yellow" alt="в разработке"> и агент на ПК учеников.
</p>

<p align="center">
  <img src="https://img.shields.io/github/v/release/talaev-sergey/tutor-assistant-releases?label=release" alt="Release">
  <img src="https://img.shields.io/github/downloads/talaev-sergey/tutor-assistant-releases/total" alt="Downloads">
  <img src="https://img.shields.io/badge/platform-Windows-0078D6?logo=windows&logoColor=white" alt="Platform">
  <img src="https://img.shields.io/badge/python-3.12%2B-blue?logo=python&logoColor=white" alt="Python">
</p>

---

## Что умеет приложение

Tutor Assistant — платформа для учителя, который ведёт занятия в компьютерном классе.
Состоит из трёх процессов, работающих в связке: **сервер** (API + веб-панель),
**Telegram-бот** и **агент**, который ставится на ученические ПК.

- **Управление с телефона через Telegram-бота** <img src="https://img.shields.io/badge/в_разработке-yellow" alt="в разработке">, адресно или сразу на весь класс.
- **Веб-панель управления** — тот же функционал в браузере.
- **Ограничения на ученических ПК** — блокировка рабочего стола, персонализации,
  параметров Windows, системных утилит, выхода из системы, установки программ,
  расширений браузера и отключение звука — каждое включается и выключается
  отдельным переключателем.
- **Режим урока** — быстрое применение набора ограничений на время занятия.
- **Экран блокировки поверх всех окон**.
- **Автообновление** — сервер и агент сами обновляются до последнего релиза
  при запуске или по кнопке «Проверить обновления».
- **Отчёт об ошибках прямо из панели** — кнопка «Сообщить об ошибках» открывает готовую
  форму issue на GitHub, ничего не отправляется в фоне и без ведома учителя.

## Скачать

Последний релиз со сборкой `tutor-installer.exe`:

<p>
  <a href="https://github.com/talaev-sergey/tutor-assistant-releases/releases/latest/download/tutor-assistent-installer-windows-x86_64.exe">
    <img src="https://img.shields.io/github/v/release/talaev-sergey/tutor-assistant-releases?style=for-the-badge&label=%D0%A1%D0%BA%D0%B0%D1%87%D0%B0%D1%82%D1%8C%20tutor-installer.exe&color=2ea44f&logo=github" alt="Скачать tutor-installer.exe">
  </a>
</p>

> [!IMPORTANT]
> Если VPN (например, AmneziaVPN) используется на сервере или на компьютерах
> учеников, самим VPN пользоваться можно — а вот **KillSwitch** нужно отключить
> на каждом из этих компьютеров перед установкой и работой с Tutor Assistant:
> он заворачивает весь трафик в VPN-туннель и рвёт связь по локальной сети
> между сервером и агентами на компьютерах учеников.
>
> В настройках VPN-клиента: **Настройки → Соединение → KillSwitch** → выключить.
>
> <img src="assets/screenshots/vpn/vpn-02-settings-menu.png" alt="Настройки VPN-клиента" height="220">
> <img src="assets/screenshots/vpn/vpn-03-connection-settings.png" alt="Раздел «Соединение»" height="220">
> <img src="assets/screenshots/vpn/vpn-04-killswitch.png" alt="Отключение KillSwitch" height="220">

## Установка

### Сервер (компьютер преподавателя)

Ставится один раз, на тот компьютер, с которого вы управляете классом:
API, панель управления и Telegram-бот.

1. Запустите `tutor-installer.exe` и выберите **«Сервер — компьютер преподавателя»**.

   <img src="assets/screenshots/server-01-select.png" alt="Выбор компонента: сервер" width="500">

2. Укажите параметры и нажмите **«Установить»**:

   - **Токен бота Telegram** — можно указать уже сейчас (получить у `@BotFather`),
     но управление через Telegram-бота пока
     <img src="https://img.shields.io/badge/в_разработке-yellow" alt="в разработке">,
     поле можно оставить пустым.
   - **Ваш Telegram-id** — можно оставить пустым: если поле пустое, командовать
     сможет кто угодно (актуально после того, как заработает Telegram-бот).
   - **Порт** — `8000` по умолчанию, обычно менять не нужно.

   <img src="assets/screenshots/server-02-config.png" alt="Настройка сервера" width="500">

3. После установки сервер покажет **адрес** и **ключ подключения** — они нужны для
   каждого клиента (компьютера ученика). Эти же данные сохраняются в файл
   `Tutor Assistant — адрес и ключ.txt` на рабочем столе — сохраните его, он
   пригодится, если понадобится подключить или переустановить агента на новом
   ученическом компьютере.

   <img src="assets/screenshots/server-03-done.png" alt="Сервер установлен: адрес и ключ подключения" width="700">

4. Веб-панель управления открывается ярлыком **Tutor Assistant** на рабочем столе.

   <img src="assets/screenshots/server-04-desktop-shortcut.png" alt="Ярлык Tutor Assistant на рабочем столе" width="200">

### Клиент (компьютер ученика)

Ставится на каждый компьютер ученика. Агент выполняет команды преподавателя,
подключаясь к серверу по адресу и ключу из установки сервера.

1. Запустите `tutor-installer.exe` на компьютере ученика и выберите
   **«Клиент — компьютер ученика»**.

   <img src="assets/screenshots/client-01-select.png" alt="Выбор компонента: клиент" width="500">

2. Введите **адрес сервера** и **ключ подключения** — они в том самом файле
   `Tutor Assistant — адрес и ключ.txt`, сохранённом на рабочем столе сервера
   (ключ один на весь класс). Поле **«Имя компьютера»** можно оставить как есть
   или задать любое своё — оно нужно только для удобства, потом его в любой
   момент можно переименовать в веб-панели сервера. Нажмите **«Установить»**.

   <img src="assets/screenshots/client-02-config.png" alt="Настройка клиента: адрес, ключ и имя компьютера" width="900">

3. При успешной установке компьютер ученика появится в веб-панели сервера.

   <img src="assets/screenshots/client-03-online.png" alt="Клиент появился в веб-панели сервера" width="700">

> [!WARNING]
> Задержка выполнения команд зависит от загруженности сети и качества сигнала
> Wi-Fi. При слабом сигнале или большой нагрузке на сеть команда может дойти
> до компьютера ученика с заметной задержкой.
