---
title: Установка расширений языка (Java) для SQL Server на Linux
description: Узнайте, как установить расширения языка (Java) для SQL Server в Red Hat, Ubuntu и SUSE.
author: dphansen
ms.author: davidph
ms.reviewer: vanto
manager: cgronlun
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3e86da652231a06cd28318096ada3ae3aed7526e
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531232"
---
# <a name="install-sql-server-2019-language-extensions-java-on-linux"></a>Установка расширений языка (Java) для SQL Server 2019 на Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Расширения языка — это надстройка ядра СУБД. Хотя [ядро СУБД и расширения языка можно установить одновременно](#install-all), рекомендуется сначала установить и настроить ядро СУБД SQL Server, чтобы устранить все неполадки, прежде чем добавлять дополнительные компоненты. 

Чтобы установить расширение языка Java, следуйте инструкциям в этой статье.

Пакет расширений Java находится в репозиториях исходного кода SQL Server для Linux. Если вы уже настроили репозитории исходного кода для ядра СУБД, команды установки пакета **mssql-server-extensibility-java** можно выполнить, используя ту же регистрацию репозиториев.

Расширения языка также поддерживаются в контейнерах Linux. Мы не предоставляем готовые контейнеры с расширениями языка, однако вы можете создать такой контейнер для SQL Server, используя [шаблон, доступный в GitHub](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices).

Расширения языка и [службы машинного обучения](../advanced-analytics/index.yml) устанавливаются по умолчанию в кластерах больших данных SQL Server. Если вы используете кластеры больших данных, нет необходимости выполнять действия, описанные в этой статье. Дополнительные сведения см. в разделе [Использование служб машинного обучения (Python и R) в кластерах больших данных](../big-data-cluster/machine-learning-services.md).

## <a name="uninstall-preview-version"></a>Удаление предварительной версии

Если вы установили предварительную версию (CTP или RC), рекомендуется удалить эту версию, чтобы удалить все предыдущие пакеты перед установкой SQL Server 2019. Параллельная установка нескольких версий не поддерживается, и список пакетов был изменен после выхода последних предварительных версий (CTP/RC).

### <a name="1-confirm-package-installation"></a>1. Подтверждение установки пакета

В качестве первого шага вам может потребоваться проверить наличие предыдущей установки. Следующие файлы указывают на существующую установку: checkinstallextensibility.sh, exthost, launchpad.

```bash
ls /opt/microsoft/mssql/bin
```

### <a name="2-uninstall-previous-ctprc-packages"></a>2. Удаление пакетов предыдущей версии CTP/RC

Выполняйте удаление на самом низком уровне пакета. Любой вышестоящий пакет, зависящий от пакета более низкого уровня, удаляется автоматически.

  + Для интеграции с Java удалите **mssql-server-extensibility-java**.

Команды для удаления пакетов приведены в таблице ниже.

| Платформа  | Команды для удаления пакетов | 
|-----------|----------------------------|
| RHEL  | `sudo yum remove msssql-server-extensibility-java` |
| SLES  | `sudo zypper remove msssql-server-extensibility-java` |
| Ubuntu    | `sudo apt-get remove msssql-server-extensibility-java`|

### <a name="3-install-sql-server-2019"></a>3. Установка SQL Server 2019

Выполните установку на самом верхнем уровне пакета, следуя инструкциям из этой статьи для вашей операционной системы.

Для каждого набора инструкций по установке, относящихся к определенной ОС, *наивысшим уровнем пакета* является **Пример 1. Полная установка** для полного набора пакетов либо **Пример 2. Минимальная установка** для минимального количества пакетов, необходимого для выполнения установки.

