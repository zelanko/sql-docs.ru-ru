---
title: "Системные базы данных | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system databases [SQL Server]
- displaying system database data
- modifying system data
- viewing system database data
ms.assetid: 30468a7c-4225-4d35-aa4a-ffa7da4f1282
caps.latest.revision: "25"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.openlocfilehash: fac90b998c51feb54a0fe496e6d09b3bf59c1129
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="system-databases"></a>Системные базы данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] включает в себя указанные ниже системные базы данных.  
  
|Системная база данных|Описание|  
|---------------------|-----------------|  
|[База данных master](../../relational-databases/databases/master-database.md)|В этой базе данных хранятся все данные системного уровня для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[База данных msdb](../../relational-databases/databases/msdb-database.md)|Используется агентом SQL Server для планирования предупреждений и задач.|  
|[База данных model](../../relational-databases/databases/model-database.md)|Используется в качестве шаблона для всех баз данных, создаваемых в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Изменение размера, параметров сортировки, модели восстановления и других параметров базы данных **model** приводит к изменению соответствующих параметров всех баз данных, создаваемых после изменения.|  
|[База данных Resource](../../relational-databases/databases/resource-database.md)|База данных только для чтения. Содержит системные объекты, которые входят в состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Системные объекты физически хранятся в базе данных **Resource** , но логически отображаются в схеме **sys** любой базы данных.|  
|[База данных tempdb](../../relational-databases/databases/tempdb-database.md)|Рабочее пространство для временных объектов или взаимодействия результирующих наборов.|  
  
## <a name="modifying-system-data"></a>изменение системных данных  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает прямое обновление пользователями данных в таких системных объектах, как таблицы, системные хранимые процедуры и представления каталогов. Вместо этого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет полный набор административных средств, позволяющих пользователям управлять всей системой, пользователями и объектами базы данных. следующие основные параметры.  
  
-   Административные программы, например [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   SQL-SMO API. Этот программный интерфейс позволяет программистам включать любые административные возможности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в разрабатываемые приложения.  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] . Можно использовать системные хранимые процедуры и DDL-инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 Эти средства защищают приложения от изменений системных объектов. Например, иногда в целях поддержки новых возможностей, добавленных в новые версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , приходится изменять системные таблицы этих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Приложения, выполняющие инструкции SELECT, которые ссылаются непосредственно на системные таблицы, часто зависят от старого формата этих таблиц. Обновление сайтов до новой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] невозможно, пока для них не будут переписаны приложения, выполняющие выборку из системных таблиц. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учитывает существующие системные хранимые процедуры, DDL и опубликованные интерфейсы SQL-SMO и работает, поддерживая обратную совместимость этих интерфейсов.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживаются триггеры, заданные для системных таблиц, поскольку они могут влиять на работу системы.  
  
> [!NOTE]  
>  Системные базы данных не могут размещаться в общих каталогах UNC.  
  
## <a name="viewing-system-database-data"></a>просмотр данных системной базы данных  
 Не следует создавать инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , которые выполняют запросы непосредственно к системным таблицам, если только это не единственный способ получить данные, необходимые для приложения. Приложения должны получать данные каталога и системные данные с помощью следующих средств:  
  
-   представлений системного каталога;  
  
-   SQL-SMO;  
  
-   интерфейса инструментария управления Windows (WMI);  
  
-   функций каталога, методов, атрибутов или свойств данных API, использующихся в приложении, например ADO, OLE DB или ODBC;  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] встроенных функций и системных хранимых процедур.  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Резервное копирование и восстановление системных баз данных (SQL Server)](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [Скрытие системных объектов в обозревателе объектов](http://msdn.microsoft.com/library/c01d8804-838c-4f75-b78c-80e41e4fffdc)  
  
## <a name="related-content"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
 [Базы данных](../../relational-databases/databases/databases.md)  
  
  
