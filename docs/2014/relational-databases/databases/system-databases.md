---
title: Системные базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- system databases [SQL Server]
- displaying system database data
- modifying system data
- viewing system database data
ms.assetid: 30468a7c-4225-4d35-aa4a-ffa7da4f1282
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 916fd6d996a1a5270173d290c61f262ddf3f797b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62871131"
---
# <a name="system-databases"></a>Системные базы данных
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входят следующие системные базы данных.  
  
|Системная база данных|Description|  
|---------------------|-----------------|  
|[База данных master](master-database.md)|В этой базе данных хранятся все данные системного уровня для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[База данных msdb](msdb-database.md)|Используется агентом SQL Server для планирования предупреждений и задач.|  
|[Шаблон базы данных](model-database.md)|Используется в качестве шаблона для всех баз данных, создаваемых в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Изменение размера, параметров сортировки, модели восстановления и других параметров базы данных **model** приводит к изменению соответствующих параметров всех баз данных, создаваемых после изменения.|  
|[База данных ресурсов](resource-database.md)|База данных только для чтения. Содержит системные объекты, которые входят в состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Системные объекты физически хранятся в базе данных **Resource** , но логически отображаются в схеме **sys** любой базы данных.|  
|[База данных tempdb](tempdb-database.md)|Рабочее пространство для временных объектов или взаимодействия результирующих наборов.|  
  
## <a name="modifying-system-data"></a>Изменение системных данных  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает прямое обновление пользователями данных в таких системных объектах, как таблицы, системные хранимые процедуры и представления каталогов. Вместо этого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет полный набор административных средств, позволяющих пользователям управлять всей системой, пользователями и объектами базы данных. К ним относятся:  
  
-   Административные программы, например [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   SQL-SMO API. Этот программный интерфейс позволяет программистам включать любые административные возможности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в разрабатываемые приложения.  
  
-   
  [!INCLUDE[tsql](../../includes/tsql-md.md)] . Можно использовать системные хранимые процедуры и DDL-инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 Эти средства защищают приложения от изменений системных объектов. Например, иногда в целях поддержки новых возможностей, добавленных в новые версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , приходится изменять системные таблицы этих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Приложения, выполняющие инструкции SELECT, которые ссылаются непосредственно на системные таблицы, часто зависят от старого формата этих таблиц. Обновление сайтов до новой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] невозможно, пока для них не будут переписаны приложения, выполняющие выборку из системных таблиц. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учитывает существующие системные хранимые процедуры, DDL и опубликованные интерфейсы SQL-SMO и работает, поддерживая обратную совместимость этих интерфейсов.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживаются триггеры, заданные для системных таблиц, поскольку они могут влиять на работу системы.  
  
> [!NOTE]  
>  Системные базы данных не могут размещаться в общих каталогах UNC.  
  
## <a name="viewing-system-database-data"></a>просмотр данных системной базы данных  
 Не следует создавать инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , которые выполняют запросы непосредственно к системным таблицам, если только это не единственный способ получить данные, необходимые для приложения. Приложения должны получать данные каталога и системные данные с помощью следующих средств:  
  
-   Представления системного каталога  
  
-   SQL-SMO;  
  
-   интерфейса инструментария управления Windows (WMI);  
  
-   функций каталога, методов, атрибутов или свойств данных API, использующихся в приложении, например ADO, OLE DB или ODBC;  
  
-   
  [!INCLUDE[tsql](../../includes/tsql-md.md)] встроенных функций и системных хранимых процедур.  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Резервное копирование и восстановление системных баз данных &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [Скрыть системные объекты в обозревателе объектов](../../ssms/object/object-explorer.md)  
  
## <a name="related-content"></a>См. также  
 [Представления каталога (Transact-SQL)](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql)  
  
 [Базы данных](databases.md)  
  
  
