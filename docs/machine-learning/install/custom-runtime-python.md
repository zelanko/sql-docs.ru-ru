---
title: Установка настраиваемой среды выполнения Python
description: Узнайте, как установить настраиваемую среду выполнения Python для SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 09/20/2020
ms.topic: how-to
author: cawrites
ms.author: chadam
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d02217eaae3cf402a1ccb6e08780f4e9406d446f
ms.sourcegitcommit: afb02c275b7c79fbd90fac4bfcfd92b00a399019
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2020
ms.locfileid: "91956396"
---
# <a name="install-a-python-custom-runtime-for-sql-server"></a>Установка настраиваемой среды выполнения Python для SQL Server
[!INCLUDE [SQL Server 2019 and later](../../includes/applies-to-version/sqlserver2019.md)]

В этой статье описывается, как установить настраиваемую среду выполнения для запуска скриптов Python с SQL Server. Настраиваемая среда выполнения использует технологию расширения языка, созданную на основе платформы расширяемости, для выполнения внешнего кода. Настраиваемую среду выполнения Python можно использовать в следующих сценариях:

+ Установка SQL Server с платформой расширяемости.

+ Установка Служб машинного обучения с SQL Server 2019. Расширение языка можно использовать со [Службами машинного обучения SQL Server ](../sql-server-machine-learning-services.md) после выполнения некоторых дополнительных этапов настройки.

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"

> [!NOTE]
> В этой статье описывается, как установить настраиваемую среду выполнения для Python в Windows. Об установке на Linux см. статью [Установка настраиваемой среды выполнения Python для SQL Server на Linux](custom-runtime-python.md?view=sql-server-linux-ver15&preserve-view=true).



## <a name="pre-install-checklist"></a>Контрольный список перед установкой

Перед установкой настраиваемой среды выполнения Python установите следующие компоненты.

+ [SQL Server 2019 для Windows с накопительным обновлением 3 или более поздней версии](../../database-engine/install-windows/install-sql-server.md).

  > [!NOTE]
  > Для настраиваемой среды выполнения Python требуется накопительное обновление (CU) 3 или более поздняя версия для SQL Server 2019.

+ [Расширения языка SQL Server для Windows с платформой расширяемости](../../language-extensions/install/install-sql-server-language-extensions-on-windows.md).

