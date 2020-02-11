---
title: Установка Служб машинного обучения SQL Server (Python, R) в Linux
description: Сведения об установке Служб машинного обучения SQL Server (Python, R) в Linux Red Hat, Ubuntu и SUSE.
author: dphansen
ms.author: davidph
ms.reviewer: vanto
manager: cgronlun
ms.date: 02/03/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 71ab699e99a3d22b6b04299b8de1ccb18e5f0708
ms.sourcegitcommit: 1b0906979db5a276b222f86ea6fdbe638e6c9719
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2020
ms.locfileid: "76971377"
---
# <a name="install-sql-server-machine-learning-services-python-and-r-on-linux"></a>Установка Служб машинного обучения SQL Server (Python, R) в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье объясняется, как установить [Службы машинного обучения SQL Server](../advanced-analytics/index.yml) в Linux. Службы машинного обучения можно использовать для запуска сценариев R или Python в базе данных.

Поддерживаются следующие дистрибутивы Linux:

- Red Hat Enterprise Linux (RHEL)
- SUSE Linux Enterprise Server (SLES)
- Ubuntu

Службы машинного обучения являются надстройкой ядра СУБД. Хотя [ядро СУБД и Службы машинного обучения можно установить одновременно](#install-all), рекомендуется сначала установить и настроить ядро СУБД SQL Server, чтобы устранить все неполадки, прежде чем добавлять дополнительные компоненты. 

Пакет расширений Python и R находится в репозиториях исходного кода SQL Server для Linux. Если вы уже настроили репозитории исходного кода для ядра СУБД, команды установки пакета **mssql-mlservices** можно выполнить, используя ту же регистрацию репозиториев.

Службы машинного обучения также поддерживаются в контейнерах Linux. Мы не предоставляем готовые контейнеры со Службами машинного обучения, однако вы можете создать такой контейнер для SQL Server, используя [шаблон, доступный в GitHub](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices).

Службы машинного обучения устанавливаются по умолчанию в кластерах больших данных SQL Server, и вам не нужно в этом случае выполнять шаги. Дополнительные сведения см. в разделе [Использование служб машинного обучения (Python и R) в кластерах больших данных](../big-data-cluster/machine-learning-services.md).

## <a name="uninstall-preview-release"></a>Удаление предварительной версии

Если вы установили предварительную версию (CTP-версию или версию-кандидат), рекомендуется удалить эту версию для удаления всех предыдущих пакетов перед установкой SQL Server 2019. Параллельная установка нескольких версий не поддерживается, и список пакетов был изменен после выхода последних предварительных версий (CTP/RC).

### <a name="1-confirm-package-installation"></a>1. Подтверждение установки пакета

В качестве первого шага вам может потребоваться проверить наличие предыдущей установки. Следующие файлы указывают на существующую установку: checkinstallextensibility.sh, exthost, launchpad.

```bash
ls /opt/microsoft/mssql/bin
```

### <a name="2-uninstall-ctprc-packages"></a>2. Удаление пакетов CTP/RC

Выполняйте удаление на самом низком уровне пакета. Любой вышестоящий пакет, зависящий от пакета более низкого уровня, удаляется автоматически.

  + Для интеграции с R удалите **microsoft-r-open** *.
  + Для интеграции с Python удалите **mssql-mlservices-python**.

Команды для удаления пакетов приведены в таблице ниже.

| Платформа  | Команды для удаления пакетов | 
|-----------|----------------------------|
| Red Hat   | `sudo yum remove microsoft-r-open-mro-3.4.4`<br/>`sudo yum remove msssql-mlservices-python` |
| SUSE  | `sudo zypper remove microsoft-r-open-mro-3.4.4`<br/>`sudo zypper remove msssql-mlservices-python` |
| Ubuntu    | `sudo apt-get remove microsoft-r-open-mro-3.4.4`<br/>`sudo apt-get remove msssql-mlservices-python`|

> [!Note]
> Microsoft R Open 3.4.4 состоит из двух или трех пакетов в зависимости от того, какой выпуск CTP был установлен ранее. (Пакет foreachiterators был объединен в основной пакет mro в CTP 2.2.) Если какие-либо из этих пакетов остаются после удаления microsoft-r-open-mro-3.4.4, их следует удалить отдельно.
> ```
> microsoft-r-open-foreachiterators-3.4.4
> microsoft-r-open-mkl-3.4.4
> microsoft-r-open-mro-3.4.4
> ```

### <a name="3-proceed-with-install"></a>3. Перейдите к установке

Выполните установку на самом верхнем уровне пакета, следуя инструкциям из этой статьи для вашей операционной системы.

Для каждого набора инструкций по установке, относящихся к определенной ОС, *наивысшим уровнем пакета* является **Пример 1. Полная установка** для полного набора пакетов либо **Пример 2. Минимальная установка** для минимального количества пакетов, необходимого для выполнения установки.

1. Для интеграции с R начните с [MRO](#mro), так как это обязательный компонент. Без него интеграция с R не будет устанавливаться.

2. Выполните команды установки, используя диспетчеры пакетов и синтаксис для вашей операционной системы. 

   + [Red Hat](#RHEL)
   + [Ubuntu](#ubuntu)
   + [SUSE](#suse)

## <a name="prerequisites"></a>Предварительные требования

+ Версия Linux должна [поддерживаться SQL Server](sql-server-linux-release-notes-2019.md#supported-platforms), но не включает в себя подсистему Docker. Поддерживаемые версии

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [SUSE Enterprise Linux Server](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ (Только для R.) [Microsoft R Open](#mro) предоставляет базовый дистрибутив R для компонента R в SQL Server.

+ У вас должно быть средство для выполнения команд T-SQL. Редактор запросов необходим для настройки и проверки после установки. Рекомендуется использовать бесплатное решение [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download?view=sql-server-2017#get-azure-data-studio-for-linux), работающее в Linux.

<a name="mro"></a>

### <a name="microsoft-r-open-mro-installation"></a>Установка Microsoft R Open (MRO)

Базовый дистрибутив R от Майкрософт является необходимым компонентом для использования RevoScaleR, MicrosoftML и других пакетов R, устанавливаемых вместе со Службами машинного обучения.

Требуемая версия: MRO 3.5.2.

Выберите один из следующих двух подходов для установки MRO.

+ Скачайте tarball-архив MRO из MRAN, распакуйте его и запустите сценарий install.sh. Вы можете выполнить [инструкции по установке в MRAN](https://mran.microsoft.com/releases/3.5.2), если хотите использовать этот подход.

+ Кроме того, можно зарегистрировать репозиторий **packages.microsoft.com**, как описано ниже, чтобы установить два пакета, составляющие дистрибутив MRO: microsoft-r-open-mro и microsoft-r-open-mkl. 

Следующие команды регистрируют репозиторий, предоставляющий MRO. После регистрации команды для установки других пакетов R, таких как mssql-mlservices-mml-r, будут автоматически включать MRO в качестве зависимости пакета.

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

#### <a name="mro-on-red-hat"></a>MRO в Red Hat

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

На устройстве, подключенном к Интернету, пакеты скачиваются и устанавливаются независимо от ядра СУБД с помощью установщика пакетов для каждой операционной системы. В следующей таблице описаны все доступные пакеты, однако для R и Python можно указать пакеты, обеспечивающие установку всех компонентов или установку минимального набора компонентов.

| Имя пакета | Область действия | Описание |
|--------------|----------|-------------|
|mssql-server-extensibility  | All | Платформа расширяемости, используемая для выполнения кода R и Python. |
| microsoft-openmpi  | Python, R | Интерфейс передачи сообщений, используемый библиотеками Revo * для параллелизации в Linux. |
| mssql-mlservices-python | Python | Дистрибутив Anaconda и Python с открытым кодом. |
|mssql-mlservices-mlm-py  | Python | *Полная установка*. Предоставляет revoscalepy, microsoftml, предварительно обученные модели для выделения признаков изображений и анализа тональности текста.| 
|mssql-mlservices-packages-py  | Python | *Минимальная установка*. Предоставляет revoscalepy и microsoftml. <br/>Не включает в себя предварительно обученные модели. | 
| [microsoft-r-open *](#mro) | R | Дистрибутив R с открытым исходным кодом, состоящий из трех пакетов. |
|mssql-mlservices-mlm-r  | R | *Полная установка*. Предоставляет RevoScaleR, MicrosoftML, sqlRUtils, olapR, предварительно обученные модели для выделения признаков изображений и анализа тональности текста.| 
|mssql-mlservices-packages-r  | R | *Минимальная установка*. Предоставляет RevoScaleR, sqlRUtils, MicrosoftML, olapR. <br/>Не включает в себя предварительно обученные модели. | 

<a name="RHEL"></a>

## <a name="redhat-commands"></a>Команды RedHat

Поддержку языков можно установить в любом требуемом сочетании (один или несколько языков). Для R и Python можно выбрать один из двух пакетов. Один предоставляет все доступные функции, что соответствует *полной установке*. Другой вариант исключает предварительно обученные модели машинного обучения и считается *минимальной установкой*.

> [!Tip]
> По возможности запустите `yum clean all`, чтобы обновить пакеты в системе перед установкой.

### <a name="example-1----full-installation"></a>Пример 1. Полная установка 

Включает в себя R и Python с открытым исходным кодом, платформу расширяемости, microsoft-openmpi, расширения (R, Python), а также библиотеки машинного обучения и предварительно обученные модели для R и Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python)
# Be sure to include -9.4.7* in mlsservices package names
sudo yum install mssql-mlservices-mlm-py-9.4.7*
sudo yum install mssql-mlservices-mlm-r-9.4.7* 
```

### <a name="example-2---minimum-installation"></a>Пример 2. Минимальная установка 

Включает в себя R и Python с открытым исходным кодом, платформу расширяемости, microsoft-openmpi, расширения (R, Python), а также основные библиотеки Revo * и библиотеки машинного обучения для R и Python. Не включает в себя предварительно обученные модели.

```bash
# Install as root or sudo
# Minimum install of R, Python extensions
# Be sure to include -9.4.6* in mlsservices package names
sudo yum install mssql-mlservices-packages-py-9.4.7*
sudo yum install mssql-mlservices-packages-r-9.4.7*
```

<a name="ubuntu"></a>

## <a name="ubuntu-commands"></a>Команды Ubuntu

Поддержку языков можно установить в любом требуемом сочетании (один или несколько языков). Для R и Python можно выбрать один из двух пакетов. Один предоставляет все доступные функции, что соответствует *полной установке*. Другой вариант исключает предварительно обученные модели машинного обучения и считается *минимальной установкой*.

> [!Tip]
> По возможности запустите `apt-get update`, чтобы обновить пакеты в системе перед установкой. Кроме того, некоторые образы Docker в Ubuntu могут не иметь варианта транспорта apt https. Чтобы установить его, используйте `apt-get install apt-transport-https`.

### <a name="example-1----full-installation"></a>Пример 1. Полная установка 

Включает в себя R и Python с открытым исходным кодом, платформу расширяемости, microsoft-openmpi, расширения (R, Python), а также библиотеки машинного обучения и предварительно обученные модели для R и Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python)
# There is no asterisk in this full install
sudo apt-get install mssql-mlservices-mlm-py 
sudo apt-get install mssql-mlservices-mlm-r 
```

### <a name="example-2---minimum-installation"></a>Пример 2. Минимальная установка 

Включает в себя R и Python с открытым исходным кодом, платформу расширяемости, microsoft-openmpi, расширения (R, Python), а также основные библиотеки Revo * и библиотеки машинного обучения для R и Python. Не включает в себя предварительно обученные модели. 

```bash
# Install as root or sudo
# Minimum install of R, Python
# No aasterisk
sudo apt-get install mssql-mlservices-packages-py
sudo apt-get install mssql-mlservices-packages-r
```

<a name="suse"></a>

## <a name="suse-commands"></a>Команды SUSE

Поддержку языков можно установить в любом требуемом сочетании (один или несколько языков). Для R и Python можно выбрать один из двух пакетов. Один предоставляет все доступные функции, что соответствует *полной установке*. Другой вариант исключает предварительно обученные модели машинного обучения и считается *минимальной установкой*.

### <a name="example-1----full-installation"></a>Пример 1. Полная установка 

Включает в себя R и Python с открытым исходным кодом, платформу расширяемости, microsoft-openmpi, расширения (R, Python), а также библиотеки машинного обучения и предварительно обученные модели для R и Python. 

```bash
# Install as root or sudo
# Add everything (all R, Python)
# Be sure to include -9.4.7* in mlsservices package names
sudo zypper install mssql-mlservices-mlm-py-9.4.7*
sudo zypper install mssql-mlservices-mlm-r-9.4.7* 
```

### <a name="example-2---minimum-installation"></a>Пример 2. Минимальная установка 

Включает в себя R и Python с открытым исходным кодом, платформу расширяемости, microsoft-openmpi, расширения (R, Python), а также основные библиотеки Revo * и библиотеки машинного обучения для R и Python. Не включает в себя предварительно обученные модели. 

```bash
# Install as root or sudo
# Minimum install of R, Python extensions
# Be sure to include -9.4.6* in mlsservices package names
sudo zypper install mssql-mlservices-packages-py-9.4.7*
sudo zypper install mssql-mlservices-packages-r-9.4.7*
```

## <a name="post-install-config-required"></a>Настройка после установки (обязательно)

Дополнительная настройка осуществляется в основном с помощью [средства mssql-conf](sql-server-linux-configure-mssql-conf.md).


1. Добавьте учетную запись пользователя mssql, использованную для запуска службы SQL Server. Это необходимо, если вы не выполняли установку ранее.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

2. Примите условия лицензионного соглашения для R и Python с открытым исходным кодом. Это можно сделать несколькими способами. Если ранее вы приняли условия лицензирования SQL Server и теперь добавляете расширения R или Python, следующая команда выразит ваше согласие с соответствующими условиями.

   ```bash
   # Run as SUDO or root
   # Use set + EULA 
   sudo /opt/mssql/bin/mssql-conf set EULA accepteulaml Y
   ```

   Альтернативная процедура заключается в том, что если вы еще не приняли условия соглашения о лицензировании ядра СУБД SQL Server, то программа установки обнаружит пакеты mssql-mlservices и выведет запрос на принятие условий лицензионного соглашения при запуске `mssql-conf setup`. Дополнительные сведения о параметрах лицензионного соглашения см. в статье [Настройка SQL Server с помощью средства mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-eula).

3. Включите исходящий сетевой доступ. По умолчанию исходящий сетевой доступ отключен. Чтобы включить исходящие запросы, задайте логическое свойство outboundnetworkaccess с помощью средства mssql-conf. Дополнительные сведения см. в статье [Настройка SQL Server на Linux с помощью средства mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-outbound-access).

   ```bash
   # Run as SUDO or root
   # Enable outbound requests over the network
   sudo /opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 1
   ```

4. Только для интеграции с R присвойте переменной среды **MKL_CBWR** значение [ensure consistent output](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) из вычислений Intel Math Kernel Library (MKL).

   + Измените или создайте файл **.bash_profile** в домашнем каталоге пользователя, добавив в него `export MKL_CBWR="AUTO"`.

   + Выполните этот файл, введя команду `source .bash_profile` в командной строке bash.

5. Перезапустите службу панели запуска SQL Server и экземпляр ядра СУБД, чтобы считать обновленные значения из INI-файла. При изменении любого свойства, связанного с расширяемостью, появляется сообщение с напоминанием о необходимости перезапуска.  

   ```bash
   systemctl restart mssql-launchpadd

   systemctl restart mssql-server.service
   ```

6. Включите выполнение внешнего скрипта с помощью Azure Data Studio или другого средства, например SQL Server Management Studio (только для Windows), выполняющего скрипты Transact-SQL. 

   ```bash
   EXEC sp_configure 'external scripts enabled', 1 
   RECONFIGURE WITH OVERRIDE 
   ```

7. Снова перезапустите службу панели запуска.

## <a name="verify-installation"></a>Проверка установки

Библиотеки R (MicrosoftML, RevoScaleR и др.) можно найти по адресу `/opt/mssql/mlservices/libraries/RServer`.

Библиотеки Python (microsoftml и revoscalepy) можно найти по адресу `/opt/mssql/mlservices/libraries/PythonServer`.

Чтобы проверить установку, запустите скрипт T-SQL, который выполняет системную хранимую процедуру, вызывающую R или Python. Для выполнения этой задачи потребуется средство обработки запросов. Хорошим выбором станет Azure Data Studio. Другие распространенные средства, такие как SQL Server Management Studio или PowerShell, подходят только для Windows. Если у вас есть компьютер под управлением Windows с этими средствами, используйте его для подключения к установке ядра СУБД Linux.

Выполните следующую команду SQL для тестирования выполнения R в SQL Server. Если этот скрипт не выполняется, попробуйте перезапустить службу: `sudo systemctl restart mssql-server.service`.

```r
EXEC sp_execute_external_script   
@language =N'R', 
@script=N' 
OutputDataSet <- InputDataSet', 
@input_data_1 =N'SELECT 1 AS hello' 
WITH RESULT SETS (([hello] int not null)); 
GO 
```
 
Выполните следующую команду SQL для тестирования выполнения Python в SQL Server. 
 
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

## <a name="chained-combo-install"></a>Комбинированная установка по цепочке

Вы можете установить и настроить ядро СУБД и Службы машинного обучения в одной процедуре, добавив параметры и пакеты R или Python в команду, устанавливающую ядро СУБД. 

1. Для интеграции с R установите [Microsoft R Open](#mro) в качестве необходимого компонента. Пропустите этот шаг, если вы не устанавливаете компонент R.

2. Укажите командную строку, включающую ядро СУБД, а также функции расширения языка.

  Вы можете добавить в установку ядра СУБД один компонент, например интеграцию с Python,

  ```bash
  sudo yum install -y mssql-server mssql-mlservices-packages-r-9.4.7* 
  ```

  либо добавить оба расширения (R, Python).

  ```bash
  sudo yum install -y mssql-server mssql-mlservices-packages-r-9.4.7* mssql-mlservices-packages-py-9.4.7*
  ```

3. Примите условия лицензионных соглашений и завершите настройку после установки. Для этой задачи используйте средство **mssql-conf**.

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

  Вам будет предложено принять условия лицензионного соглашения для ядра СУБД, выбрать выпуск и задать пароль администратора. Вам также будет предложено принять условия лицензионного соглашения для Служб машинного обучения.

4. При появлении соответствующего запроса перезапустите службу.

  ```bash
  sudo systemctl restart mssql-server.service
  ```

## <a name="unattended-installation"></a>Автоматическая установка

С помощью [автоматической установки](https://docs.microsoft.com/sql/linux/sql-server-linux-setup?view=sql-server-2017#unattended) для ядра СУБД вы можете добавить пакеты для mssql-mlservices и лицензионных соглашений.

Помните, что программа установки или средство mssql-conf запрашивает принятие условий лицензионного соглашения. Если вы уже настроили ядро СУБД SQL Server и приняли условия соответствующего лицензионного соглашения, используйте один из параметров лицензионного соглашения, привязанный к mlservices, для дистрибутивов R и Python с открытым исходным кодом.

```bash
sudo /opt/mssql/bin/mssql-conf setup accept-eula-ml
```

Все возможные комбинации при принятии условий лицензионного соглашения описаны в статье [Настройка SQL Server на Linux с помощью средства mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-eula).

## <a name="offline-installation"></a>Автономная установка

Описание шагов по установке пакетов см. в инструкциях по [автономной установке](sql-server-linux-setup.md#offline). Найдите сайт скачивания, а затем скачайте конкретные пакеты с помощью приведенного ниже списка.

> [!Tip]
> Некоторые средства управления пакетами предоставляют команды, помогающие определить зависимости пакетов. Для yum используйте `sudo yum deplist [package]`. Для Ubuntu используйте `sudo apt-get install --reinstall --download-only [package name]`, а затем `dpkg -I [package name].deb`.


#### <a name="download-site"></a>Сайт загрузки

Пакеты можно скачать по адресу [https://packages.microsoft.com/](https://packages.microsoft.com/). Все пакеты mlservices для R и Python размещены вместе с пакетом ядра СУБД. Базовой версией для пакетов mlservices является 9.4.6. Не забывайте, что пакеты microsoft-r-open находятся [в другом репозитории](#mro).

#### <a name="rhel7-paths"></a>Пути RHEL/7

|||
|--|----|
| Пакеты mssql/mlservices | [https://packages.microsoft.com/rhel/7/mssql-server-2019/](https://packages.microsoft.com/rhel/7/mssql-server-2019/) |
| Пакеты microsoft-r-open | [https://packages.microsoft.com/rhel/7/prod/](https://packages.microsoft.com/rhel/7/prod/) | 


#### <a name="ubuntu1604-paths"></a>Пути Ubuntu/16.04

|||
|--|----|
| Пакеты mssql/mlservices | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/) |
| Пакеты microsoft-r-open | [https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/) | 

#### <a name="sles12-paths"></a>Пути SLES/12

|||
|--|----|
| Пакеты mssql/mlservices | [https://packages.microsoft.com/sles/12/mssql-server-2019/](https://packages.microsoft.com/sles/12/mssql-server-2019/) |
| Пакеты microsoft-r-open | [https://packages.microsoft.com/sles/12/prod/](https://packages.microsoft.com/sles/12/prod/) | 

#### <a name="package-list"></a>Список пакетов

В зависимости от того, какие расширения вы хотите использовать, скачайте пакеты, необходимые для конкретного языка. Точные имена файлов содержат сведения о платформе в суффиксе, но приведенные ниже имена должны быть достаточно понятными, чтобы вы могли определить, какие файлы нужно получить.

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

## <a name="add-more-rpython-packages"></a>Добавление дополнительных пакетов R/Python 
 
Вы можете установить другие пакеты R и Python и использовать их в скрипте, выполняемом в SQL Server 2019.

### <a name="r-packages"></a>Пакеты R 
 
1. Запустите сеанс R.

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R 
   ```

2. Установите пакет R с именем [glue](https://mran.microsoft.com/package/glue), чтобы проверить установку пакета.

   ```r
   # install.packages("glue",lib="/opt/mssql/mlservices/libraries/RServer") 
   ```
   Кроме того, можно установить пакет R из командной строки. 

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R CMD INSTALL -l /opt/mssql/mlservices/libraries/RServer glue_1.1.1.tar.gz 
   ```

3. Импортируйте пакет R в [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

   ```r
   EXEC sp_execute_external_script  
   @language = N'R', 
   @script = N'library(glue)' 
   ```

### <a name="python-packages"></a>Пакеты Python 
 
1. Установите пакет Python с именем [httpie](https://httpie.org/), используя pip. 

   ```python
   # sudo /opt/mssql/mlservices/bin/python/python -m pip install httpie 
   ``` 

2. Импортируйте пакет Python в [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
 
   ```python
   EXEC sp_execute_external_script  
   @language = N'Python',  
   @script = N'import httpie' 
   ```

## <a name="run-in-a-container"></a>Запуск в контейнере

Выполните следующие действия, чтобы создать и запустить Службы машинного обучения SQL Server в контейнере Docker. Дополнительные сведения см. в статье [Настройка образов контейнеров SQL Server в Docker](sql-server-linux-configure-docker.md).

### <a name="prerequisites"></a>Предварительные требования

- Интерфейс командной строки Git.
- Docker Engine 1.8 или более поздней версии на любом поддерживаемом дистрибутиве Linux или Docker для Mac или Windows. Дополнительные сведения см. в разделе [Установка Docker](https://docs.docker.com/engine/installation/).
- Не менее 2 гигабайт (ГБ) места на диске.
- Не менее 2 ГБ ОЗУ.
- [Требования к системе для SQL Server на Linux](sql-server-linux-setup.md#system).

### <a name="clone-the-mssql-docker-repository"></a>Клонирование репозитория mssql-docker

1. Откройте терминал bash в ОС Linux или Mac либо терминал WSL в ОС Windows.

1. Создайте локальный каталог для хранения локальной копии репозитория mssql-docker.

1. Выполните команду git clone, чтобы клонировать репозиторий mssql-docker:

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

### <a name="build-a-sql-server-linux-container-image-with-machine-learning-services"></a>Создание образа контейнера SQL Server в Linux со Службами машинного обучения

1. Измените каталог на mssql-mlservices:

    ```bash
    cd mssql-docker/linux/preview/examples/mssql-mlservices
    ```

1. Выполните скрипт build.sh:

   ```bash
   ./build.sh
   ```

   > [!NOTE]
   > Для создания образа Docker вам нужно установить пакеты размером в несколько ГБ. Выполнение скрипта может занять до 20 минут. Этот период зависит от пропускной способности сети.

### <a name="run-the-sql-server-linux-container-image-with-machine-learning-services"></a>Запуск образа контейнера SQL Server в Linux со Службами машинного обучения

1. Перед запуском контейнера задайте переменные среды. В качестве значения переменной среды PATH_TO_MSSQL укажите каталог узла:

   ```bash
    export MSSQL_PID='Developer'
    export ACCEPT_EULA='Y'
    export ACCEPT_EULA_ML='Y'
    export PATH_TO_MSSQL='/home/mssql/'
   ```

1. Выполните скрипт run.sh:

   ```bash
   ./run.sh
   ```

   Эта команда позволяет создать контейнер SQL Server со Службами машинного обучения, используя выпуск Developer Edition (по умолчанию). Порт SQL Server **1433** доступен на узле как порт **1401**.

   > [!NOTE]
   > Процесс запуска контейнера с рабочими выпусками SQL Server немного отличается. Дополнительные сведения см. в статье [Настройка образов контейнеров SQL Server в Docker](sql-server-linux-configure-docker.md). Если вы используете те же имена и порты контейнеров, действия в оставшейся части этого руководства будут актуальны и для рабочих контейнеров.

1. Чтобы просмотреть контейнеры Docker, выполните команду `docker ps`:

   ```bash
   sudo docker ps -a
   ```

1. Если в столбце **STATUS** (Состояние) отображается значение **Up** (Работает), SQL Server выполняется в контейнере и прослушивает порт, указанный в столбце **PORTS** (Порты). Если в столбце **STATUS** контейнера с SQL Server отображается **Exited** (завершен), см.руководство [Устранение неполадок конфигурации](sql-server-linux-configure-docker.md#troubleshooting).

   ```bash
   $ sudo docker ps -a
   ```

    Выходные данные: 
    
    ```
    CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
    941e1bdf8e1d        mcr.microsoft.com/mssql/server/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour     0.0.0.0:1401->1433/tcp   sql1
    ```

## <a name="next-steps"></a>Дальнейшие действия

Разработчики на языке R могут ознакомиться с простыми примерами, а также узнать, как код R работает с SQL Server. Дополнительные сведения см. в следующих статьях.

+ [Руководство. Запуск R в T-SQL](../advanced-analytics/tutorials/quickstart-r-create-script.md)
+ [Руководство. Аналитические функции в базе данных для разработчиков R](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

Разработчики на языке Python могут узнать, как использовать Python с SQL Server, изучив следующие руководства.

+ [Руководство. Запуск Python в T-SQL](../advanced-analytics/tutorials/run-python-using-t-sql.md)
+ [Руководство. Аналитические функции в базе данных для разработчиков Python](../advanced-analytics/tutorials/sqldev-in-database-python-for-sql-developers.md)

Примеры машинного обучения, основанные на реальных сценариях, см. в разделе [руководствах по машинному обучению](../advanced-analytics/tutorials/machine-learning-services-tutorials.md).
