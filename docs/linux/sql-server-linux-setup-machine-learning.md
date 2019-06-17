---
title: Установка SQL Server службы машинного обучения (R, Python) на платформе Linux | Документация Майкрософт
description: Сведения об установке SQL Server служб машинного обучения (R, Python) в Red Hat, Ubuntu и SUSE.
author: dphansen
ms.author: davidph
manager: cgronlun
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a64addb1d9267aadc7e7eb2828e032d67db5d540
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705097"
---
# <a name="install-sql-server-2019-machine-learning-services-r-python-on-linux"></a>Установка SQL Server 2019 службы машинного обучения (R, Python) на платформе Linux

[Службы машинного обучения SQL Server](../advanced-analytics/what-is-sql-server-machine-learning.md) работает в операционных системах Linux, начиная с этого выпуска предварительной версии SQL Server 2019. Выполните действия, описанные в этой статье, чтобы установить машинного обучения расширений R и Python. 

Машинного обучения и программирование расширения являются надстройку к компоненту database engine. Несмотря на то, что вы можете [одновременно установить компонент database engine и служб машинного обучения](#install-all), это лучший способ сначала установите и настройте компонент SQL Server database engine, устранить все проблемы перед добавлением сведения компоненты. 

Пакет расширений R и Python находится в репозитории исходного SQL Server Linux. Если вы уже настроили репозиториях для установки ядра базы данных, вы можете запустить **mssql mlservices** упаковать команды установки, используя регистрацию репозитория.

Службы машинного обучения также поддерживается в контейнерах Linux. Мы не предоставляем готовые контейнеры со службами машинного обучения, но можно создать один из контейнеров SQL Server, с помощью [пример шаблона доступен на сайте GitHub](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices).

## <a name="uninstall-previous-ctp"></a>Удаление предыдущей CTP-версии

Список пакетов изменилось за последние несколько выпусков CTP, приводит к меньшим числом пакетов. Мы рекомендуем удалить CTP-версии 2.x, чтобы удалить все предыдущие пакеты перед установкой CTP-версии 3.0. Side-by-side установку нескольких версий не поддерживается.

### <a name="1-confirm-package-installation"></a>1. Подтверждение установки пакета

Можно проверить существование из предыдущей установки в качестве первого шага. Указать существующую установку, следующие файлы: checkinstallextensibility.sh, exthost, панели запуска.

```bash
ls /opt/microsoft/mssql/bin
```

### <a name="2-uninstall-previous-ctp-2x-packages"></a>2. Удаление предыдущих CTP-версии 2.x пакетов

Удалите на самом низком уровне пакета. Любой прием пакетов вышестоящего источника зависимый от более низкого уровня пакета, автоматически удаляется.

  + Интеграция R, удалите **microsoft r open —** *
  + Интеграция Python, удалите **mssql-mlservices-python**

В следующей таблице, появятся команды для удаления пакетов.

| Платформа  | Выполнение команд удаления пакета | 
|-----------|----------------------------|
| RHEL  | `sudo yum remove microsoft-r-open-mro-3.4.4`<br/>`sudo yum remove msssql-mlservices-python` |
| SLES  | `sudo zypper remove microsoft-r-open-mro-3.4.4`<br/>`sudo zypper remove msssql-mlservices-python` |
| Ubuntu    | `sudo apt-get remove microsoft-r-open-mro-3.4.4`<br/>`sudo apt-get remove msssql-mlservices-python`|

> [!Note]
> Microsoft R Open 3.4.4 состоит из двух или трех пакетов, в зависимости от того, что CTP-версии был установлен ранее. (Пакет foreachiterators была объединена в пакет основных mro в CTP-версии 2.2.) Если любой из этих пакетов остаются после удаления microsoft-r-open-mro-3.4.4, их следует удалить по отдельности.
> ```
> microsoft-r-open-foreachiterators-3.4.4
> microsoft-r-open-mkl-3.4.4
> microsoft-r-open-mro-3.4.4
> ```

### <a name="3-proceed-with-ctp-30-install"></a>3. Продолжить установку CTP 3.0

Установите на самом высоком уровне пакета, с помощью инструкций в этой статье для вашей операционной системы.

Для каждого набора определенных Операционных систем инструкции по установке *наивысший уровень пакета* либо **пример 1 — Полная установка** для полного набора пакетов, или **пример 2 - минимальную установку**  содержащий наименьшее число пакеты, необходимые для установки соединения.

1. Интеграция с R, начните с [MRO](#mro) , так как он является необходимым условием. Интеграция R не установит его.

2. Выполните команды установки с помощью диспетчеров пакетов и синтаксис для вашей операционной системы: 

   + [RedHat](#RHEL)
   + [Ubuntu](#ubuntu)
   + [SUSE](#suse)

## <a name="prerequisites"></a>предварительные требования

+ Версии Linux должны быть [поддерживается в SQL Server](sql-server-linux-release-notes-2019.md#supported-platforms), но не включает подсистему Docker. Поддерживаемые версии:

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [SUSE Enterprise Linux Server](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ (R) [Microsoft R Open](#mro) предоставляет базовое распределение R для функции R в SQL Server

+ Следует получить средство для выполнения команд T-SQL. Редактор запросов необходим для настройки после установки и проверки. Мы рекомендуем [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download?view=sql-server-2017#get-azure-data-studio-for-linux), бесплатно и под управлением Linux.

<a name="mro"></a>

### <a name="microsoft-r-open-mro-installation"></a>Установка Microsoft R Open (MRO)

Базовое распределение R корпорации Майкрософт является необходимым условием для работы с помощью RevoScaleR, MicrosoftML и других пакетов R, установленных с помощью служб машинного обучения.

Требуемая версия — MRO 3.5.2.

Выберите для установки MRO следующих двух способов:

+ Загрузить MRO tarball MRAN, распаковать его и выполните его сценарий install.sh. Можно выполнить [инструкции по установке на MRAN](https://mran.microsoft.com/releases/3.5.2) Если вы хотите, чтобы этот подход.

+ Кроме того, зарегистрировать **packages.microsoft.com** репозитория, как описано ниже, чтобы установить два пакета, включающего в себя распределение MRO: microsoft-r-open-mro и microsoft-r-open-mkl. 

Следующие команды зарегистрировать репозиторий, предоставляя MRO. После регистрации, команды для установки других пакетов R, например mssql-mlservices-mml-r, автоматически включается MRO как зависимость пакета.

#### <a name="mro-on-ubuntu"></a>MRO в Ubuntu

```bash
# Install as root
sudo su

# Optionally, if your system does not have the https apt transport option
apt-get install apt-transport-https

# Set the location of the package repo the "prod" directory containing the distribution.
# This example specifies 16.04. Replace with 14.04 if you want that version
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the repo
dpkg -i packages-microsoft-prod.deb

# Update packages on your system (required), including MRO installation
sudo apt-get update
```

#### <a name="mro-on-rhel"></a>MRO на RHEL

```bash
# Import the Microsoft repository key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc


# Set the location of the package repo at the "prod" directory
# The following command is for version 7.x
# For 6.x, replace 7 with 6 to get that version
rpm -Uvh https://packages.microsoft.com/config/rhel/7/packages-microsoft-prod.rpm

# Update packages on your system (optional)
yum update
```
#### <a name="mro-on-suse"></a>MRO в SUSE

```bash
# Install as root
sudo su

# Set the location of the package repo at the "prod" directory containing the distribution
# This example is for SLES12, the only supported version of SUSE in Machine Learning Server
zypper ar -f https://packages.microsoft.com/sles/12/prod packages-microsoft-com

# Update packages on your system (optional)
zypper update
```

## <a name="package-list"></a>Список пакетов

На устройстве, подключенном к Интернету пакеты загружаются и устанавливаются независимо от ядра базы данных, с помощью пакета установщика для каждой операционной системы. В следующей таблице описаны все доступные пакеты, но для R и Python, нужно указать пакеты, которые предоставляют возможности установки или установки минимальное компонента.

| Имя пакета | Применяется к | Описание |
|--------------|----------|-------------|
|mssql-server-extensibility  | All | Инфраструктура расширяемости, используемые для запуска кода R и Python. |
| Microsoft openmpi  | Python, R | Интерфейс, используемый библиотеками Revo * для параллелизации на платформе Linux передачи сообщений. |
| mssql-mlservices-python | Python | Распределение открытым исходным кодом Anaconda и Python. |
|mssql-mlservices-mlm-py  | Python | *Полная установка*. Предоставляет revoscalepy, microsoftml, предварительно обученных моделей для анализа тональности образа Добавление признаков и текст.| 
|mssql-mlservices-packages-py  | Python | *Минимальная установка*. Предоставляет revoscalepy и microsoftml. <br/>Исключает предварительно обученных моделей. | 
| [Microsoft-r-открытым *](#mro) | Чтение | Открытый дистрибутив R, состоящий из трех пакетов. |
|mssql-mlservices-mlm-r  | Чтение | *Полная установка*. Предоставляет RevoScaleR, MicrosoftML, sqlRUtils, olapR, предварительно обученных моделей для анализа тональности образа Добавление признаков и текст.| 
|mssql-mlservices-packages-r  | Чтение | *Минимальная установка*. Предоставляет RevoScaleR, sqlRUtils, MicrosoftML, olapR. <br/>Исключает предварительно обученных моделей. | 
|mssql-mlservices-mml-py  | Только CTP 2.0 — 2.1 | Устарело в CTP-версии 2.2, из-за консолидации пакета Python в mssql-mslservices-python. Предоставляет revoscalepy. Исключает предварительно обученных моделей и microsoftml.| 
|mssql-mlservices-mml-r  | Только CTP 2.0 — 2.1 | Устарело в CTP-версии 2.2, из-за консолидации пакета R в mssql-mslservices-python. Предоставляет RevoScaleR, sqlRUtils, olapR. Исключает предварительно обученных моделей и MicrosoftML.  |

<a name="RHEL"></a>

## <a name="redhat-commands"></a>RedHat команды

Можно установить поддержку языка в любой комбинации требуется (один или несколько языков). R и Python существует два пакета на выбор. Один предоставляет все доступные компоненты, обозначаемым *полная установка*. Выбор альтернативного исключает предварительно обученные модели машинного обучения и считается *минимальную установку*.

> [!Tip]
> По возможности запустите `yum clean all` обновление пакетов в системе до установки.

### <a name="example-1----full-installation"></a>Пример 1 - Полная установка 

Включает в себя открытым исходным кодом R и Python, extensibility framework, microsoft-openmpi расширения (R, Python), с помощью библиотеки машинного обучения и предварительно обученных моделей R и Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python)
# Be sure to include -9.4.7* in mlsservices package names
sudo yum install mssql-mlservices-mlm-py-9.4.7*
sudo yum install mssql-mlservices-mlm-r-9.4.7* 
```

### <a name="example-2---minimum-installation"></a>Пример 2 - Установка минимум 

Включает открытым исходным кодом R и Python, инфраструктура расширяемости microsoft openmpi, core Revo * библиотеки и библиотеки машинного обучения для R и Python. Исключает предварительно обученных моделей.

```bash
# Install as root or sudo
# Minimum install of R, Python extensions
# Be sure to include -9.4.6* in mlsservices package names
sudo yum install mssql-mlservices-packages-py-9.4.7*
sudo yum install mssql-mlservices-packages-r-9.4.7*
```

<a name="ubuntu"></a>

## <a name="ubuntu-commands"></a>Команды для Ubuntu

Можно установить поддержку языка в любой комбинации требуется (один или несколько языков). R и Python существует два пакета на выбор. Один предоставляет все доступные компоненты, обозначаемым *полная установка*. Выбор альтернативного исключает предварительно обученные модели машинного обучения и считается *минимальную установку*.

> [!Tip]
> По возможности запустите `apt-get update` обновление пакетов в системе до установки. Кроме того некоторые образы docker в Ubuntu. не может быть возможность apt транспорта https. Чтобы установить его, используйте `apt-get install apt-transport-https`.

### <a name="example-1----full-installation"></a>Пример 1 - Полная установка 

Включает в себя открытым исходным кодом R и Python, extensibility framework, microsoft-openmpi расширения (R, Python), с помощью библиотеки машинного обучения и предварительно обученных моделей R и Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python)
# There is no asterisk in this full install
sudo apt-get install mssql-mlservices-mlm-py 
sudo apt-get install mssql-mlservices-mlm-r 
```

### <a name="example-2---minimum-installation"></a>Пример 2 - Установка минимум 

Включает открытым исходным кодом R и Python, инфраструктура расширяемости microsoft openmpi, core Revo * библиотеки и библиотеки машинного обучения для R и Python. Исключает предварительно обученных моделей. 

```bash
# Install as root or sudo
# Minimum install of R, Python
# No aasterisk
sudo apt-get install mssql-mlservices-packages-py
sudo apt-get install mssql-mlservices-packages-r
```

<a name="suse"></a>

## <a name="suse-commands"></a>Команды SUSE

Можно установить поддержку языка в любой комбинации требуется (один или несколько языков). R и Python существует два пакета на выбор. Один предоставляет все доступные компоненты, обозначаемым *полная установка*. Выбор альтернативного исключает предварительно обученные модели машинного обучения и считается *минимальную установку*.

### <a name="example-1----full-installation"></a>Пример 1 - Полная установка 

Включает в себя открытым исходным кодом R и Python, extensibility framework, microsoft-openmpi расширения (R, Python), с помощью библиотеки машинного обучения и предварительно обученных моделей R и Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python)
# Be sure to include -9.4.7* in mlsservices package names
sudo zypper install mssql-mlservices-mlm-py-9.4.7*
sudo zypper install mssql-mlservices-mlm-r-9.4.7* 
```

### <a name="example-2---minimum-installation"></a>Пример 2 - Установка минимум 

Включает открытым исходным кодом R и Python, инфраструктура расширяемости microsoft openmpi, core Revo * библиотеки и библиотеки машинного обучения для R и Python. Исключает предварительно обученных моделей. 

```bash
# Install as root or sudo
# Minimum install of R, Python extensions
# Be sure to include -9.4.6* in mlsservices package names
sudo zypper install mssql-mlservices-packages-py-9.4.7*
sudo zypper install mssql-mlservices-packages-r-9.4.7*
```

## <a name="post-install-config-required"></a>После установки конфигурации (обязательно)

Дополнительная настройка не главным образом посредством [средство mssql-conf](sql-server-linux-configure-mssql-conf.md).


1. Добавьте учетную запись пользователя mssql, используемой для запуска службы SQL Server. Это необходимо, если настройка еще не запущен ранее.

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

3. Разрешите исходящий сетевой доступ. Исходящий сетевой доступ отключен по умолчанию. Чтобы включить исходящие запросы, задайте «outboundnetworkaccess» логическое свойство, используя средство mssql-conf. Дополнительные сведения см. в разделе [Настройка SQL Server в Linux с помощью mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-outbound-access).

   ```bash
   # Run as SUDO or root
   # Enable outbound requests over the network
   sudo /opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 1
   ```

4. Для R интеграции только, задайте функции **MKL_CBWR** переменную среды, чтобы [гарантировать согласованный результат](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) из вычислений Intel Math Kernel Library (MKL).

   + Измените или создайте файл с именем **.bash_profile** в домашнем каталоге пользователя, добавив строку `export MKL_CBWR="AUTO"` к файлу.

   + Выполните этот файл, введя `source .bash_profile` в командной строке bash.

5. Перезапустите службу панели запуска SQL Server и экземпляра компонента database engine для чтения обновленные значения из INI-файл. Сообщение перезапуска, напоминающее каждый раз, когда изменяется параметр относящиеся к расширяемости.  

   ```bash
   systemctl restart mssql-launchpadd

   systemctl restart mssql-server.service
   ```

6. Включить выполнение внешних скриптов, с помощью Azure Data Studio или другого средства, например SQL Server Management Studio (только Windows), которое будет выполняться Transact-SQL. 

   ```bash
   EXEC sp_configure 'external scripts enabled', 1 
   RECONFIGURE WITH OVERRIDE 
   ```

7. Еще раз перезапустите службу панели запуска.

## <a name="verify-installation"></a>Проверка установки

Библиотеки R (MicrosoftML RevoScaleR и другим пользователям) можно найти в `/opt/mssql/mlservices/libraries/RServer`.

Библиотеки Python (microsoftml и revoscalepy) можно найти в `/opt/mssql/mlservices/libraries/PythonServer`.

Чтобы проверить установку, запустите сценарий T-SQL, который выполняет вызов R или Python системной хранимой процедуры. Вам потребуется средство запроса для выполнения этой задачи. Azure Data Studio является хорошим выбором. Другие часто используемые средства, такие как SQL Server Management Studio или PowerShell, доступные только для Windows. Если у вас есть компьютер Windows с помощью этих средств, используйте его для подключения к Linux установке компонента database engine.

Выполните следующую команду SQL для проверки выполнения R в SQL Server. Если сценарий не выполняется, попробуйте выполнить перезапуск службы, `sudo systemctl restart mssql-server.service`.

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

## <a name="chained-combo-install"></a>Установка цепочки «поле со списком»

Можно установить и настроить компонент database engine и служб машинного обучения в одну процедуру путем добавления пакетов R или Python и параметров в команду, которая устанавливает ядро СУБД. 

1. Интеграция R, установите [Microsoft R Open](#mro) как необходимый компонент. Если вы не устанавливаете службы R, этот шаг можно пропустите.

2. Укажите командную строку, которая включает в себя компонент database engine, а также возможности расширения языка.

  Можно добавить один компонент, таких как Python, установка интеграции для компонента database engine.

  ```bash
  sudo yum install -y mssql-server mssql-mlservices-packages-r-9.4.7* 
  ```

  Или добавьте оба расширения (R, Python).

  ```bash
  sudo yum install -y mssql-server mssql-mlservices-packages-r-9.4.7* mssql-mlservices-packages-py-9.4.7*
  ```

3. Принятие условий лицензионного соглашения и выполнить настройку после установки. Используйте **mssql-conf** средство для выполнения этой задачи.

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

  Вам будет предложено принять лицензионное соглашение для компонента database engine, выберите выпуск и задание пароля администратора. Кроме того, будет предложено принять лицензионное соглашение для служб машинного обучения.

4. Перезапустите службу, если будет предложено сделать это.

  ```bash
  sudo systemctl restart mssql-server.service
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

Вы можете скачать пакеты из [ https://packages.microsoft.com/ ](https://packages.microsoft.com/). Все mlservices пакеты R и Python, являющийся пакет ядра СУБД. 9\.4.5 (для CTP-версии 2.0) является базовой версии для пакетов mlservices 9.4.6 (CTP 2.1 и более поздних версий). Вспомним, что пакеты microsoft r open — находятся в [другого репозитория](#mro).

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
| MSSQL/mlservices пакетов | [https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |
| Microsoft r-open пакетов | [https://packages.microsoft.com/sles/12/prod/](https://packages.microsoft.com/sles/12/prod/) | 

#### <a name="package-list"></a>Список пакетов

В зависимости от того, какие расширения, вы хотите использовать, загружать пакеты, необходимые для конкретного языка. Точные имена файлов включают сведения о платформе в суффиксе, но ниже имена файлов должно быть достаточно близко для того, можно определить, какие файлы следует получить.

```
# Core packages 
mssql-server-15.0.1000
mssql-server-extensibility-15.0.1000

# R
microsoft-openmpi-3.0.0
microsoft-r-open-mkl-3.5.2
microsoft-r-open-mro-3.5.2
mssql-mlservices-packages-r-9.4.7.64
mssql-mlservices-mlm-r-9.4.7.64


# Python
microsoft-openmpi-3.0.0
mssql-mlservices-python-9.4.7.64
mssql-mlservices-packages-py-9.4.7.64
mssql-mlservices-mlm-py-9.4.7.64
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

## <a name="limitations-in-ctp-releases"></a>Ограничения в выпусках CTP

Интеграция R и Python в Linux — по-прежнему в активной разработке. Следующие функции еще не включены в предварительной версии.

+ Неявная проверка подлинности доступна в настоящее время не в службах машинного обучения на платформе Linux в настоящее время, это означает, что не удается подключиться к серверу из сценария R или Python выполняется для доступа к данным или другим ресурсам. 

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

+ [Учебник. Запуск R в T-SQL](../advanced-analytics/tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Учебник. Аналитика в базе данных для разработчиков R](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

Разработчики Python рассказывается, как использовать Python с SQL Server с помощью этих учебных материалов:

+ [Учебник. Запустите Python в T-SQL](../advanced-analytics/tutorials/run-python-using-t-sql.md)
+ [Учебник. Аналитика в базе данных для разработчиков Python](../advanced-analytics/tutorials/sqldev-in-database-python-for-sql-developers.md)

Чтобы просмотреть примеры машинного обучения, которые основаны на реальных сценариев, см. в разделе [машинного обучения учебники](../advanced-analytics/tutorials/machine-learning-services-tutorials.md).
