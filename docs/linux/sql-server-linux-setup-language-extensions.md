---
title: Установка расширения языка (Java) для SQL Server в Linux | Документация Майкрософт
description: Сведения об установке расширения языка (Java) для SQL Server в Red Hat, Ubuntu и SUSE.
author: dphansen
ms.author: davidph
manager: cgronlun
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8c796d8f445f4cc1b02a0f49d12cde55e0a7ab4b
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719376"
---
# <a name="install-sql-server-2019-language-extensions-java-on-linux"></a>Установка расширения языка SQL Server 2019 г. (Java) в Linux

Расширения языка являются надстройку к компоненту database engine. Несмотря на то, что вы можете [одновременно установить компонент database engine и расширения языка](#install-all), это лучший способ сначала установите и настройте компонент SQL Server database engine, устранить все проблемы перед добавлением дополнительные компоненты. 

Выполните действия, описанные в этой статье, чтобы установить расширение языка Java.

Пакет расширений Java находится в репозитории исходного SQL Server Linux. Если вы уже настроили репозиториях для установки ядра базы данных, вы можете запустить **mssql-server расширяемости java** упаковать команды установки, используя регистрацию репозитория.

Расширения языка также поддерживается в контейнерах Linux. Мы не предоставляем готовые контейнеры с помощью расширений языка, но можно создать один из контейнеров SQL Server, с помощью [пример шаблона доступен на сайте GitHub](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices).

## <a name="uninstall-previous-ctp"></a>Удаление предыдущей CTP-версии

Список пакетов изменилось за последние несколько выпусков CTP, приводит к меньшим числом пакетов. Мы рекомендуем удалить CTP-версии 2.x, чтобы удалить все предыдущие пакеты перед установкой CTP-версии 3.0. Side-by-side установку нескольких версий не поддерживается.

### <a name="1-confirm-package-installation"></a>1. Подтверждение установки пакета

Можно проверить существование из предыдущей установки в качестве первого шага. Указать существующую установку, следующие файлы: checkinstallextensibility.sh, exthost, панели запуска.

```bash
ls /opt/microsoft/mssql/bin
```

### <a name="2-uninstall-previous-ctp-2x-packages"></a>2. Удаление предыдущих CTP-версии 2.x пакетов

Удалите на самом низком уровне пакета. Любой прием пакетов вышестоящего источника зависимый от более низкого уровня пакета, автоматически удаляется.

  + Для интеграции Java, удалите **mssql-server расширяемости java**

В следующей таблице, появятся команды для удаления пакетов.

| Платформа  | Выполнение команд удаления пакета | 
|-----------|----------------------------|
| RHEL  | `sudo yum remove msssql-server-extensibility-java` |
| SLES  | `sudo zypper remove msssql-server-extensibility-java` |
| Ubuntu    | `sudo apt-get remove msssql-server-extensibility-java`|

### <a name="3-proceed-with-ctp-30-install"></a>3. Продолжить установку CTP 3.0

Установите на самом высоком уровне пакета, с помощью инструкций в этой статье для вашей операционной системы.

Для каждого набора определенных Операционных систем инструкции по установке *наивысший уровень пакета* либо **пример 1 — Полная установка** для полного набора пакетов, или **пример 2 - минимальную установку**  содержащий наименьшее число пакеты, необходимые для установки соединения.

1. Выполните команды установки с помощью диспетчеров пакетов и синтаксис для дистрибутива Linux. 

   + [RedHat](#RHEL)
   + [Ubuntu](#ubuntu)
   + [SUSE](#suse)

## <a name="prerequisites"></a>предварительные требования

+ Версии Linux должны быть [поддерживается в SQL Server](sql-server-linux-release-notes-2019.md#supported-platforms), но не включает подсистему Docker. Поддерживаемые версии:

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [SUSE Enterprise Linux Server](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ Следует получить средство для выполнения команд T-SQL. Редактор запросов необходим для настройки после установки и проверки. Мы рекомендуем [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download?view=sql-server-2017#get-azure-data-studio-for-linux), бесплатно и под управлением Linux.

## <a name="package-list"></a>Список пакетов

На устройстве, подключенном к Интернету пакеты загружаются и устанавливаются независимо от ядра базы данных, с помощью пакета установщика для каждой операционной системы. В следующей таблице описаны все доступные пакеты.

| Имя пакета | Применяется к | Описание |
|--------------|----------|-------------|
|mssql-server-extensibility  | Все языки | Инфраструктура расширяемости, используемый для выполнения кода Java. |
|MSSQL-server расширяемости java | Java | Расширение Java для загрузки среда выполнения Java. Отсутствуют дополнительные библиотеки или пакеты для Java. |

<a name="RHEL"></a>

## <a name="install-language-extensions"></a>Установка расширения языка

Можно установить расширения языка и Java в Linux, установив **mssql-server расширяемости java**. При установке **mssql-server расширяемости java**, пакет автоматически устанавливает JRE 8, если они еще не установлены. Он также добавляется путь виртуальной машины Java для переменной среды с именем переменная.

> [!Note]
> На сервере, подключенном к Интернету зависимости пакетов загружаются и устанавливаются как часть установки главного пакета. Если сервер не подключен к Интернету, см. в разделе более подробно в [установки в автономном режиме](#offline-install).

### <a name="redhat-install-command"></a>Команда установки RedHat

Можно установить расширения языка для Java в RedHat, используя приведенную ниже команду.

> [!Tip]
> По возможности запустите `yum clean all` обновление пакетов в системе до установки.

```bash
# Install as root or sudo
sudo yum install mssql-server-extensibility-java
```

<a name="ubuntu"></a>

### <a name="ubuntu-install-command"></a>Команда установки Ubuntu

Расширения языка для Java можно установить на базе Ubuntu с помощью следующей команды.

> [!Tip]
> По возможности запустите `apt-get update` обновление пакетов в системе до установки. Кроме того некоторые образы docker в Ubuntu. не может быть возможность apt транспорта https. Чтобы установить его, используйте `apt-get install apt-transport-https`.

```bash
# Install as root or sudo
sudo apt-get install mssql-server-extensibility-java
```

<a name="suse"></a>

### <a name="suse-install-command"></a>Команда установки SUSE

Расширения языка для Java можно установить на SUSE с помощью следующей команды.

```bash
# Install as root or sudo
sudo zypper install mssql-server-extensibility-java
```

## <a name="post-install-config-required"></a>После установки конфигурации (обязательно)

1. GRANT, предоставление разрешений на платформе Linux

    Не нужно выполнять этот шаг, если вы используете внешние библиотеки. Рекомендуемый способ работы использует внешние библиотеки. Дополнительные сведения о создании внешней библиотеки из JAR-файл, см. в разделе [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)

    Если вы не используете внешние библиотеки, необходимо предоставить разрешения на выполнение классов Java в JAR-файлу SQL Server.

    Чтобы предоставляют права чтения и выполнения доступ к JAR-файл, выполните следующую **chmod** команду JAR-файл. Мы рекомендуем всегда помещения файлов класса в JAR-файл, при работе с SQL Server. Дополнительные сведения о создании JAR-файл, см. в разделе [Создание JAR-файл](https://docs.microsoft.com/sql/language-extensions/how-to/create-a-java-jar-file-from-class-files).

    ```cmd
    chmod ug+rx <MyJarFile.jar>
    ```

    Необходимо также предоставить разрешения mssql_satellite JAR-файл для чтения и выполнения.

    ```cmd
    chown mssql_satellite:mssql_satellite <MyJarFile.jar>
    ```

    Дополнительная настройка не главным образом посредством [средство mssql-conf](sql-server-linux-configure-mssql-conf.md).

2. Добавьте учетную запись пользователя mssql, используемой для запуска службы SQL Server. Это необходимо, если настройка еще не запущен ранее.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

3. Разрешите исходящий сетевой доступ. Исходящий сетевой доступ отключен по умолчанию. Чтобы включить исходящие запросы, задайте «outboundnetworkaccess» логическое свойство, используя средство mssql-conf. Дополнительные сведения см. в разделе [Настройка SQL Server в Linux с помощью mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-outbound-access).

   ```bash
   # Run as SUDO or root
   # Enable outbound requests over the network
   sudo /opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 1
   ```

4. Перезапустите службу панели запуска SQL Server и экземпляра компонента database engine для чтения обновленные значения из INI-файл. Сообщение перезапуска, напоминающее каждый раз, когда изменяется параметр относящиеся к расширяемости.  

   ```bash
   systemctl restart mssql-launchpadd

   systemctl restart mssql-server.service
   ```

5. Включить выполнение внешних скриптов, с помощью Azure Data Studio или другого средства, например SQL Server Management Studio (только Windows), которое будет выполняться Transact-SQL.

   ```bash
   EXEC sp_configure 'external scripts enabled', 1
   RECONFIGURE WITH OVERRIDE
   ```

6. Перезапустите `mssql-launchpadd` службы снова.

7. Для каждой базы данных, необходимо использовать расширения языка в, необходимо зарегистрировать внешний язык [создать внешний язык](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql).

## <a name="verify-installation"></a>Проверка установки

Функция интеграции Java не поддерживает библиотеки, но можно запускать `grep -r JRE_HOME /etc` чтобы подтвердить создание переменной среды JAVA_HOME.

Проверка установки, запустите сценарий T-SQL, выполняющий систему хранимую процедуру, вызове Java. Вам потребуется средство запроса для выполнения этой задачи. Azure Data Studio является хорошим выбором. Другие часто используемые средства, такие как SQL Server Management Studio или PowerShell, доступные только для Windows. Если у вас есть компьютер Windows с помощью этих средств, используйте его для подключения к Linux установке компонента database engine.

<a name="install-all"></a>

## <a name="full-install-of-sql-server-and-language-extensions"></a>Полная установка SQL Server и расширения языка

Можно установить и настроить компонент database engine и расширения языка в одну процедуру путем добавления пакетов Java и параметров в команду, которая устанавливает ядро СУБД.

1. Укажите командную строку, которая включает в себя компонент database engine, а также возможности расширения языка.

  Вы можете добавить расширения к ядру СУБД установить Java.

  ```bash
  sudo yum install -y mssql-server mssql-server-extensibility-java 
  ```

3. Принятие условий лицензионного соглашения и выполнить настройку после установки. Используйте **mssql-conf** средство для выполнения этой задачи.

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

  Вам будет предложено принять лицензионное соглашение для компонента database engine, выберите выпуск и задание пароля администратора. 

4. Перезапустите службу, если будет предложено сделать это.

  ```bash
  sudo systemctl restart mssql-server.service
  ```

## <a name="unattended-installation"></a>Автоматическая установка

С помощью [автоматическая установка](https://docs.microsoft.com/sql/linux/sql-server-linux-setup#unattended) для компонента Database Engine, добавьте пакеты для mssql-server расширяемости java.

<a name="offline-install"></a>


## <a name="offline-installation"></a>Автономная установка

Выполните [автономной установки](sql-server-linux-setup.md#offline) инструкции пошаговые инструкции по установке пакетов. Найти сайт загрузки и загрузите определенных пакетов, с помощью списка пакетов.

> [!Tip]
> Некоторые средства управления, пакет предоставляет команды, которые помогут вам определить зависимости пакетов. Yum, используйте `sudo yum deplist [package]`. Для Ubuntu используйте `sudo apt-get install --reinstall --download-only [package name]` следуют `dpkg -I [package name].deb`.

#### <a name="download-site"></a>Сайт загрузки

Вы можете скачать пакеты из [ https://packages.microsoft.com/ ](https://packages.microsoft.com/). Все пакеты для Java, являющийся пакет ядра СУБД. 

#### <a name="redhat7-paths"></a>Пути RedHat/7

|||
|--|----|
| mssql/extensibility-java packages | [https://packages.microsoft.com/rhel/7/mssql-server-preview/](https://packages.microsoft.com/rhel/7/mssql-server-preview/) |

#### <a name="ubuntu1604-paths"></a>Ubuntu-16.04 пути

|||
|--|----|
| mssql/extensibility-java packages | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/) |

#### <a name="suse12-paths"></a>SUSE/12 путей

|||
|--|----|
| mssql/extensibility-java packages | [https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |

#### <a name="package-list"></a>Список пакетов

В зависимости от того, какие расширения, вы хотите использовать, загружать пакеты, необходимые для конкретного языка. Точные имена файлов включают сведения о платформе в суффиксе, но ниже имена файлов должно быть достаточно близко для того, можно определить, какие файлы следует получить.

```
# Core packages 
mssql-server-15.0.1000
mssql-server-extensibility-15.0.1000

# Java
mssql-server-extensibility-java-15.0.1000
```

## <a name="limitations-in-ctp-releases"></a>Ограничения в выпусках CTP

Расширяемость расширений языка и Java в Linux сейчас по-прежнему активно разрабатывается. Следующие функции еще не включены в предварительной версии.

+ Неявная проверка подлинности в данный момент доступна не на платформе Linux в настоящее время, это означает, что не удается подключиться к серверу из выполняющихся Java для доступа к данным или другим ресурсам.


### <a name="resource-governance"></a>Управление ресурсами

Имеется соответствие между Linux и Windows для [ресурсами](../t-sql/statements/create-external-resource-pool-transact-sql.md) для внешних пулов ресурсов, но статистику для [sys.dm_resource_governor_external_resource_pools](../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) установлена единиц в Linux. В следующей CTP-версии единиц выравнивания.
 
| Имя столбца   | Описание | Значение в Linux | 
|---------------|--------------|---------------|
|peak_memory_kb | Максимальный объем памяти, используемой для пула ресурсов. | В Linux этот статистический показатель происходит из CGroups подсистемы памяти, где значение — memory.max_usage_in_bytes |
|write_io_count | Общая сумма записи операций с момента сброса статистики регулятора ресурсов ввода. | В Linux этот статистический показатель происходит из подсистемы blkio CGroups, где значение в строке записи — blkio.throttle.io_serviced | 
|read_io_count | Общее чтение операций с момента сброса статистики регулятора ресурсов ввода. | В Linux этот статистический показатель происходит из подсистемы blkio CGroups, в которых в строке чтения является blkio.throttle.io_serviced | 
|total_cpu_kernel_ms | Совокупное пользователя ядра время ЦП в миллисекундах с момента сброса статистики регулятора ресурсов. | В Linux этот статистический показатель происходит из подсистемы cpuacct CGroups, в которых в строке пользователя является cpuacct.stat |  
|total_cpu_user_ms | Совокупное время пользователя ЦП в миллисекундах с момента сброса статистики регулятора ресурсов.| В Linux этот статистический показатель происходит из подсистемы cpuacct CGroups, где значение на системное значение строки равно cpuacct.stat | 
|active_processes_count | Количество внешних процессов, запущенных в данный момент запроса.| В Linux этот статистический показатель происходит из подсистемы идентификаторов процесса GGroups, где значение — pids.current | 

## <a name="next-steps"></a>Следующие шаги

Разработчики Java можно приступить к работе с простыми примерами и ознакомиться с основами как Java работает с SQL Server. Следующий шаг см. следующие ссылки:

+ [Учебник. Регулярные выражения с помощью Java](../language-extensions/tutorials/search-for-string-using-regular-expressions-in-java.md)