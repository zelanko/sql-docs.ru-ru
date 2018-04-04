---
title: Библиотеки пакета для машинного обучения на сервере SQL Server по умолчанию | Документы Microsoft
ms.custom: ''
ms.date: 02/19/2018
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: 97dc375dcee9dab2eb38c568b410e8ea2084842f
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="default-package-libraries-for-machine-learning-on-sql-server"></a>Библиотеки пакета для машинного обучения на сервере SQL Server по умолчанию
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описываются библиотеки по умолчанию R и Python, установленных с SQL Server. В этой статье предоставляет расположения по умолчанию для этих библиотек и объясняется, как определить, какие пакеты и версии R или Python, устанавливаются в каждый экземпляр библиотеки.

## <a name="using-the-default-instance-library"></a>С помощью библиотеки экземпляр по умолчанию

При установке машинного обучения с помощью SQL Server на уровне экземпляра для каждого языка, который вы устанавливаете создается библиотека одного пакета. SQL Server не может получить доступ к пакеты, установленные в других библиотеках.

При подключении к серверу с удаленного клиента, любой код R или Python, который будет выполняться в контексте сервера можно использовать только пакеты, установленные в библиотеке экземпляра.

Защита ресурсов сервера, имя библиотеки по умолчанию экземпляр устанавливается в безопасной папке, зарегистрированные с SQL Server и может быть изменен только администратором компьютера. Если вы не являетесь владельцем компьютера, может потребоваться получить разрешение от администратора для установки пакетов на эту библиотеку. 

Даже если на вашем компьютере, следует учитывать полезность любой определенный пакет R или Python в серверной среде Добавление пакета в библиотеку экземпляра. Рассмотрите также требует ли пакет сети или Интернету факторов, таких как размер файлов пакета, которые требуют нескольких версий access.

### <a name="sql-server"></a>SQL Server

|Версия | Имя экземпляра|Путь по умолчанию|
|------|------|------|
| SQL Server 2016 |экземпляр по умолчанию|`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`|
| SQL Server 2016 |именованный экземпляр |`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES\library`|
| SQL Server 2017 г. с помощью R|экземпляр по умолчанию |`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library` |
| SQL Server 2017 г. с помощью R|именованный экземпляр|`C:\Program Files\Microsoft SQL Server\MSSQL14.MyNamedInstance\R_SERVICES\library` |
| SQL Server 2017 г. с Python |экземпляр по умолчанию |`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\library` |
| SQL Server 2017 г. с Python|именованный экземпляр|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES\library` |

### <a name="r-server-standalone-or-machine-learning-server-standalone"></a>R Server (изолированный) или машины обучения Server (изолированный)

В этой таблице перечислены пути по умолчанию для двоичных файлов, при установке автономного сервера с помощью программы установки SQL Server. 

|Версия| Установка|Путь по умолчанию|
|------|------|------|
| SQL Server 2016|R Server (Standalone)| |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2017|Машинное обучение сервера с помощью R |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2017|Машинное обучение сервера с Python |`C:\Program Files\Microsoft SQL Server\130\PYTHON_SERVER`|

При установке Microsoft R Server или машинного обучения с помощью отдельного установщика Windows, отличаются пути по умолчанию: как правило, таким как `C:\Program Files\Microsoft\R Server\R_SERVER`. Дополнительные сведения см. в разделе:
 
+ [Установка машинного обучения для Windows Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Установка R Server 9.1 для Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)

## <a name="what-is-included-in-a-default-installation"></a>Что входит в установку по умолчанию

В этом разделе представлена сводка возможностей R или Python, установленных по умолчанию.

### <a name="default-r-installation-for-sql-server"></a>Установка по умолчанию R для SQL Server

По умолчанию R **базового** установки пакетов. Базовые пакеты включения основных функциональных возможностей, предоставляемых пакетов, например `stats` и `utils`.

Базовой установки R также включает многочисленные образцы наборов данных и стандартными средствами R, такими как RGui (упрощенных интерактивный редактор) и RTerm (Командная строка R).

Установка r в SQL Server 2016 или 2017 г. SQL Server также включает **RevoScaleR** пакета и связанные улучшенные пакеты и поставщики, которые поддерживает контекстах удаленных вычислений потоковой передачи, параллельного выполнения функция rx и Многие другие возможности.

Чтобы обновить пакет RevoScaleR, либо использовать привязку для просто машинного обучения компоненты, обновления или исправления или обновите экземпляр до более новой версии SQL Server.

+ Обзор расширенные возможности R см. в разделе [о компьютере обучения, сервер](https://docs.microsoft.com/machine-learning-server/what-is-microsoft-r-server)

+ Чтобы загрузить библиотеки RevoScaleR на компьютер клиента, установите [клиент Microsoft R](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

### <a name="default-python-installation-for-sql-server"></a>Установка Python по умолчанию для SQL Server

При выборе машинного обучения, функции и параметром языка Python дистрибутив Anaconda устанавливается. Точная версия зависит от того, версию SQL Server и обновлены экземпляр с помощью установщика сервера Machine обучения.

|Выпуск| Версия anaconda| Другие изменения|
|------|------|------|
| SQL Server RTM 2017 г.| 3.5.2| New: revoscalepy|
| обновление через сервер обучения машины 9.2.1 сентября 2017 г.| Anaconda 4.2| обновления для revoscalepy |
| SQL Server 2017 CU3| Anaconda 4.2| обновления для revoscalepy |

Помимо библиотеки кода Python Стандартная установка включает образцы данных, модульных тестов и сценариев.

## <a name="restrictions-and-known-issues"></a>Ограничения и известные проблемы

Любые решения, работающего в SQL Server можно использовать **только** пакетов, установленных в библиотеке по умолчанию, связанный с экземпляром.

При использовании привязки для обновления компонентов R в экземпляре, можно изменить путь к библиотеке экземпляра. Обязательно проверьте путь к библиотеке, в настоящее время используются в SQL Server.

## <a name="administrative-permissions-required-for-package-installation"></a>Административные разрешения, необходимые для установки пакета

Между SQL Server 2016 и 2017 г. SQL Server были изменены разрешения, необходимые для установки пакета.

+ В SQL Server 2016 для установки новых пакетов R требуется административный доступ.

+ В 2017 г. SQL Server можно продолжать установки пакетов от имени администратора R и Python, и возможно, это самый простой способ.

    Инструкции DDL, создать ВНЕШНИЕ БИБЛИОТЕКИ, позволяет администратору базы данных для установки пакетов без использования средств R. 

    При использовании функции пакета управления для компьютера сервера обучения RevoScaleR можно использовать для установки пакетов R на уровне базы данных. Администратор базы данных необходимо включить функцию и предоставьте пользователям возможность устанавливать собственные пакеты отдельно для каждой базы данных. Дополнительные сведения см. в разделе [пакета управления с помощью библиотеки DDL](r-package-how-to-enable-or-disable.md).

### <a name="user-libraries-are-not-supported"></a>Библиотек пользователей не поддерживаются.

Пользователи, не может установить пакет в надежном месте часто прибегать к установке пакета в библиотеку пользователя. Однако это невозможно в среде SQL Server. Даже доступ к файловой системе ограничен часто на сервере.

Даже при наличии прав администратора и доступ в папку документов пользователя на сервере среды выполнения внешнего сценария, выполняющегося в SQL Server не может получить доступ к все пакеты, установленные вне библиотеки экземпляр по умолчанию.

Советы по устранению неполадок, связанных с библиотек пользователей см. в разделе [пакет установлен в библиотеках пользователя](packages-installed-in-user-libraries.md).