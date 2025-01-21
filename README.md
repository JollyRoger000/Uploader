# FTP Uploader

Этот скрипт предназначен для загрузки файлов на FTP-сервер. Он использует конфигурационный файл для настройки параметров подключения и логирует процесс загрузки в консоль и файл.

---

## Описание

Скрипт выполняет следующие задачи:

1. Читает параметры подключения к FTP-серверу из конфигурационного файла `config.json`.
2. Проверяет доступность FTP-сервера.
3. Загружает указанные файлы (`firmware` и `storage`) на сервер.
4. Отображает прогресс загрузки с помощью progress bar.
5. Логирует все действия в консоль и файл `upload.log`.

---

## Требования

Для работы скрипта необходимы следующие библиотеки:

- `ftplib` (встроенная в Python)
- `logging` (встроенная в Python)
- `json` (встроенная в Python)
- `socket` (встроенная в Python)
- `tqdm` (для отображения progress bar)

Установите недостающие библиотеки с помощью pip:

```bash
pip install tqdm
```

---

## Конфигурация

Перед запуском скрипта создайте файл `config.json` в той же директории, где находится скрипт. Пример содержимого файла:

```json
{
  "host": "ftp.example.com",
  "user": "username",
  "password": "password",
  "remote_folder": "/path/to/remote/folder",
  "firmware_file": "firmware.bin",
  "storage_file": "storage.bin"
}
```

### Параметры:

- `host`: Адрес FTP-сервера.
- `user`: Имя пользователя для подключения.
- `password`: Пароль для подключения.
- `remote_folder`: Путь к папке на сервере, куда будут загружены файлы.
- `firmware_file`: Путь к локальному файлу `firmware`.
- `storage_file`: Путь к локальному файлу `storage`.

---

## Использование

1. Убедитесь, что файл `config.json` настроен правильно.
2. Запустите скрипт:
   ```bash
   python upload.py
   ```

### Пример вывода в консоль:

```
2023-10-10 12:00:00,000 - INFO - Соединение c ftp.example.com успешно установлено.
firmware.bin: 100%|████████████████████| 50.0M/50.0M [00:10<00:00, 5.00MB/s]
2023-10-10 12:00:10,123 - INFO - Файл firmware.bin успешно загружен.
storage.img:  75%|██████████████▌      | 75.0M/100.0M [00:15<00:05, 5.00MB/s]
2023-10-10 12:00:25,456 - INFO - Файл storage.img успешно загружен.
```

---

## Логирование

Скрипт логирует все действия в консоль и файл `upload.log`. Формат логов:

```
<дата и время> - <уровень> - <сообщение>
```

Пример содержимого файла `upload.log`:

```
2023-10-10 12:00:00,000 - INFO - Соединение c ftp.example.com успешно установлено.
2023-10-10 12:00:10,123 - INFO - Файл firmware.bin успешно загружен.
2023-10-10 12:00:25,456 - INFO - Файл storage.img успешно загружен.
```

---

## Обработка ошибок

Скрипт обрабатывает следующие ошибки:

- Отсутствие или недоступность конфигурационного файла.
- Отсутствие или недоступность файлов для загрузки.
- Недоступность FTP-сервера.
- Ошибки при загрузке файлов.

В случае ошибки скрипт логирует её и завершает выполнение.

---

## Пример использования

1. Создайте файл `config.json`:

   ```json
   {
     "host": "ftp.example.com",
     "user": "username",
     "password": "password",
     "remote_folder": "/uploads",
     "firmware_file": "firmware.bin",
     "storage_file": "storage.bin"
   }
   ```

2. Убедитесь, что файлы `firmware.bin` и `storage.bin` существуют.

3. Запустите скрипт:
   ```bash
   python upload.py
   ```

---

## Лицензия

Этот проект распространяется под лицензией MIT. Подробности см. в файле [LICENSE](LICENSE).

---

## Автор

JollyRoger000 aka Roman Volkov (https://github.com/JollyRoger000)  
mailto:r.y.volkov@gmail.com
