---
title: Установка компонентов SQL Server машинного обучения без доступа к Интернету | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/02/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a0ec6834bf3aee8a7f8176bc5fd6d6d66d367b62
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="install-sql-server-machine-learning-components-without-internet-access"></a>Установка SQL Server машинного обучения компоненты без доступа к Интернету
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

По умолчанию узлов загрузки корпорации Майкрософт, чтобы получить необходимые подключиться установщики и обновленные компоненты для машинное обучение на сервере SQL Server. Если ограничения брандмауэра предотвратить установщик достижения этих сайтов, можно использовать устройства, подключенного к Интернету для загрузки файлов, передачи файлов на автономный сервер и снова запустите программу установки.

## <a name="get-the-installation-media"></a>Получение установочного носителя

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

> [!NOTE]  
> Для локальных установок необходимо запускать программу установки с правами администратора. При установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из удаленной общей папки необходимо использовать учетную запись домена с разрешениями на чтение и выполнение для удаленной общей папки.  
 
 ###  <a name="bkmk_ga_instalpatch"></a> Требование для установки исправления 

Корпорация Майкрософт выявила проблему с определенной версией двоичных файлов среды выполнения Microsoft VC++ 2013, которые SQL Server устанавливает в качестве необходимого компонента. Если это обновление двоичных файлов среды выполнения VC не установлено, в SQL Server могут возникать проблемы с надежностью в определенных сценариях. Перед установкой SQL Server выполните инструкции, приведенные в [заметках о выпуске SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch), чтобы узнать, требуется ли на вашем компьютере исправление для двоичных файлов среды выполнения VC.  


## <a name="download-cab-files"></a>Загрузите CAB-файлы

На сервере, подключенном к Интернету Загрузите CAB-файлы, необходимые для автономной установки. Программа установки использует CAB-файлы для установки дополнительных компонентов.

Выпуск  |Ссылка на скачивание  |
---------|---------|
**Первоначальный выпуск SQL Server 2017 г.** |
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Откройте Microsoft Python     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Сервер Microsoft Python    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |
**SQL Server 2017 г. CU1** |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
Откройте Microsoft Python     |без изменений; использовать предыдущее |
Сервер Microsoft Python    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) |
**SQL Server 2017 г. с накопительным обновлением 2** |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server      |без изменений; использовать предыдущее|
Откройте Microsoft Python     |без изменений; использовать предыдущее|
Сервер Microsoft Python    |без изменений; использовать предыдущее|
**CU3 SQL Server 2017 г.** |
Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
Откройте Microsoft Python     |без изменений; использовать предыдущее|
Сервер Microsoft Python    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)|
**SQL Server 2017 г. CU4** |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
Откройте Microsoft Python     |без изменений; использовать предыдущее|
Сервер Microsoft Python    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|
**CU5 SQL Server 2017 г.** |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server      |[SRS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869052&clcid=1033)|
Откройте Microsoft Python     |без изменений; использовать предыдущее|
Сервер Microsoft Python    |[SPS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869053&clcid=1033)|
**CU6 SQL Server 2017 г.** |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server      |[SRS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871074&clcid=1033)|
Откройте Microsoft Python     |без изменений; использовать предыдущее|
Сервер Microsoft Python    |[SPS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871073&clcid=1033)|

### <a name="bkmk_2016Installers"></a>Загружаемые файлы для SQL Server 2016

> [!IMPORTANT]
> 
> При установке SQL Server 2016 SP1 CU4 или SP1 CU5 вне сети, загрузите SRO_3.2.2.16000_1033.cab. Если вы загрузили SRO_3.2.2.13000_1033.cab из FWLINK 831785, как указано в диалоговом окне программы установки, переименуйте файл как SRO_3.2.2.16000_1033.cab перед установкой накопительного пакета обновления.

Выпуск  |Ссылка на скачивание  |
---------|---------|
**SQL Server 2016 RTM**     |
Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)
Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)
**SQL Server 2016 с накопительным пакетом обновления 1**     |
Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)
Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)
**SQL Server 2016 с накопительным пакетом обновления 2**     |
Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)
Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)
**SQL Server 2016 с накопительным пакетом обновления 3**     |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server     | без изменений; использовать предыдущее |
**SQL Server 2016 накопительным пакетом обновления 4**     |
Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)|
Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)|
**SQL Server 2016 накопительным пакетом обновления 5**     |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server     |без изменений; использовать предыдущее|
**SQL Server 2016 накопительным пакетом обновления 6**     |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server     |[SRS_8.0.3.14000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850316)  |
**SQL Server 2016 накопительным пакетом обновления 7**     |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server     |без изменений; использовать предыдущее |
**SQL Server 2016 с пакетом обновления 1 (SP1)**     |
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)
**SQL Server 2016 с пакетом обновления 1 CU1**     |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server     |без изменений; использовать предыдущее|
**SQL Server 2016 с пакетом обновления 1 с накопительным обновлением 2**     |
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
**SQL Server 2016 с пакетом обновления 1 CU3**     |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server     |без изменений; использовать предыдущее|
**SQL Server 2016 с пакетом обновления 1 CU4 и GDR**     |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)
**CU5 SQL Server 2016 с пакетом обновления 1**     |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server    |без изменений; использовать предыдущее |