+ [Python 3.7]( https://www.python.org/downloads/release/python-379/).

## <a name="add-sql-server-language-extensions-for-windows"></a>Добавление расширений языка SQL Server для Windows

> [!NOTE]
> Если на SQL Server 2019 установлены Службы машинного обучения, то платформа расширяемости уже установлена и этот шаг можно пропустить.

Расширения языка используют платформу расширяемости для исполнения внешнего кода. Выполнение кода изолировано от процессов ядра, но полностью интегрировано с выполнением запросов SQL Server.

1. Запустите мастер установки SQL Server 2019.
  
1. На вкладке **Установка** выберите параметр **Новая установка изолированного экземпляра SQL Server или добавление компонентов к существующей установке**.
    
    ![Установка SQL Server 2019 с накопительным обновлением 3 или более поздней версии](../install/media/2019setup-installation-page-mlsvcs.png) 

1. На странице **Выбор компонентов** выберите следующие компоненты:
  
    - **Службы ядра СУБД**
  
        Чтобы использовать расширения языка с SQL Server, необходимо установить экземпляр ядра СУБД. Можно использовать экземпляр по умолчанию или именованный экземпляр.
  
    - **Службы машинного обучения и расширения языка**
   
       Выберите **Службы машинного обучения и расширения языка**. Нет необходимости выбирать Python.

    ![Возможности установки SQL Server 2019 с накопительным обновлением 3 или более поздней версии](../install/media/sql-feature-selection.png) 

1. На странице **Все готово для установки** проверьте, включены ли указанные ниже компоненты, и нажмите **Установить**.
  
    + Службы ядра СУБД
    + Службы машинного обучения и расширения языка

1. Если после завершения установки будет предложено перезагрузить компьютер, выполните перезагрузку. После завершения установки важно прочитать сообщение мастера установки. Дополнительные сведения см. в разделе [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).


## <a name="install-python-37"></a>установите Python 3.7; 

Установите [Python 3.7]( https://www.python.org/downloads/release/python-379/) и добавьте его в переменную PATH.

![Добавьте Python 3.7 в путь.](../install/media/python-379.png) 


#### <a name="install-pandas"></a>Установка Pandas

Установите пакет [Pandas](https://pandas.pydata.org/) для Python из командной строки *с повышенными привилегиями*:

```bash
python.exe -m pip install pandas
```

## <a name="update-the-system-environment-variables"></a>Обновление системных переменных среды

Добавьте или измените PYTHONHOME как системную переменную среды.

+ В поле поиска Windows введите "среда" и выберите **Изменение системных переменных среды**.
+ На вкладке **Дополнительно** выберите **Переменные среды**.
+ В разделе **Системные переменные**выберите **Создать**, чтобы создать PYTHONHOME с указанием на расположение установки Python 3.7.
Если PYTHONHOME уже существует, выберите **Изменить**, чтобы он указывал на расположение установки Python 3.7.
+ Нажмите **ОК**, чтобы закрыть остальные окна.

![Создайте системную переменную PYTHONHOME.](../install/media/sys-pythonhome.png)

## <a name="grant-access-to-the-custom-python-installation-folder"></a>Предоставление доступа к настраиваемой папке установки Python

Выполните команды **icacls** из новой командной строки *с повышенными привилегиями*, чтобы предоставить разрешение на чтение и выполнение в PYTHONHOME для **имени пользователя службы панели запуска SQL Server** и идентификатора безопасности **S-1-15-2-1** (**ВСЕ ПАКЕТЫ ПРИЛОЖЕНИЙ**). Имя пользователя службы панели запуска имеет вид `NT Service\MSSQLLAUNCHPAD$INSTANCENAME* where INSTANCENAME` — это имя экземпляра SQL Server. Эти команды будут рекурсивно предоставлять доступ ко всем файлам и папкам в указанном каталоге.

Добавьте имя экземпляра в `MSSQLLAUNCHPAD` (`MSSQLLAUNCHPAD$INSTANCENAME`). В этом примере INSTANCENAME — экземпляр по умолчанию `MSSQLSERVER`.

1. Предоставьте разрешения **имени пользователя службы панели запуска SQL Server**.

    ```cmd
    icacls "%PYTHONHOME%" /grant "NT Service\MSSQLLAUNCHPAD$MSSQLSERVER":(OI)(CI)RX /T

2. Give permissions to **SID S-1-15-2-1**.
    ```cmd
    icacls "%PYTHONHOME%" /grant *S-1-15-2-1:(OI)(CI)RX /T

>[!NOTE]
>The preceding command grants permissions to the computer **SID S-1-15-2-1**, which is equivalent to ALL APPLICATION PACKAGES on an English version of Windows. Alternatively, you can use `icacls "%R_HOME%" /grant "ALL APPLICATION PACKAGES":(OI)(CI)RX /T` on an English version of Windows.

## Restart SQL Server Launchpad service

From an *elevated* command prompt, run the following commands. Replace "MSSQLSERVER" with the name of your SQL Server instance.

```CMD
net stop MSSQLLAUNCHPAD$MSSQLSERVER
net start MSSQLLAUNCHPAD$MSSQLSERVER
```

В качестве альтернативы щелкните правой кнопкой мыши службу панели запуска SQL Server в приложении системы **Службы** и нажмите на команду **Перезапустить**. Или используйте [диспетчер конфигурации SQL Server](../../relational-databases/sql-server-configuration-manager.md), чтобы перезапустить службу.

## <a name="download-python-language-extension"></a>Скачивание расширения языка Python

Скачайте [ZIP-файл с расширением языка Python для Windows](https://github.com/microsoft/sql-server-language-extensions/releases). Рекомендуется использовать версию выпуска в рабочей среде. Используйте версию для отладки в среде разработки или тестирования, так как она предоставляет журналы с подробными сведениями, позволяющими анализировать ошибки.

## <a name="register-external-language"></a>Регистрация внешнего языка

С помощью команды [CREATE EXTERNAL LANGUAGE](../../t-sql/statements/create-external-language-transact-sql.md) зарегистрируйте внешний язык для каждой базы данных, в которой необходимо использовать расширение языка Python. Используйте [Azure Data Studio](../../azure-data-studio/download-azure-data-studio.md) для подключения к SQL Server и выполнения следующей команды T-SQL. Измените путь в этом операторе таким образом, чтобы он отражал расположение скачанного ZIP-файла расширения языка (python-lang-extension.zip).

> [!NOTE]
> Python — зарезервированное слово. Используйте другое имя для внешнего языка, например "myPython".

```sql
CREATE EXTERNAL LANGUAGE [myPython]
FROM (CONTENT = N'/path/to/python-lang-extension.zip', FILE_NAME = 'pythonextension.dll');
GO
```

::: moniker-end

::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"

Вы можете установить SQL Server на платформах Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) и Ubuntu. Дополнительные сведения см. в разделе ["Поддерживаемые платформы" в руководстве по установке SQL Server на Linux](../../linux/sql-server-linux-setup.md).

> [!NOTE]
> В этой статье описывается, как установить настраиваемую среду выполнения для Python на Linux. Об установке в Windows см. статью [Установка настраиваемой среды выполнения Python для SQL Server в Windows](custom-runtime-python.md?view=sql-server-ver15&preserve-view=true)

## <a name="pre-install-checklist"></a>Контрольный список перед установкой

Перед установкой настраиваемой среды выполнения Python установите следующие компоненты.

+ [SQL Server 2019 для Linux (накопительное обновление 3 или более поздней версии)](../../linux/sql-server-linux-setup.md).
При установке SQL Server на Linux необходимо настроить репозиторий Майкрософт. Дополнительные сведения см. в статье [настройка репозиториев](../../linux/sql-server-linux-change-repo.md)

  > [!NOTE]
  > Для настраиваемой среды выполнения Python требуется накопительное обновление (CU) 3 или более поздняя версия для SQL Server 2019.

+ [Расширения языка SQL Server на Linux с платформой расширяемости](../../linux/sql-server-linux-setup-language-extensions.md).

+ [Python 3.7](https://www.python.org/downloads/release/python-379/).

## <a name="add-sql-server-language-extensions-for-linux"></a>Добавление расширений языка SQL Server для Linux

> [!NOTE]
> Если на SQL Server 2019 установлены Службы машинного обучения, то пакет **mssql-server-extensibility** для расширений языка уже установлен и этот шаг можно пропустить.

Расширения языка используют платформу расширяемости для исполнения внешнего кода. Выполнение кода изолировано от процессов ядра, но полностью интегрировано с выполнением запросов SQL Server.

Чтобы установить расширения языка, используйте следующие команды с учетом вашей версии Linux.

### <a name="ubuntu"></a>Ubuntu
> [!TIP]
> По возможности запустите `update`, чтобы обновить пакеты в системе перед установкой. Ubuntu может не иметь параметр https apt transport. Чтобы установить его, используйте `apt-get install apt-transport-https`.

```bash
# Install as root or sudo
sudo apt-get install mssql-server-extensibility
```

### <a name="red-hat"></a>Red Hat
```bash
# Install as root or sudo
sudo yum install mssql-server-extensibility
```

### <a name="suse"></a>Suse
```bash
# Install as root or sudo
sudo zypper install mssql-server-extensibility
```

## <a name="install-python-37-and-pandas"></a>Установка Python 3.7 и Pandas

Установите Python 3.7, библиотеку libpython3.7 и пакет Pandas. 

Ниже приведены примеры команд для Ubuntu.

```bash
# Install python3.7 and the corresponding library:
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
sudo apt-get install python3.7 python3-pip libpython3.7

# Install pandas to /usr/lib:
sudo python3.7 -m pip install pandas -t /usr/lib/python3.7/dist-packages
```

## <a name="using-a-custom-installation-of-python-37"></a>Использование настраиваемой установки Python 3.7

> [!NOTE]
> Если выбрана установка Python в папку по умолчанию `/usr/lib/python3.7`, можно пропустить этот этап и перейти [к следующему этапу](#download-python-linux).

Если вы создали собственную версию Python 3.7, используйте следующие команды, чтобы SQL Server мог найти и загрузить настраиваемую установку.

### <a name="update-the-environment-variables"></a>Обновление переменных среды

1. Измените службу mssql-launchpadd, чтобы добавить переменную среды PYTHONHOME в файл `/etc/systemd/system/mssql-launchpadd.service.d/override.conf`

      ```bash
      sudo systemctl edit mssql-launchpadd
      ```

    + Вставьте следующий текст в открывающийся файл `/etc/systemd/system/mssql-launchpadd.service.d/override.conf`. Установите значение параметра PYTHONHOME в соответствии с настраиваемым путем установки Python.

      ```vi
      [Service]
      Environment="PYTHONHOME=/path/to/installation/of/python3.7"
      ```

    + Сохраните и закройте файл.

2. Убедитесь, что можно загрузить `libpython3.7m.so.1.0`.

    + Создайте файл custom-python.conf в `/etc/ld.so.conf.d`.

      ```bash
      sudo vi /etc/ld.so.conf.d/custom-python.conf
      ```

    + В открывшийся файл добавьте путь к **libpython3.7m.so.1.0** из настраиваемой установки Python.

      ```vi
      /path/to/installation/of/python3.7/lib
      ```

    + Сохраните и закройте новый файл.

    + Запустите `ldconfig` и убедитесь, что можно загрузить `libpython3.7m.so.1.0`, выполнив следующую команду и проверив наличие всех зависимых библиотек.

      ```bash
      sudo ldconfig
      ldd /path/to/installation/of/python3.7/lib/libpython3.7m.so.1.0
      ```

### <a name="grant-access-to-the-custom-python-folder"></a>Предоставление доступа к папке установки Python

Присвойте параметру `datadirectories` в разделе "Расширяемость" файла /var/opt/mssql/mssql.conf значение настраиваемой установки Python.

```bash
sudo /opt/mssql/bin/mssql-conf set extensibility.datadirectories /path/to/installation/of/python3.7
```

### <a name="restart-the-mssql-launchpadd-service"></a>Перезапуск службы mssql-launchpadd

```bash
sudo systemctl restart mssql-launchpadd
```
## <a name="download-python-language-extension"></a><a name="download-python-linux"></a>Скачивание расширения языка Python

Скачайте [ZIP-файл с расширением языка Python для Linux](https://github.com/microsoft/sql-server-language-extensions/releases). Рекомендуется использовать версию выпуска в рабочей среде. Используйте версию для отладки в среде разработки или тестирования, так как она предоставляет журналы с подробными сведениями, позволяющими анализировать ошибки.

## <a name="register-external-language"></a>Регистрация внешнего языка

С помощью команды [CREATE EXTERNAL LANGUAGE](../../t-sql/statements/create-external-language-transact-sql.md) зарегистрируйте внешний язык для каждой базы данных, в которой необходимо использовать расширение языка Python. Используйте [Azure Data Studio](../../azure-data-studio/download-azure-data-studio.md) для подключения к SQL Server и выполнения следующей команды T-SQL. 
Измените путь в этом операторе таким образом, чтобы он отражал расположение скачанного ZIP-файла расширения языка (python-lang-extension.zip).

> [!NOTE]
>Python — зарезервированное слово. Используйте другое имя для внешнего языка, например "myPython".

```sql
CREATE EXTERNAL LANGUAGE myPython 
FROM (CONTENT = N'/PATH/TO/python-lang-extension.zip', FILE_NAME = 'libPythonExtension.so.1.0');
GO
```

::: moniker-end

## <a name="enable-external-script-execution-in-sql-server"></a>Включение выполнения внешнего скрипта в SQL Server

Внешний скрипт в Python может быть выполнен с помощью хранимой процедуры [sp_execute_external script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), запускаемой на SQL Server. 

Чтобы включить внешние скрипты, выполните следующие команды SQL с помощью [Azure Data Studio](../../azure-data-studio/download-azure-data-studio.md), подключенного к SQL Server.

```sql
sp_configure 'external scripts enabled', 1;
RECONFIGURE WITH OVERRIDE;  
```

## <a name="verify-language-extension-installation"></a>Проверка установки расширения языка

Этот скрипт SQL проверяет функциональность установленного расширения языка.

```sql
EXEC sp_execute_external_script
@language =N'myPython',
@script=N'
import sys
print(sys.path)
print(sys.version)
print(sys.executable)'
```

## <a name="verify-parameters-and-datasets-of-different-data-types"></a>Проверка параметров и наборов данных различных типов

Этот скрипт проверяет различные типы данных для входных и выходных параметров и наборов данных.

```sql
DECLARE @sumVal int = 12;
DECLARE @charVal VARCHAR(30) = N'Hello'

EXEC sp_execute_external_script
@language =N'myPython',
@script=N'
print(sumVal)
print(charVal)
sumVal = sumVal + 300
OutputDataSet = InputDataSet'
,@input_data_1 = N'SELECT 1, CAST(1.4 as real), ''Hi'', CAST(''1'' as bit)'
,@params = N'@sumVal int OUTPUT, @charVal VARCHAR(30)'
,@sumVal = @sumVal OUTPUT
,@charVal = @charVal
WITH RESULT SETS ((intCol int, doubleCol real, charCol char(2), logicalCol bit));

PRINT @sumVal
```

## <a name="next-steps"></a>Дальнейшие действия

+ [Платформа расширяемости в SQL Server](../concepts/extensibility-framework.md)
+ [Общие сведения о расширениях языка](../../language-extensions/language-extensions-overview.md)