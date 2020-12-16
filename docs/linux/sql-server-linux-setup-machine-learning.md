---
title: Установка в Linux
titleSuffix: SQL Server Machine Learning Services
description: Сведения об установке Служб машинного обучения SQL Server (Python, R) в Linux Red Hat, Ubuntu и SUSE.
author: dphansen
ms.author: davidph
manager: cgronlun
ms.date: 11/24/2020
ms.topic: how-to
ms.prod: sql
ms.technology: machine-learning-services
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15'
ms.openlocfilehash: 1ea9d4307281a13b21715c36d5c0cadce5f85a26
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97471415"
---
# <a name="install-sql-server-machine-learning-services-python-and-r-on-linux"></a>Установка Служб машинного обучения SQL Server (Python, R) в Linux

[!INCLUDE [SQL Server 2019 - Linux](../includes/applies-to-version/sqlserver2019-linux.md)]

В этой статье представлен порядок установки [Службы машинного обучения SQL Server](../machine-learning//sql-server-machine-learning-services.md) в Linux. Службы машинного обучения можно использовать для запуска сценариев R или Python в базе данных.

Вы можете установить Службы машинного обучения на платформах Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) и Ubuntu. Дополнительные сведения см. в разделе ["Поддерживаемые платформы" в руководстве по установке SQL Server на Linux](sql-server-linux-setup.md#supportedplatforms).

> [!NOTE]
> Службы машинного обучения устанавливаются по умолчанию в кластерах больших данных SQL Server. Дополнительные сведения см. в разделе [Использование служб машинного обучения (Python и R) в кластерах больших данных](../big-data-cluster/machine-learning-services.md)

<a name="mro"></a>

## <a name="pre-install-checklist"></a>Контрольный список перед установкой

* [Установите SQL Server в Linux](sql-server-linux-setup.md) и проверьте установку.

* Проверьте репозитории SQL Server в Linux для расширений Python и R. 
  Если вы уже настроили репозитории исходного кода для ядра СУБД, команды установки пакета **mssql-mlservices** можно выполнить, используя ту же регистрацию репозиториев.

* (Только для R) Microsoft R Open (MRO) предоставляет базовый дистрибутив R для функции R в SQL Server и является необходимым компонентом для использования RevoScaleR, MicrosoftML и других пакетов R, устанавливаемых вместе со Службами машинного обучения.
    * Требуемая версия: MRO 3.5.2.
    * Выберите один из следующих двух подходов для установки MRO.
        * Скачайте tarball-архив MRO из MRAN, распакуйте его и запустите сценарий install.sh. Вы можете выполнить [инструкции по установке в MRAN](https://mran.microsoft.com/releases/3.5.2), если хотите использовать этот подход.
        * Зарегистрируйте репозиторий **packages.microsoft.com**, как описано ниже, чтобы установить дистрибутив MRO: microsoft-r-open-mro и microsoft-r-open-mkl. 
    * Сведения об установке MRO см. в следующих разделах об установке.

* У вас должно быть средство для выполнения команд T-SQL. 

  * Вы можете использовать [Azure Data Studio](../azure-data-studio/download-azure-data-studio.md), бесплатное средство для работы с базами данных, которое работает в Linux, Windows и macOS.

## <a name="package-list"></a>Список пакетов

На устройстве, подключенном к Интернету, пакеты скачиваются и устанавливаются независимо от ядра СУБД с помощью установщика пакетов для каждой операционной системы. В следующей таблице описаны все доступные пакеты, однако для R и Python можно указать пакеты, обеспечивающие установку всех компонентов или установку минимального набора компонентов.

Доступные пакеты установки:

| Имя пакета | Область действия | Описание |
|--------------|----------|-------------|
|mssql-server-extensibility  | All | Платформа расширяемости, используемая для выполнения кода Python и R. |
| microsoft-openmpi  | Python, R | Интерфейс передачи сообщений, используемый библиотеками Rev* для распараллеливания в Linux. |
| mssql-mlservices-python | Python | Дистрибутив Anaconda и Python с открытым кодом. |
|mssql-mlservices-mlm-py  | Python | *Полная установка*. Предоставляет revoscalepy, microsoftml, предварительно обученные модели для выделения признаков изображений и анализа тональности текста.| 
|mssql-mlservices-packages-py  | Python | *Минимальная установка*. Предоставляет revoscalepy и microsoftml. <br/>Не включает в себя предварительно обученные модели. | 
| [microsoft-r-open *](#mro) | R | Дистрибутив R с открытым исходным кодом, состоящий из трех пакетов. |
|mssql-mlservices-mlm-r  | R | *Полная установка*. Предоставляет: RevoScaleR, MicrosoftML, sqlRUtils, olapR, предварительно обученные модели для выделения признаков изображений и анализа тональности текста.| 
|mssql-mlservices-packages-r  | R | *Минимальная установка*. Предоставляет RevoScaleR, sqlRUtils, MicrosoftML, olapR. <br/>Не включает в себя предварительно обученные модели. |

<a name="RHEL"></a>

## <a name="install-on-rhel"></a>Установка в RHEL

Выполните следующие действия, чтобы установить Службы машинного обучения SQL Server на Red Hat Enterprise Linux (RHEL).

### <a name="install-mro-on-rhel"></a>Установка MRO в RHEL

Следующие команды регистрируют репозиторий, предоставляющий MRO. После регистрации команды для установки других пакетов R, таких как mssql-mlservices-mml-r, будут автоматически включать MRO в качестве зависимости пакета.
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

Параметры установки для Python и R.

*  Установите языковую поддержку в соответствии с вашими требованиями (один или несколько языков).
*  В режиме *полной установки* устанавливаются все доступные функции, включая предварительно обученные модели машинного обучения.
*  В режиме *минимальной установки* исключаются модели, однако все функциональные возможности сохраняются.

> [!Tip]
> По возможности запустите `yum clean all`, чтобы обновить пакеты в системе перед установкой.

### <a name="full-installation"></a>Полная установка

Включает следующее.
*  Открытый исходный код Python
*  Открытый исходный код R
*  Платформа расширяемости
*  Microsoft-openmpi
*  Расширения (Python, R)
*  Библиотеки машинного обучения
*  Предварительно обученные модели для Python и R

```bash
# Install as root or sudo
# Add everything (all R, Python)
# Be sure to include -9.4.7* in mlsservices package names
sudo yum install mssql-mlservices-mlm-py-9.4.7*
sudo yum install mssql-mlservices-mlm-r-9.4.7*
```

### <a name="minimum-installation"></a>Минимальная установка

Включает следующее.
*  Открытый исходный код Python
*  Открытый исходный код R
*  Платформа расширяемости
*  Microsoft-openmpi
*  Основные библиотеки Revo*
*  Библиотеки машинного обучения

```bash
# Install as root or sudo
# Minimum install of R, Python extensions
# Be sure to include -9.4.6* in mlsservices package names
sudo yum install mssql-mlservices-packages-py-9.4.7*
sudo yum install mssql-mlservices-packages-r-9.4.7*
```
<a name="ubuntu"></a>

## <a name="install-on-ubuntu"></a>Установка в Ubuntu

Выполните следующие действия, чтобы установить Службы машинного обучения SQL Server на Ubuntu.

### <a name="install-mro-on-ubuntu"></a>Установка MRO на Ubuntu

Следующие команды регистрируют репозиторий, предоставляющий MRO. После регистрации команды для установки других пакетов R, таких как mssql-mlservices-mml-r, будут автоматически включать MRO в качестве зависимости пакета.

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

Параметры установки для Python и R.

*  Установите языковую поддержку в соответствии с вашими требованиями (один или несколько языков).
*  В режиме *полной установки* устанавливаются все доступные функции, включая предварительно обученные модели машинного обучения.
*  В режиме *минимальной установки* исключаются модели, однако все функциональные возможности сохраняются.

> [!Tip]
> По возможности запустите `apt-get update`, чтобы обновить пакеты в системе перед установкой. 

### <a name="full-installation"></a>Полная установка 

Включает следующее.
*  Открытый исходный код Python
*  Открытый исходный код R
*  Платформа расширяемости
*  Microsoft-openmpi
*  Расширения Python
*  Расширения R
*  Библиотеки машинного обучения
*  Предварительно обученные модели для Python и R

```bash
# Install as root or sudo
# Add everything (all R, Python)
# There is no asterisk in this full install
sudo apt-get install mssql-mlservices-mlm-py 
sudo apt-get install mssql-mlservices-mlm-r 
```

### <a name="minimum-installation"></a>Минимальная установка 

Включает следующее.
*  Открытый исходный код Python
*  Открытый исходный код R
*  Платформа расширяемости
*  Microsoft-openmpi
*  Основные библиотеки Revo*
*  Библиотеки машинного обучения

```bash
# Install as root or sudo
# Minimum install of R, Python
# No asterisk
sudo apt-get install mssql-mlservices-packages-py
sudo apt-get install mssql-mlservices-packages-r
```

<a name="SLES"></a>

## <a name="install-on-sles"></a>Установка в SLES

Выполните следующие действия, чтобы установить Службы машинного обучения SQL Server на SUSE Linux Enterprise Server (SLES).

### <a name="install-mro-on-sles"></a>Установка MRO на SLES

Следующие команды регистрируют репозиторий, предоставляющий MRO. После регистрации команды для установки других пакетов R, таких как mssql-mlservices-mml-r, будут автоматически включать MRO в качестве зависимости пакета.

```bash
# Install as root
sudo su

# Set the location of the package repo at the "prod" directory containing the distribution
# This example is for SLES12, the only supported version of SLES in Machine Learning Server
zypper ar -f https://packages.microsoft.com/sles/12/prod packages-microsoft-com

# Update packages on your system (optional)
zypper update
```

Параметры установки для Python и R.

*  Установите языковую поддержку в соответствии с вашими требованиями (один или несколько языков).
*  В режиме *полной установки* устанавливаются все доступные функции, включая предварительно обученные модели машинного обучения.
*  В режиме *минимальной установки* исключаются модели, однако все функциональные возможности сохраняются.

### <a name="full-installation"></a>Полная установка 

Включает следующее.
*  Открытый исходный код Python
*  Открытый исходный код R
*  Платформа расширяемости
*  Microsoft-openmpi
*  Расширения для Python и R
*  Библиотеки машинного обучения
*  Предварительно обученные модели для Python и R

```bash
# Install as root or sudo
# Add everything (all R, Python)
sudo zypper install mssql-mlservices-mlm-py
sudo zypper install mssql-mlservices-mlm-r
```

### <a name="minimum-installation"></a>Минимальная установка 

Включает следующее.
*  Открытый исходный код Python
*  Открытый исходный код R
*  Платформа расширяемости
*  Microsoft-openmpi
*  Основные библиотеки Revo*
*  Библиотеки машинного обучения 

```bash
# Install as root or sudo
# Minimum install of R, Python extensions
sudo zypper install mssql-mlservices-packages-py
sudo zypper install mssql-mlservices-packages-r
```

## <a name="post-install-config-required"></a>Настройка после установки (обязательно)

Дополнительная настройка осуществляется в основном с помощью [средства mssql-conf](sql-server-linux-configure-mssql-conf.md).

1. Когда установка пакета завершится, выполните команду mssql-conf setup и следуйте указаниям, чтобы задать пароль системного администратора и выбрать выпуск. Выполните этот шаг, только если вы еще не настроили SQL Server в Linux. 

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

2. Примите условия лицензионного соглашения для расширений R и Python с открытым исходным кодом. Используйте следующую команду:

   ```bash
   # Run as SUDO or root
   # Use set + EULA 
   sudo /opt/mssql/bin/mssql-conf set EULA accepteulaml Y
   ```
   Программа установки обнаруживает пакеты mssql-mlservices и предлагает принять условия лицензионного соглашения (если оно не было принято ранее) при выполнении `mssql-conf setup`. Дополнительные сведения о параметрах лицензионного соглашения см. в статье [Настройка SQL Server с помощью средства mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-eula).

3. Включите исходящий сетевой доступ. По умолчанию исходящий сетевой доступ отключен. Чтобы включить исходящие запросы, задайте логическое свойство outboundnetworkaccess с помощью средства mssql-conf. Дополнительные сведения см. в статье [Настройка SQL Server на Linux с помощью средства mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-outbound-access).

   ```bash
   # Run as SUDO or root
   # Enable outbound requests over the network
   sudo /opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 1
   ```

4. Только для интеграции с R присвойте переменной среды **MKL_CBWR** значение [ensure consistent output](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) из вычислений Intel Math Kernel Library (MKL).

   + Измените или создайте файл `.bash_profile` в домашнем каталоге пользователя, добавив в него `export MKL_CBWR="AUTO"`.

   + Выполните этот файл, введя команду `source .bash_profile` в командной строке bash.

5. Перезапустите службу панели запуска SQL Server и экземпляр ядра СУБД, чтобы считать обновленные значения из INI-файла. При изменении параметра, связанного с расширяемостью, отображается сообщение уведомления.  

   ```bash
   systemctl restart mssql-launchpadd

   systemctl restart mssql-server.service
   ```

6. Включите выполнение внешнего скрипта с помощью Azure Data Studio или другого средства, например SQL Server Management Studio (только для Windows), выполняющего скрипты Transact-SQL.

   ```sql
   EXEC sp_configure 'external scripts enabled', 1 
   RECONFIGURE WITH OVERRIDE 
   ```

7. Снова перезапустите службу панели запуска.

## <a name="verify-installation"></a>Проверка установки

Библиотеки R (MicrosoftML, RevoScaleR и др.) можно найти по адресу `/opt/mssql/mlservices/libraries/RServer`.

Библиотеки Python (microsoftml и revoscalepy) можно найти по адресу `/opt/mssql/mlservices/libraries/PythonServer`.

Порядок проверки установки

* Запустите скрипт T-SQL, который выполняет системную хранимую процедуру, вызывающую Python или R, с помощью инструмента запросов. 

* Выполните следующую команду SQL для тестирования выполнения R в SQL Server. Возникли ошибки? Попробуйте перезапустить службу, `sudo systemctl restart mssql-server.service`.
  ```sql
  EXEC sp_execute_external_script   
  @language =N'R', 
  @script=N' 
  OutputDataSet <- InputDataSet', 
  @input_data_1 =N'SELECT 1 AS hello' 
  WITH RESULT SETS (([hello] int not null)); 
  GO 
  ```
 
* Выполните следующую команду SQL для тестирования выполнения Python в SQL Server. 
 
  ```sql
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

## <a name="unattended-installation"></a>Автоматическая установка

С помощью [автоматической установки](sql-server-linux-setup.md#unattended) для ядра СУБД вы можете добавить пакеты для mssql-mlservices и лицензионных соглашений.

 Используйте один из параметров лицензионного соглашения mlservices для дистрибутивов R и Python с открытым исходным кодом:

```bash
sudo /opt/mssql/bin/mssql-conf setup accept-eula-ml
```

Полный текст лицензионного соглашения см. в статье [Настройка SQL Server в Linux с помощью средства mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-eula).

## <a name="offline-installation"></a>Автономная установка

Описание шагов по установке пакетов см. в инструкциях по [автономной установке](sql-server-linux-setup.md#offline). Найдите сайт скачивания, а затем скачайте конкретные пакеты с помощью приведенного ниже списка.

> [!Tip]
> Некоторые средства управления пакетами предоставляют команды, помогающие определить зависимости пакетов. Для yum используйте `sudo yum deplist [package]`. Для Ubuntu используйте `sudo apt-get install --reinstall --download-only [package name]`, а затем `dpkg -I [package name].deb`.

 
### <a name="download-site"></a>Сайт загрузки

Скачайте пакеты с сайта [https://packages.microsoft.com/](https://packages.microsoft.com/). Все пакеты mlservices для R и Python размещены вместе с пакетом ядра СУБД. Базовой версией для пакетов mlservices является 9.4.6. Не забывайте, что пакеты microsoft-r-open находятся [в другом репозитории](#mro).

### <a name="rhel7-paths"></a>Пути RHEL/7

|Пакет|Расположение для скачивания|
|--|----|
| Пакеты mssql/mlservices | [https://packages.microsoft.com/rhel/7/mssql-server-2019/](https://packages.microsoft.com/rhel/7/mssql-server-2019/) |
| Пакеты microsoft-r-open | [https://packages.microsoft.com/rhel/7/prod/](https://packages.microsoft.com/rhel/7/prod/) | 

### <a name="ubuntu1604-paths"></a>Пути Ubuntu/16.04

|Пакет|Расположение для скачивания|
|--|----|
| Пакеты mssql/mlservices | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/) |
| Пакеты microsoft-r-open | [https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/) | 

### <a name="sles12-paths"></a>Пути SLES/12

|Пакет|Расположение для скачивания|
|--|----|
| Пакеты mssql/mlservices | [https://packages.microsoft.com/sles/12/mssql-server-2019/](https://packages.microsoft.com/sles/12/mssql-server-2019/) |
| Пакеты microsoft-r-open | [https://packages.microsoft.com/sles/12/prod/](https://packages.microsoft.com/sles/12/prod/) | 

Выберите расширения, которые хотите использовать, скачайте пакеты, необходимые для требуемого языка. Имена файлов включают сведения о платформе в суффиксе.

### <a name="package-list"></a>Список пакетов

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

## <a name="next-steps"></a>Дальнейшие действия

Разработчики на языке Python могут узнать, как использовать Python с SQL Server, изучив следующие руководства.

+ [Учебник по Python. Прогнозирование проката лыж с помощью линейной регрессии в Службах машинного обучения SQL Server](../machine-learning/tutorials/python-ski-rental-linear-regression-deploy-model.md)
+ [Учебник по Python. Классификация клиентов на основе кластеризации методом k-средних с помощью служб машинного обучения SQL Server](../machine-learning/tutorials/python-clustering-model.md)

Разработчики на языке R могут ознакомиться с простыми примерами, а также узнать, как код R работает с SQL Server. Дополнительные сведения см. в следующих статьях.

+ [Краткое руководство. Запуск R в T-SQL](../machine-learning/tutorials/quickstart-r-create-script.md)
+ [Руководство. Аналитические функции в базе данных для разработчиков R](../machine-learning/tutorials/r-taxi-classification-introduction.md)
