# brm

Пакетный менеджер для Buildroot, позволяющий устанавливать дополнительные пакеты с внешних устройств на read-only системы, путем совмещения ФС при инициализации системы

Установка:
  1. Клонировать репозиторий в buildroot/package (в buildroot должны быть расширения для модульной сборки пакетов)
  2. Выполнить команду make menuconfig
  3. Включить опцию brm в разделе Target packages
  4. Сохранить изменения и выйти из меню конфигурации
  5. Выполнить команду make

Использование:
  Для того, чтобы brm мог работать с устройством, в его корне должен назодиться файл .modconfig с указанием путей ко всем пакетам на устройстве относительно него. Buildroot с расширением для сборки модульных пакетов при сборке пакетов в выбранную директорию (по умолчанию output/packages) генерирует .modconfig, поэтому для работы с устройством достаточно будет просто скопировать все содержиое этой директории вместе с .modconfig на внешнее устройство.
  
  При запуске brm автоматически найдет устройства с .modconfig и подключит все активные пакеты (по умолчанию все пакеты активны)
  
  Для просмотра списка активных пакетов нужно запустить скрипт brm без параметров. Форматом вывода будет устройство на котором находится пакет, а так же путь к этому пакету относительно устройства.
  
  Список параметров:
    
  -a - вывести все пакеты, в том числе неактивные (неактивные пакеты имеют символ # перед путем на устройстве)

  -y [путь к устройству] [путь к пакету] - включить пакет

  -n [путь к устройству] [путь к пакету] - выключить пакет 

  -h - вывести справочную информацию
