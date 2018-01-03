---
title: "Пакеты R, установленных с SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 09/29/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 4d426cf6-a658-4d9d-bfca-4cdfc8f1567f
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 070e1776f0a9760742e933064be569818fe200b2
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2017
---
# <a name="r-packages-installed-with-sql-server"></a>Пакеты R, установленных с SQL Server

В этой статье описываются пакеты R, которые устанавливаются вместе с SQL Server и предоставляет сведения о способах просмотра существующих пакетов и управления ими.

В этой статье также содержит ссылки на сведения о добавлении новых пакетов для использования с SQL Server.

**Применяется к:** SQL Server 2017 г машины обучения Services (в базе данных), SQL Server 2016 R Services (в базе данных)

## <a name="what-is-the-instance-library-and-where-is-it"></a>Что такое экземпляр библиотеки и где именно?

Все решения R, работающий в SQL Server можно использовать только пакеты, установленные в библиотеке R по умолчанию, связанный с экземпляром.

При установке компонентов R в SQL Server библиотеки пакета R расположен в папке экземпляра.

+ Экземпляр по умолчанию *MSSQLSERVER* 

    SQL Server 2017 г.:`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library` 
    
    SQL Server 2016.`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`

+ Именованный экземпляр *Мойименованныйэкземпляр* 

    SQL Server 2017 г.:`C:\Program Files\Microsoft SQL Server\MSSQL14.MyNamedInstance\R_SERVICES\library` 
    
    SQL Server 2016.`C:\Program Files\Microsoft SQL Server\MSSQL13.MyNamedInstance\R_SERVICES\library`

Вы можете выполнить приведенную ниже инструкцию, чтобы проверить библиотеку по умолчанию для текущего экземпляра R.

```SQL
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```
## <a name="r-packages-installed-with-sql-server"></a>Пакеты R, установленных с SQL Server

При установке языка R в SQL Server по умолчанию R **базового** установки пакетов. Базовые пакеты включения основных функциональных возможностей, предоставляемых пакетов, например `stats` и `utils`.

Установка r в SQL Server 2016 и 2017 г. SQL Server также включает **RevoScaleR** пакета и связанные улучшенные пакеты и поставщики, которые поддерживает контекстах удаленных вычислений потоковой передачи, параллельного выполнения функция rx и Многие другие возможности.

+ Обзор расширенные возможности R см. в разделе [о компьютере обучения, сервер](https://docs.microsoft.com/r-server/what-is-microsoft-r-server)

+ Чтобы загрузить библиотеки RevoScaleR на компьютер клиента, установите [клиент Microsoft R](https://docs.microsoft.com/r-server/r-client/what-is-microsoft-r-client)

## <a name="permissions-required-for-installing-r-packages"></a>Разрешения, необходимые для установки R-пакетов

В SQL Server 2016 администратор было установить новые пакеты R на уровне экземпляра. В SQL Server 2017 г были добавлены новые возможности базы данных администратор базы данных, дать возможность делегировать управление пакетами для выбранных пользователей.

В этом разделе описываются разрешения, необходимые для установки и управления пакетами по версиям.

+ Службы R SQL Server 2016 (в базе данных)

    Чтобы установить новый R-пакет на компьютере, на котором выполняется [!INCLUDE [ssCurrent](..\..\includes\sscurrent-md.md)], необходимо иметь права администратора на компьютере. Задача, администратор базы данных или другого администратора на сервере, чтобы убедиться, что установлены все необходимые пакеты на [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] экземпляра.

    Если у вас прав администратора на компьютере, на котором размещена [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] экземпляр, можно предоставлять данные администратора о том, как установить пакеты R и обеспечивают доступ к репозитория безопасного пакетов где пакетов по запросу пользователи могут быть получены.

+ Службы машинного обучения SQL Server 2017

    Этот выпуск включает функции пакета управления, позволяющие администратору базы данных делегировать права установки пакета для выбранных пользователей. Если эта возможность включена, запрос, добавить, администратор базы данных для одной из ролей, новый пакет. Дополнительные сведения см. в разделе [R пакета управления для SQL Server](r-package-management-for-sql-server-r-services.md).

    Если вы являетесь администратором на экземпляре SQL Server, можно установить новые пакеты на будут. Просто нужно убедиться, что для использования библиотеки по умолчанию, связанный с экземпляром. Пакеты, установленные в других местах невозможна при вызове из хранимой процедуры. Любой код R, который выполняется в SQL Server, что контекст вычислений также требует, чтобы пакеты были доступны в библиотеке экземпляра.

+ R Server (Standalone)

    Вам требуются права администратора на компьютере для установки новых пакетов R.

+ Другие клиентские среды

    Если вы устанавливаете новый R-пакет на компьютере, который используется в качестве рабочей станции R и на компьютере, **не** есть экземпляр [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] установлен, по-прежнему необходимые права администратора на компьютере Установите пакет. После установки пакета его можно выполнять локально.

## <a name="managing-or-viewing-installed-packages"></a>Управление и Просмотр установленных пакетов

Существует несколько способов, которые можно получить полный список пакетов, установленных в настоящее время. Дополнительные сведения см. в разделе [определить, какие пакеты устанавливаются на сервере SQL Server](determine-which-packages-are-installed-on-sql-server.md).
