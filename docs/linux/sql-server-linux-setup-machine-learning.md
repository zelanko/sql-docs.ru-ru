---
title: Установка SQL Server службы машинного обучения (R, Python, Java) на платформе Linux | Документация Майкрософт
description: В этой статье описывается установка SQL Server служб машинного обучения (R, Python, Java) на Ubuntu и Red Hat.
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 5d10e6646d83d90af60aa748a8265a069d961443
ms.sourcegitcommit: c3e233c13ebb6fbee60723590179da00802c3f3a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2018
ms.locfileid: "47058933"
---
# <a name="install-sql-server-2019-machine-learning-services-r-python-java-on-linux"></a>Установка SQL Server 2019 службы машинного обучения (R, Python, Java) на платформе Linux

[Службы машинного обучения SQL Server](../advanced-analytics/what-is-sql-server-machine-learning.md) работает в операционных системах Linux, начиная с этого выпуска предварительной версии SQL Server 2019. Выполните действия, описанные в этой статье, чтобы установить расширение программирования Java или машинного обучения расширений R и Python. 

Машинного обучения и программирование расширения являются надстройку к компоненту database engine. Несмотря на то, что вы можете [одновременно установить компонент database engine и служб машинного обучения](#install-all), это лучший способ сначала установите и настройте компонент SQL Server database engine, устранить все проблемы перед добавлением сведения компоненты. 

Расположение пакета расширений R, Python и Java доступны в репозитории исходного SQL Server Linux. Если вы уже настроили установить репозитории источника для компонента database engine, можно выполнить mssql-mlservices команды установки пакета, используя регистрацию репозитория.

## <a name="prerequisites"></a>предварительные требования

+ Операционная система Linux должна быть [поддерживается SQL Server](sql-server-linux-release-notes-2019.md#supported-platforms), работающей в локальной среде или в контейнере Docker.

+ Экземпляр ядра СУБД SQL Server 2019 г. необходимо иметь на: 

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [SUSE Enterprise Linux Server](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ Для R, [Microsoft R Open](#mro) для пакетов R mssql mlsservices. 

<a name="mro"></a>

### <a name="microsoft-r-open-mro"></a>Microsoft R Open (MRO)

Базовое распределение R корпорации Майкрософт является необходимым условием для работы с помощью RevoScaleR, MicrosoftML и других пакетов R, установленных с помощью служб машинного обучения.

Следующие команды зарегистрировать репозиторий, предоставляя MRO. После регистрации, команды для установки других пакетов R автоматически включит MRO как зависимость пакета.

#### <a name="on-ubuntu"></a>В Ubuntu

```bash
# Set the location of the package repo the "prod" directory containing the distribution.
# This example specifies 16.04. Replace with 18.04 if you want that version
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the repo
dpkg -i packages-microsoft-prod.deb
```

#### <a name="on-rhel"></a>В RHEL

```bash
# Set the location of the package repo at the "prod" directory
rpm -Uvh https://packages.microsoft.com/config/rhel/7/packages-microsoft-prod.rpm
```
#### <a name="on-suse"></a>В SUSE

```bash
# Set the location of the package repo
zypper ar -f https://packages.microsoft.com/sles/12/prod packages-microsoft-com
```

## <a name="package-list"></a>Список пакетов

На устройстве, подключенном к Интернету пакеты загружаются и устанавливаются независимо от ядра базы данных, с помощью пакета установщика для каждой операционной системы. В следующей таблице описаны все доступные пакеты, но для установки, подключенной к Интернету, вам нужно только *один* R или Python пакет, чтобы получить определенное сочетание функций.

| Имя пакета | Применяется к | Описание |
|--------------|----------|-------------|
|MSSQL-server расширяемость  | All | Инфраструктура расширяемости, используемые для запуска кода R, Python или Java. |
|MSSQL-server расширяемости java | Java | Расширение Java для загрузки среда выполнения Java. Отсутствуют дополнительные библиотеки или пакеты для Java. |
| Microsoft openmpi  | Python, R | Интерфейс, используемый библиотеками Revo * для параллелизации на платформе Linux передачи сообщений. |
| Microsoft r open — | Чтение | Распределение открытым исходным кодом R. |
| MSSQL-mlservices-python | Python | Распределение открытым исходным кодом Anaconda и Python. |
|MSSQL-mlservices-mlm-py  | Python | Полная установка. Предоставляет revoscalepy, microsoftml, предварительно обученных моделей для анализа тональности образа Добавление признаков и текст.| 
|MSSQL-mlservices-mml-py  | Python | Частичной установки. Предоставляет revoscalepy, microsoftml. <br/>Исключает предварительно обученных моделей. | 
|MSSQL-mlservices пакеты py  | Python | Частичной установки. Предоставляет revoscalepy. <br/>Исключает предварительно обученных моделей и microsoftml. | 
|MSSQL-mlservices-mlm-r  | Чтение | Полная установка. Предоставляет RevoScaleR, MicrosoftML, sqlRUtils, olapR, предварительно обученных моделей для анализа тональности образа Добавление признаков и текст.| 
|MSSQL-mlservices-mml-r  | Чтение | Частичной установки. Предоставляет RevoScaleR, MicrosoftML, sqlRUtils, olapR. <br/>Исключает предварительно обученных моделей.  |
|MSSQL-mlservices пакеты r  | Чтение | Частичной установки. Предоставляет RevoScaleR, sqlRUtils, olapR. <br/>Исключает предварительно обученных моделей и MicrosoftML. | 

<a name="RHEL"></a>

## <a name="rhel-commands"></a>Команды RHEL

Устанавливать какие-либо *один* пакет R и другие *один* пакет Python и Java, если вы хотите, чтобы эту возможность. Каждый пакет R и Python включает набор функций. Выберите пакет, который предоставляет набор функций, которые вам нужны. Зависимые пакеты включаются автоматически.

> [!Tip]
> По возможности запустите `yum clean all` обновление пакетов в системе до установки.

### <a name="example-1----full-installation"></a>Пример 1 - Полная установка 

Включает в себя открытым исходным кодом R и Python, extensibility framework, microsoft-openmpi расширения (R, Python, Java), с помощью библиотеки машинного обучения и предварительно обученных моделей R и Python. R и Python, что-то между полной и Минимальная установка - например библиотеки машинного обучения, но без предварительно обученных моделей - замените `mssql-mlservices-mml-r-9.4.5*` и `mssql-mlservices-mml-py-9.4.5*` вместо этого.

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# Be sure to include -9.4.5* in mlsservices package names
sudo yum install mssql-mlservices-mlm-py-9.4.5*
sudo yum install mssql-mlservices-mlm-r-9.4.5* 
sudo yum install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Пример 2 - Установка минимум 

Включает в себя R и Python, extensibility framework, microsoft-openmpi core Revo * библиотек с открытым кодом R и Python, Java расширения. Исключает предварительно обученных моделей и библиотеки машинного обучения для R и Python. 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java extensions
# Be sure to include -9.4.5* in mlsservices package names
sudo yum install mssql-mlservices-packages-py-9.4.5*
sudo yum install mssql-mlservices-packages-r-9.4.5*
sudo yum install mssql-server-extensibility-java
```

<a name="ubuntu"></a>

## <a name="ubuntu-commands"></a>Команды для Ubuntu

Устанавливать какие-либо *один* пакет R и другие *один* пакет Python и Java, если вы хотите, чтобы эту возможность. Каждый пакет R и Python включает набор функций. Выберите пакет, который предоставляет набор функций, которые вам нужны. Зависимые пакеты включаются автоматически.

> [!Tip]
> По возможности запустите `apt-get update` обновление пакетов в системе до установки. Кроме того некоторые образы docker в Ubuntu. не может быть возможность apt транспорта https. Чтобы установить его, используйте `apt-get install apt-transport-https`.

### <a name="prerequisite-for-1804"></a>Необходимым условием для 18.04

Для запуска mssql-mlservices библиотеки R на Ubuntu 18.04 должны **libpng12** из ядра Linux архивов. Этот пакет больше не включается в стандартную поставку и должен быть установлен вручную. Чтобы получить эту библиотеку, выполните следующие команды:

```bash
wget https://mirrors.kernel.org/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.54-1ubuntu1_amd64.deb
dpkg -i libpng12-01_1.2.54-1ubuntu1_amd64.deb
```

### <a name="example-1----full-installation"></a>Пример 1 - Полная установка 

Включает в себя открытым исходным кодом R и Python, extensibility framework, microsoft-openmpi расширения (R, Python, Java), с помощью библиотеки машинного обучения и предварительно обученных моделей R и Python. Для R и Python, если требуется что-то между полной установки и минимум установить - например библиотеки машинного обучения, но без предварительно обученных моделей - замените mssql-mlservices-mml-r и mssql-mlservices-mml-py вместо этого.

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# There is no asterisk in this full install
sudo apt-get install mssql-mlservices-mlm-py 
sudo apt-get install mssql-mlservices-mlm-r 
sudo apt-get install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Пример 2 - Установка минимум 

Включает в себя R и Python, extensibility framework, microsoft-openmpi core Revo * библиотек с открытым кодом R и Python, Java расширения. Исключает предварительно обученных моделей и библиотеки машинного обучения для R и Python. 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java
# No aasterisk
sudo apt-get install mssql-mlservices-packages-py
sudo apt-get install mssql-mlservices-packages-r
sudo apt-get install mssql-server-extensibility-java
```

<a name="suse"></a>

## <a name="suse-commands"></a>Команды SUSE

Устанавливать какие-либо *один* пакет R и другие *один* пакет Python и Java, если вы хотите, чтобы эту возможность. Каждый пакет R и Python включает набор функций. Выберите пакет, который предоставляет набор функций, которые вам нужны. Зависимые пакеты включаются автоматически. 

### <a name="example-1----full-installation"></a>Пример 1 - Полная установка 

Включает в себя открытым исходным кодом R и Python, extensibility framework, microsoft-openmpi расширения (R, Python, Java), с помощью библиотеки машинного обучения и предварительно обученных моделей R и Python. R и Python, что-то между полной и Минимальная установка - например библиотеки машинного обучения, но без предварительно обученных моделей - замените `mssql-mlservices-mml-r-9.4.5*` и `mssql-mlservices-mml-py-9.4.5*` вместо этого.

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# Be sure to include -9.4.5* in mlsservices package names
sudo zypper install mssql-mlservices-mlm-py-9.4.5*
sudo zypper install mssql-mlservices-mlm-r-9.4.5* 
sudo zypper install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>Пример 2 - Установка минимум 

Включает в себя R и Python, extensibility framework, microsoft-openmpi core Revo * библиотек с открытым кодом R и Python, Java расширения. Исключает предварительно обученных моделей и библиотеки машинного обучения для R и Python. 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java extensions
# Be sure to include -9.4.5* in mlsservices package names
sudo zypper install mssql-mlservices-packages-py-9.4.5*
sudo zypper install mssql-mlservices-packages-r-9.4.5*
sudo zypper install mssql-server-extensibility-java
```

## <a name="post-install-config-required"></a>После установки конфигурации (обязательно)

Дополнительная настройка не главным образом посредством [средство mssql-conf](sql-server-linux-configure-mssql-conf.md).


1. Добавьте учетную запись пользователя mssql, используемой для запуска службы панели запуска SQL Server.

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

2. Примите лицензионные соглашения для открытым исходным кодом R и Python. Это можно осуществить несколькими способами. Если вы ранее принят лицензирования SQL Server и теперь при добавлении расширения R или Python, следующая команда является ваше согласие на свои условия:

  ```bash
  # Run as SUDO or root
  # Use set + EULA 
    sudo /opt/mssql/bin/mssql-conf set EULA accepteulaml Y
  ```

  Альтернативный рабочий процесс представляет, что если вы еще не приняли компонент SQL Server database engine, лицензионное соглашение, программа установки обнаруживает mssql-mlservices пакеты и запросы для принятия лицензионного соглашения при `mssql-conf setup` выполняется. Дополнительные сведения о параметрах лицензионное соглашение, см. в разделе [SQL Server можно настроить с помощью средства mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-eula).

3. Перезапустите службу панели запуска SQL Server и экземпляра компонента database engine.

  ```bash
  systemctl restart mssql-launchpadd

  systemctl restart mssql-server.service
  ```

4. Включите выполнение внешних скриптов в SQL Server Management Studio или другой инструмент, который выполняется Transact-SQL. 

  ```bash
  EXEC sp_configure 'external scripts enabled', 1 
  RECONFIGURE WITH OVERRIDE 
  ```

## <a name="verify-installation"></a>Проверка установки

Библиотеки R (MicrosoftML RevoScaleR и другим пользователям) можно найти в `/opt/mssql/mlservices/libraries/RServer`.

Библиотеки Python (microsoftml и revoscalepy) можно найти в `/opt/mssql/mlservices/libraries/PythonServer`.

С помощью инструмента запросов SQL Server, выполните следующую команду SQL, чтобы проверить выполнение R в SQL Server. Если сценарий не выполняется, попробуйте выполнить перезапуск службы, `sudo systemctl restart mssql-server`.

```r
EXEC sp_execute_external_script   
@language =N'R', 
@script=N' 
OutputDataSet <- InputDataSet', 
@input_data_1 =N'SELECT 1 AS hello' 
WITH RESULT SETS (([hello] int not null)); 
GO 
```
 
Выполните следующую команду SQL для проверки выполнения Python в SQL Server. 
 
```python
EXEC sp_execute_external_script  
@language =N'Python', 
@script=N' 
OutputDataSet = InputDataSet; 
', 
@input_data_1 =N'SELECT 1 AS hello' 
WITH RESULT SETS (([hello] int not null)); 
GO 
```

<a name="install-all"></a>

## <a name="chained-installation"></a>Сцепленных

Можно установить и настроить компонент database engine и служб машинного обучения в одну процедуру путем добавления пакетов R, Python или Java и параметров в команду, которая устанавливает ядро СУБД. 

Следующий пример — является «template» иллюстрацией того, как с помощью диспетчера пакетов Yum выглядит объединенный пакет установки:

```bash
sudo yum install -y mssql-sqlserver mssql-server-extensibility-java 
```

В примере устанавливает ядро СУБД и добавляет расширения языка Java, запрашивающий extensibility framework пакет как зависимость. Все пакеты, используемые в этом примере находятся по тому же пути. Если вы добавили пакеты R, регистрация для репозитория пакетов microsoft r open — не требуются.

После установки, не забудьте использовать средство mssql-conf для настройки установки в целом и принять лицензионные соглашения. Неподдерживаемого лицензионные соглашения для компонентов R и Python с открытым кодом, определяются автоматически, и вам будет предложено согласны с ними, а также условия лицензионного соглашения для SQL Server.

```bash
sudo /opt/mssql/bin/mssql-conf setup MSSQL_PID=Developer 
```

## <a name="unattended-installation"></a>Автоматическая установка

С помощью [автоматическая установка](https://docs.microsoft.com/sql/linux/sql-server-linux-setup?view=sql-server-2017#unattended) для компонента Database Engine, добавить пакеты для mssql mlservices и лицензионные соглашения.

Вспомним, что программа установки или средство mssql-conf запросит принять условия лицензионного соглашения. Если вы уже настроен компонент SQL Server database engine и принятия его лицензионного соглашения, используйте один из параметров лицензионное соглашение mlservices для открытым исходным кодом R и Python.

```bash
sudo /opt/mssql/bin/mssql-conf setup accept-eula-ml
```

Все возможные перестановки принятия лицензионного соглашения документированы в [Настройка SQL Server в Linux с использованием средство mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-eula).

## <a name="offline-installation"></a>Автономная установка

Выполните [автономной установки](sql-server-linux-setup.md#offline) инструкции пошаговые инструкции по установке пакетов. Найти сайт загрузки и загрузите определенных пакетов, с помощью списка пакетов.

> [!Tip]
> Некоторые средства управления, пакет предоставляет команды, которые помогут вам определить зависимости пакетов. Yum, используйте `sudo yum deplist [package]`. Для Ubuntu используйте `sudo apt-get install --reinstall --download-only [package name]` следуют `dpkg -I [package name].deb`.


#### <a name="download-site"></a>Сайт загрузки

Вы можете скачать пакеты из [ https://packages.microsoft.com/ ](https://packages.microsoft.com/). Все пакеты R, Python и Java mlservices размещены совместно с пакет ядра СУБД. Базовые версии для пакетов mlservices — 9.4.5. Micrososoft-r-open пакеты находятся в другую папку.

#### <a name="rhel7-paths"></a>Пути RHEL/7

|||
|--|----|
| MSSQL/mlservices пакетов | [https://packages.microsoft.com/rhel/7/mssql-server-preview/](https://packages.microsoft.com/rhel/7/mssql-server-preview/) |
| Microsoft r-open пакетов | [https://packages.microsoft.com/rhel/7/prod/](https://packages.microsoft.com/rhel/7/prod/) | 


#### <a name="ubuntu1604-paths"></a>Ubuntu-16.04 пути

|||
|--|----|
| MSSQL/mlservices пакетов | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/) |
| Microsoft r-open пакетов | [https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/) | 

#### <a name="sles12-paths"></a>SLES/12 путей

|||
|--|----|
| MSSQL/mlservices пакетов | [ https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |
| Microsoft r-open пакетов | [https://packages.microsoft.com/sles/12/prod/](https://packages.microsoft.com/sles/12/prod/) | 

#### <a name="package-list"></a>Список пакетов

В зависимости от того, какие расширения, вы хотите использовать, загружать пакеты, необходимые для конкретного языка. Точные имена файлов включают сведения о платформе, но ниже имена файлов должно быть достаточно близко для того, можно определить, какие файлы следует получить.

```
# Core packages 
mssql-server-15.0.1000
mssql-server-extensibility-15.0.1000

# Java
mssql-server-extensibility-java-15.0.1000

# R
microsoft-openmpi-3.0.0
microsoft-r-open-foreachiterators-3.4.4
microsoft-r-open-mkl-3.4.4
microsoft-r-open-mro-3.4.4
mssql-mlservices-packages-r-9.4.5
mssql-mlservices-mlm-r-9.4.5
mssql-mlservices-mml-r-9.4.5

# Python
microsoft-openmpi-3.0.0
mssql-mlservices-python-9.4.5
mssql-mlservices-packages-py-9.4.5
mssql-mlservices-mlm-py-9.4.5
mssql-mlservices-mml-py-9.4.5 
```

## <a name="add-more-rpython-packages"></a>Добавить дополнительные пакеты R и Python 
 
Можно установить другие пакеты R и Python и использовать их в скрипт, выполняемый на SQL Server 2019.

### <a name="r-packages"></a>Пакеты R 
 
1. Запустите сеанс R.

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R 
   ```

2. Установить пакет R вызывается [связующий](https://mran.microsoft.com/package/glue) для проверки установки пакета.

   ```r
   # install.packages("glue",lib="/opt/mssql/mlservices/libraries/RServer") 
   ```
   Кроме того можно установить пакет R из командной строки 

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R CMD INSTALL -l /opt/mssql/mlservices/libraries/RServer glue_1.1.1.tar.gz 
   ```

3. Импорт пакета R в [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

   ```r
   EXEC sp_execute_external_script  
   @language = N'R', 
   @script = N'library(glue)' 
   ```

### <a name="python-packages"></a>Пакеты Python 
 
1. Установить пакет Python [httpie](https://httpie.org/) с помощью pip. 

   ```python
   # sudo /opt/mssql/mlservices/bin/python/python -m pip install httpie 
   ``` 

2. Импорт пакета Python в [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
 
   ```python
   EXEC sp_execute_external_script  
   @language = N'Python',  
   @script = N'import httpie' 
   ```

## <a name="limitations-in-ctp-20"></a>Ограничения в CTP-версии 2.0

В этой CTP-версии существуют следующие ограничения.

+ Неявная проверка подлинности доступна в настоящее время не в службах машинного обучения на платформе Linux в настоящее время, это означает, что не удается подключиться к серверу из сценария R или Python выполняется для доступа к данным или другим ресурсам. 

+ [CREATE EXTERNAL LIBRARY](../t-sql/statements/create-external-library-transact-sql.md) (для хранения пакетов R в базе данных), в настоящее время недоступна в Linux и не поддерживает Python.  

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

Разработчики R можно приступить к работе с простыми примерами и ознакомиться с основами как R работает с SQL Server. Следующий шаг см. следующие ссылки:

+ [Руководство: Запуск R в T-SQL](../advanced-analytics/tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Учебник: Анализ в базе данных для разработчиков R](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

Разработчики Python рассказывается, как использовать Python с SQL Server с помощью этих учебных материалов:

+ [Руководство: Запуск Python в T-SQL](../advanced-analytics/tutorials/run-python-using-t-sql.md)
+ [Учебник: Анализ в базе данных для разработчиков Python](../advanced-analytics/tutorials/sqldev-in-database-python-for-sql-developers.md)

Чтобы просмотреть примеры машинного обучения, которые основаны на реальных сценариев, см. в разделе [машинного обучения учебники](../advanced-analytics/tutorials/machine-learning-services-tutorials.md).