1. Выполните команды установки, используя диспетчеры пакетов и синтаксис для вашего дистрибутива Linux: 

   + [RedHat](#RHEL)
   + [Ubuntu](#ubuntu)
   + [SUSE](#suse)

## <a name="prerequisites"></a>предварительные требования

+ Версия Linux должна [поддерживаться SQL Server](sql-server-linux-release-notes-2019.md#supported-platforms), но не включает в себя подсистему Docker. Поддерживаемые версии

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [SUSE Enterprise Linux Server](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ У вас должно быть средство для выполнения команд T-SQL. Редактор запросов необходим для настройки и проверки после установки. Рекомендуется использовать бесплатное решение [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download?view=sql-server-2017#get-azure-data-studio-for-linux), работающее в Linux.

## <a name="package-list"></a>Список пакетов

На устройстве, подключенном к Интернету, пакеты скачиваются и устанавливаются независимо от ядра СУБД с помощью установщика пакетов для каждой операционной системы. В таблице ниже содержится описание доступных пакетов.

| Имя пакета | Область действия | Описание |
|--------------|----------|-------------|
|mssql-server-extensibility  | Все языки | Платформа расширяемости, используемая для расширения языка Java. |
|mssql-server-extensibility-java | Java | Платформа расширяемости, которая используется для расширения языка Java и включает среду выполнения Java. |

<a name="RHEL"></a>

## <a name="install-language-extensions"></a>Установка расширений языка

Расширения языка и Java можно установить в Linux путем установки пакета **mssql-server-extensibility-java**. При установке пакета **mssql-server-extensibility-java** автоматически устанавливается среда JRE 11, если она еще не установлена. Кроме того, путь к JVM добавляется в переменную среды JRE_HOME.

> [!Note]
> На сервере, подключенном к Интернету, зависимости пакета скачиваются и устанавливаются в рамках установки основного пакета. Если сервер не подключен к Интернету, см. дополнительные сведения в разделе об [автономной установке](#offline-install).

### <a name="redhat-install-command"></a>Команда установки для RedHat

Расширения языка для Java можно установить в RedHat с помощью приведенной ниже команды.

> [!Tip]
> По возможности запустите `yum clean all`, чтобы обновить пакеты в системе перед установкой.

```bash
# Install as root or sudo
sudo yum install mssql-server-extensibility-java
```

<a name="ubuntu"></a>

### <a name="ubuntu-install-command"></a>Команда установки для Ubuntu

Расширения языка для Java можно установить в Ubuntu с помощью приведенной ниже команды.

> [!Tip]
> По возможности запустите `apt-get update`, чтобы обновить пакеты в системе перед установкой. Кроме того, некоторые образы Docker в Ubuntu могут не иметь варианта транспорта apt https. Чтобы установить его, используйте `apt-get install apt-transport-https`.

```bash
# Install as root or sudo
sudo apt-get install mssql-server-extensibility-java
```

<a name="suse"></a>

### <a name="suse-install-command"></a>Команда установки для SUSE

Расширения языка для Java можно установить в SUSE с помощью приведенной ниже команды.

```bash
# Install as root or sudo
sudo zypper install mssql-server-extensibility-java
```

## <a name="post-install-config-required"></a>Настройка после установки (обязательно)

1. Предоставление разрешений в Linux

    Если используются внешние библиотеки, этот шаг выполнять не нужно. Рекомендуемый способ работы — использование внешних библиотек. Сведения о создании внешней библиотеки из JAR-файла см. в описании команды [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

    Если вы не используете внешние библиотеки, необходимо предоставить SQL Server разрешения на выполнение классов Java в JAR-файле.

    Чтобы предоставить доступ для чтения и выполнения к JAR-файлу, выполните приведенную ниже команду **chmod** для JAR-файла. При работе с SQL Server рекомендуется всегда помещать файлы классов в JAR-файл. Сведения о создании JAR-файла см. в статье [Создание JAR-файла](https://docs.microsoft.com/sql/language-extensions/how-to/create-a-java-jar-file-from-class-files).

    ```cmd
    chmod ug+rx <MyJarFile.jar>
    ```

    Кроме того, необходимо предоставить разрешения mssql_satellite на чтение и выполнение JAR-файла.

    ```cmd
    chown mssql_satellite:mssql_satellite <MyJarFile.jar>
    ```

    Дополнительная настройка осуществляется в основном с помощью [средства mssql-conf](sql-server-linux-configure-mssql-conf.md).

2. Добавьте учетную запись пользователя mssql, использованную для запуска службы SQL Server. Это необходимо, если вы не выполняли установку ранее.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

3. Включите исходящий сетевой доступ. По умолчанию исходящий сетевой доступ отключен. Чтобы включить исходящие запросы, задайте логическое свойство outboundnetworkaccess с помощью средства mssql-conf. Дополнительные сведения см. в статье [Настройка SQL Server на Linux с помощью средства mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-outbound-access).

   ```bash
   # Run as SUDO or root
   # Enable outbound requests over the network
   sudo /opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 1
   ```

4. Перезапустите службу панели запуска SQL Server и экземпляр ядра СУБД, чтобы считать обновленные значения из INI-файла. При изменении любого свойства, связанного с расширяемостью, появляется сообщение с напоминанием о необходимости перезапуска.  

   ```bash
   systemctl restart mssql-launchpadd

   systemctl restart mssql-server.service
   ```

5. Включите выполнение внешнего скрипта с помощью Azure Data Studio или другого средства, например SQL Server Management Studio (только для Windows), выполняющего скрипты Transact-SQL.

   ```bash
   EXEC sp_configure 'external scripts enabled', 1
   RECONFIGURE WITH OVERRIDE
   ```

6. Снова перезапустите службу `mssql-launchpadd`.

7. Для каждой базы данных, в которой необходимо использовать расширения языка, зарегистрируйте внешний язык с помощью команды [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql).

## <a name="register-external-language"></a>Регистрация внешнего языка

Для каждой базы данных, в которой необходимо использовать расширения языка, зарегистрируйте внешний язык с помощью команды [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql).

Следующий пример добавляет внешний язык Java в базу данных на сервере SQL Server на Linux.

```SQL
CREATE EXTERNAL LANGUAGE Java
FROM (CONTENT = N'<path-to-tar.gz>', FILE_NAME = 'javaextension.so');
GO
```

Дополнительные сведения см. в разделе [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql).

## <a name="verify-installation"></a>Проверка установки

Интеграция функций Java не включает в себя библиотеки, но можно выполнить команду `grep -r JRE_HOME /etc`, чтобы подтвердить создание переменной среды JAVA_HOME.

Чтобы проверить установку, запустите скрипт T-SQL, который выполняет системную хранимую процедуру, вызывающую Java. Для выполнения этой задачи потребуется средство обработки запросов. Хорошим выбором станет Azure Data Studio. Другие распространенные средства, такие как SQL Server Management Studio или PowerShell, подходят только для Windows. Если у вас есть компьютер под управлением Windows с этими средствами, используйте его для подключения к установке ядра СУБД Linux.

<a name="install-all"></a>

## <a name="full-install-of-sql-server-and-language-extensions"></a>Полная установка SQL Server и расширений языка

Вы можете установить и настроить ядро СУБД и расширения языка в одной процедуре, добавив параметры и пакеты Java в команду, устанавливающую ядро СУБД.

1. Укажите командную строку, включающую ядро СУБД, а также функции расширения языка.

  В установку ядра СУБД можно добавить расширяемость Java.

  ```bash
  sudo yum install -y mssql-server mssql-server-extensibility-java 
  ```

3. Примите условия лицензионных соглашений и завершите настройку после установки. Для этой задачи используйте средство **mssql-conf**.

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

  Вам будет предложено принять условия лицензионного соглашения для ядра СУБД, выбрать выпуск и задать пароль администратора. 

4. При появлении соответствующего запроса перезапустите службу.

  ```bash
  sudo systemctl restart mssql-server.service
  ```

## <a name="unattended-installation"></a>Автоматическая установка

С помощью [автоматической установки](https://docs.microsoft.com/sql/linux/sql-server-linux-setup#unattended) для ядра СУБД вы можете добавить пакеты для mssql-server-extensibility-java.

<a name="offline-install"></a>


## <a name="offline-installation"></a>Автономная установка

Описание шагов по установке пакетов см. в инструкциях по [автономной установке](sql-server-linux-setup.md#offline). Найдите сайт скачивания, а затем скачайте конкретные пакеты с помощью приведенного ниже списка.

> [!Tip]
> Некоторые средства управления пакетами предоставляют команды, помогающие определить зависимости пакетов. Для yum используйте `sudo yum deplist [package]`. Для Ubuntu используйте `sudo apt-get install --reinstall --download-only [package name]`, а затем `dpkg -I [package name].deb`.

#### <a name="download-site"></a>Сайт загрузки

Пакеты можно скачать по адресу [https://packages.microsoft.com/](https://packages.microsoft.com/). Все пакеты для Java размещены вместе с пакетом ядра СУБД. 

#### <a name="redhat7-paths"></a>Пути RedHat/7

|||
|--|----|
| Пакеты mssql/extensibility-java | [https://packages.microsoft.com/rhel/7/mssql-server-preview/](https://packages.microsoft.com/rhel/7/mssql-server-preview/) |

#### <a name="ubuntu1604-paths"></a>Пути Ubuntu/16.04

|||
|--|----|
| Пакеты mssql/extensibility-java | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/) |

#### <a name="suse12-paths"></a>Пути SUSE/12

|||
|--|----|
| Пакеты mssql/extensibility-java | [https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |

#### <a name="package-list"></a>Список пакетов

В зависимости от того, какие расширения вы хотите использовать, скачайте пакеты, необходимые для конкретного языка. Точные имена файлов содержат сведения о платформе в суффиксе, но приведенные ниже имена должны быть достаточно понятными, чтобы вы могли определить, какие файлы нужно получить.

```
# Core packages 
mssql-server-15.0.1000
mssql-server-extensibility-15.0.1000

# Java
mssql-server-extensibility-java-15.0.1000
```

## <a name="limitations"></a>Ограничения

+ Неявная проверка подлинности в настоящее время недоступна в Linux, поэтому вы не можете подключиться обратно к серверу из выполняемого скрипта Java для доступа к данным или другим ресурсам.

### <a name="resource-governance"></a>Управление ресурсами

С точки зрения [управления ресурсами](../t-sql/statements/create-external-resource-pool-transact-sql.md) для внешних пулов ресурсов между Linux и Windows наблюдается паритет, однако статистика для [sys.dm_resource_governor_external_resource_pools](../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) сейчас содержит другие единицы измерения для Linux. 
 
| Имя столбца   | Описание | Значение в Linux | 
|---------------|--------------|---------------|
|peak_memory_kb | Максимальный объем используемой памяти для пула ресурсов. | В Linux эта статистика извлекается из подсистемы memory CGroups, где используется значение memory.max_usage_in_bytes. |
|write_io_count | Общее число выполненных операций ввода-вывода записи с момента сброса статистики Resource Governor. | В Linux эта статистика извлекается из подсистемы blkio CGroups, где для строки write используется значение blkio.throttle.io_serviced. | 
|read_io_count | Общее число выполненных операций ввода-вывода чтения с момента сброса статистики Resource Governor. | В Linux эта статистика извлекается из подсистемы blkio CGroups, где для строки read используется значение blkio.throttle.io_serviced. | 
|total_cpu_kernel_ms | Совокупное время ядра использования ЦП, в миллисекундах, с момента сброса статистики Resource Governor. | В Linux эта статистика извлекается из подсистемы cpuacct CGroups, где для строки user используется значение cpuacct.stat. |  
|total_cpu_user_ms | Совокупное время использования ЦП, в миллисекундах, с момента сброса статистики Resource Governor.| В Linux эта статистика извлекается из подсистемы cpuacct CGroups, где для строки system используется значение cpuacct.stat. | 
|active_processes_count | Количество внешних процессов, выполняемых в момент запроса.| В Linux эта статистика извлекается из подсистемы pids CGroups, где используется значение pids.current. | 

## <a name="next-steps"></a>Следующие шаги

Разработчики на языке Java могут ознакомиться с простыми примерами, а также узнать, как код Java работает с SQL Server. Дополнительные сведения см. в следующих статьях:

+ [Учебник. Регулярные выражения с Java](../language-extensions/tutorials/search-for-string-using-regular-expressions-in-java.md)