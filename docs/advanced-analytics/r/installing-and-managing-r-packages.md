---
title: "Пакеты R, установленных с SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 4d426cf6-a658-4d9d-bfca-4cdfc8f1567f
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 082aea3b1cde3c335dd7fa51b8ef219fc30f7efd
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2018
---
# <a name="r-packages-installed-with-sql-server"></a>Пакеты R, установленных с SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описываются пакеты R, которые устанавливаются вместе с SQL Server, если установить и включить функции обучения компьютера. В этой статье также описывается управление и просмотр существующих пакетов или добавления новых пакетов в экземпляре SQL Server.

**Применяется к:** SQL Server 2017 г машины обучения Services (в базе данных), SQL Server 2016 R Services (в базе данных)

## <a name="what-is-the-instance-library-and-where-is-it"></a>Что такое экземпляр библиотеки и где именно?

Все решения R, работающий в SQL Server можно использовать только пакеты, установленные в библиотеке R по умолчанию, связанный с экземпляром. При установке компонентов R в SQL Server библиотеки пакета R расположен в папке экземпляра.

+ Экземпляр по умолчанию *MSSQLSERVER* 

    SQL Server 2017: `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library` 
    
    SQL Server 2016: `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`

+ Именованный экземпляр *Мойименованныйэкземпляр* 

    SQL Server 2017: `C:\Program Files\Microsoft SQL Server\MSSQL14.MyNamedInstance\R_SERVICES\library` 
    
    SQL Server 2016: `C:\Program Files\Microsoft SQL Server\MSSQL13.MyNamedInstance\R_SERVICES\library`

Вы можете выполнить приведенную ниже инструкцию, чтобы проверить библиотеку по умолчанию для текущего экземпляра R.

```sql
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

Alternatiely, вы можете использовать новый [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) функционировать, если при выполнении пакета\_выполнение\_внешних\_сценария непосредственно на целевом компьютере. Функция не может возвращать путей к библиотеке для удаленных соединений.

```sql
EXEC sp_execute_external_script
  @language =N'R',
  @script=N'
  sql_r_path <- rxSqlLibPaths("local")
  print(sql_r_path)
```

> [!NOTE]
> При использовании привязки для обновления компонентов R в экземпляре, можно изменить путь к библиотеке экземпляра. Не забудьте проверить библиотеку, в которой используется сервером SQL Server.

## <a name="r-packages-installed-with-sql-server"></a>Пакеты R, установленных с SQL Server

По умолчанию R **базового** установки пакетов. Базовые пакеты включения основных функциональных возможностей, предоставляемых пакетов, например `stats` и `utils`.

Установка r в SQL Server 2016 или 2017 г. SQL Server всегда включает **RevoScaleR** пакета и связанные улучшенные пакеты и поставщики, которые поддерживает контекстах удаленных вычислений потоковой передачи, параллельного выполнения функция rx и Многие другие возможности. Чтобы обновить пакет RevoScaleR, либо использовать привязку для просто машинного обучения компоненты, обновления или исправления или обновите экземпляр до более новой версии SQL Server.

+ Обзор расширенные возможности R см. в разделе [о компьютере обучения, сервер](https://docs.microsoft.com/machine-learning-server/what-is-microsoft-r-server)

+ Чтобы загрузить библиотеки RevoScaleR на компьютер клиента, установите [клиент Microsoft R](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

## <a name="permissions-required-for-installing-r-packages"></a>Разрешения, необходимые для установки R-пакетов

В SQL Server 2016 администратор было установить новые пакеты R на уровне экземпляра. 

2017 г. SQL Server появились новые возможности установки пакета и управления:

+ Для установки пакетов с помощью закрытые или общие области, можно использовать команды R с удаленного клиента. Для этой функции требуется либо [Microsoft R Server](https://docs.microsoft.com/machine-learning-server/install/r-server-install) или [машины обучения Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), а также права доступа dbo в экземпляре.
+ Новые возможности базы данных были добавлены для поддержки пакета управления администраторами баз данных без использования T-SQL. В будущем эти функции обеспечивают администраторам баз данных с возможностью делегировать большинство аспектов управления пакетами привилегированным пользователям.

В этом разделе описываются разрешения, необходимые для установки и управления пакетами по версиям.

+ Службы R SQL Server 2016 (в базе данных)

    Чтобы установить новый R-пакет на компьютере, на котором выполняется [!INCLUDE [ssCurrent](..\..\includes\sscurrent-md.md)], необходимо иметь права администратора на компьютере. Задача, администратор базы данных или другого администратора на сервере, чтобы убедиться, что установлены все необходимые пакеты на [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] экземпляра.

    Если у вас прав администратора на компьютере, на котором размещена [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] экземпляр, можно предоставлять данные администратора о том, как установить пакеты R и обеспечивают доступ к репозитория безопасного пакетов где пакетов по запросу пользователи могут быть получены.

+ Службы машинного обучения SQL Server 2017

    Если вы являетесь администратором на экземпляре SQL Server, можно установить новые пакеты на будут. Просто нужно убедиться, что для использования библиотеки по умолчанию, связанный с экземпляром. Пакеты, установленные в других местах невозможна при вызове из хранимой процедуры. Любой код R, который выполняется в SQL Server, что контекст вычислений также требует, чтобы пакеты были доступны в библиотеке экземпляра.

    Этот выпуск также включает ряд новых функций, которые предназначены для поддержки упрощает управление пакета администраторами баз данных в более поздней версии. На данном этапе рекомендуется продолжать устанавливать пакеты R на уровне экземпляра.

+ R Server (Standalone)

    Вам требуются права администратора на компьютере для установки новых пакетов R.

+ Другие клиентские среды

    Если вы устанавливаете новый R-пакет на компьютере, который используется в качестве рабочей станции R и на компьютере, **не** есть экземпляр [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] установлен, по-прежнему необходимые права администратора на компьютере Установите пакет. После установки пакета его можно выполнять локально.

## <a name="managing-or-viewing-installed-packages"></a>Управление и Просмотр установленных пакетов

Существует несколько способов, которые можно получить полный список пакетов, установленных в настоящее время. Дополнительные сведения см. в разделе [определить, какие пакеты устанавливаются на сервере SQL Server](determine-which-packages-are-installed-on-sql-server.md).
