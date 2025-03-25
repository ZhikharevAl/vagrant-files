# Vagrant Configurations Repository

Репозиторий содержит готовые конфигурации Vagrant для развертывания виртуальных сред с Docker и базовыми серверами.

## Содержание

- [Доступные конфигурации](#доступные-конфигурации)
- [Требования](#требования)
- [Быстрый старт](#быстрый-старт)
- [Настройки виртуальных машин](#настройки-виртуальных-машин)
- [Использование](#использование)
- [Лицензия](#лицензия)

## Доступные конфигурации

### 1. Debian 12 с Docker

Файл: `debian-docker/Vagrantfile`

- Базовый образ: `debian/bookworm64`
- Характеристики:
  - 12GB RAM
  - 4 vCPU
  - Docker CE + дополнительные компоненты
- Особенности:
  - Проброс порта 8080 (host:8080 → guest:8080)
  - Настроенный Docker с поддержкой пользователя vagrant

### 2. Ubuntu Server (базовый)

Файл: `ubuntu-basic/Vagrantfile`

- Базовый образ: `hashicorp/bionic64`
- Характеристики:
  - 1GB RAM
  - 1 vCPU
- Особенности:
  - Минимальная конфигурация для тестирования
  - Bridged-сеть (public_network)

## Требования

- Vagrant 2.2+
- VirtualBox 6.0+
- 15GB свободного места на диске (для Debian-конфигурации)

## Быстрый старт

1. Клонируйте репозиторий:

   ```bash
   git clone https://github.com/ZhikharevAl/vagrant-files
   cd vagrant-files
   ```

2. Запустите нужную конфигурацию:

   ```bash
   # Для Debian с Docker
   cd debian-docker
   vagrant up

   # Для базового Ubuntu
   cd ubuntu-basic
   vagrant up
   ```

## Настройки виртуальных машин

### Debian 12 с Docker

- Автоматическая установка:
  - Docker CE
  - Docker Compose
  - Настроенные права для пользователя vagrant
- Сеть:
  - Публичная сеть (public_network)
  - Проброс порта 8080

### Ubuntu Server

- Чистая установка Ubuntu
- Только базовые настройки:
  - Bridged-сеть
  - Отключенная синхронизация папок

## Использование

После запуска Debian-конфигурации:

```bash
# Проверить работу Docker
vagrant ssh
docker run hello-world

# Доступ к портам (если сервис запущен на 8080)
curl http://localhost:8080
```

Для Ubuntu-конфигурации:

```bash
vagrant ssh
# Базовая система без дополнительных компонентов
```

## Управление ВМ

Общие команды:

```bash
# Запуск
vagrant up

# Остановка
vagrant halt

# Перезагрузка
vagrant reload

# Удаление
vagrant destroy
```

## Лицензия

MIT License. Подробнее в файле [LICENSE](LICENSE).