Если вы хотите просмотреть исходный код для Microsoft R, его можно загрузить как архив в формате TAR или: [установщиков загрузки R Server](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows#download)

### <a name = "bkmk_OtherComponents"></a>Предварительные условия

В зависимости от среды может потребоваться создать локальные копии установщиков для следующих необходимых компонентов.

Компонент  |Version
---------|---------
[Поставщик Microsoft AS OLE DB для SQL Server 2016](https://go.microsoft.com/fwlink/?linkid=834405)     |  13.0.1601.5
[Microsoft .NET Core](https://go.microsoft.com/fwlink/?linkid=834319)     | 1.0.1
[Microsoft MPI](https://go.microsoft.com/fwlink/?linkid=834316)     | 7.1.12437.25
[Распространяемый пакет Microsoft Visual C++ 2013](https://go.microsoft.com/fwlink/?linkid=799853)     | 12.0.30501.0
[Распространяемый компонент Microsoft Visual C++ 2015](https://go.microsoft.com/fwlink/?linkid=828641)     | 14.0.23026.0

## <a name="transfer-files"></a>Передача файлов

Перенос сжатый установочного носителя SQL Server и файлы, уже загружены на компьютер, на котором вы устанавливаете программы установки.

Таких как поместить CAB-файлов в папке удобный **загружает** или установки временной папки: C:\Users < имя_пользователя > \AppData\Local\Temp.

Поместите файл en_sql_server_2017.iso в удобном месте. Дважды щелкните **setup.exe** начать установку.

### <a name="run-setup"></a>Запуск программы установки

При запуске программы установки SQL Server на компьютере отключен от Интернета, программа установки добавляет **автономной установки** страницы мастера, можно указать расположение CAB-файлов, скопированный на предыдущем шаге.

1. Запустите мастер установки SQL Server.

2. Когда программа установки отобразит страницу лицензирования R с открытым кодом или компонентов, Python, нажмите кнопку **Accept**. Свое согласие с условиями лицензионного соглашения можно перейти к следующему шагу.

3. В **автономной установки** страницы в **путь установки**, укажите папку, содержащую CAB-файлы, скопированное ранее.

4. Продолжить следующие появляющимся на экране инструкциям для завершения установки.

После завершения установки перезапустите службу и затем настройте сервер, чтобы включить выполнение скриптов, как описано в [установки служб SQL Server 2017 г машины обучения (в базе данных)](sql-machine-learning-services-windows-install.md) или [Установка SQL Server Службы R Services 2016 (в базе данных)](sql-r-services-windows-install.md).

## <a name="slipstream-upgrades-for-offline-servers"></a>Интегрированная установка обновлений для автономных серверов

Интегрированная установка — это возможность применить исправление или обновление для экземпляра, установка которого завершилась сбоем, чтобы устранить существующие неполадки. Преимущество этого метода заключается в том, что SQL Server обновляется прямо во время выполнения установки, поэтому необходимость в последующей перезагрузке отсутствует.

+ Если у сервера нет доступа к Интернету, скачайте установщик SQL Server, а затем соответствующие версии установщиков компонентов R и **запустите** процесс обновления.  Компоненты R, которые не включаются по умолчанию вместе с SQL Server.

+ При добавлении компонентов к существующей установке используете обновленную версию установщика SQL Server и соответствующие обновленной версии дополнительных компонентов. При указании функции R должна быть установлена программа установки ищет соответствующую версию установщики для машинного обучения компонентов.

## <a name="get-help"></a>Получить справку

Нужна помощь с установку или обновление? Ответы на часто задаваемые вопросы и известные проблемы см. в следующей статье:

* [Обновление и установка часто задаваемые вопросы — Machine Services обучения](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Чтобы проверить состояние установки экземпляра и устранить распространенные проблемы, попробуйте следующие пользовательские отчеты.

* [Пользовательские отчеты для служб SQL Server R](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

Группа поддержки служб R в этой статье показано, как выполнить автоматическую установку или обновление служб R в SQL Server 2016: [развертывание служб R на компьютерах без доступа к Интернету](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/).


## <a name="next-steps"></a>Следующие шаги

Разработчики R можно начать работу с несколько простых примеров и основные сведения о работе с SQL Server R. Следующий шаг см. по следующим ссылкам:

+ [Учебник: Запускать в T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Учебник: Анализ в базе данных для разработчиков R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Разработчиков Python можно освоить использование Python с SQL Server, выполнив следующие учебники:

+ [Учебник: Запустите Python в T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Учебник: Анализ в базе данных для разработчиков Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Чтобы просмотреть примеры машинного обучения, основанные на реальных сценариев, в разделе [машинного обучения учебники](../tutorials/machine-learning-services-tutorials.md).

