---
title: Системные таблицы (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- status information [SQL Server]
- tables [SQL Server], system tables
- information retrieval [SQL Server]
- status information [SQL Server], system tables
- system information [SQL Server]
- system tables [SQL Server]
- system tables [SQL Server], about system tables
- system tables [SQL Server], retrieving information from
- retrieving system table information
ms.assetid: 56b8ad51-930c-4e5c-8d99-8c939d5b70ac
caps.latest.revision: 41
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2658b6ab0687a3eb3c63d6d658f93ff2c25b55c6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38047219"
---
# <a name="system-tables-transact-sql"></a>Системные таблицы (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В подразделах данного раздела описаны системные таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Системные таблицы не должны изменяться непосредственно ни одним пользователем. Например, не пытайтесь изменять системные таблицы с помощью инструкций DELETE, UPDATE или INSERT либо с помощью пользовательских триггеров.  
  
 Обращение к документированным столбцам системных таблиц разрешено. Однако многие столбцы системных таблиц не документированы. В приложениях непосредственные запросы к недокументированным столбцам применять не следует. Вместо этого для получения данных, хранящихся в системных таблицах, в приложениях можно использовать один из следующих компонентов:  
  
-   Системные хранимые процедуры  
  
-   инструкции и функции языка [!INCLUDE[tsql](../../includes/tsql-md.md)];  
  
-   Управляющие объекты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SMO)  
  
-   объекты RMO;  
  
-   функции каталога Database API.  
  
 Эти компоненты составляют опубликованный API-интерфейс для получения системных сведений от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[msCoName](../../includes/msconame-md.md)] поддерживает совместимость этих компонентов от выпуска к выпуску. Формат системных таблиц зависит от внутренней архитектуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и может изменяться от выпуска к выпуску. Поэтому приложениям, получающим непосредственный доступ к недокументированным столбцам системных таблиц, могут потребоваться изменения, прежде чем они смогут получить доступ к более поздней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
 Подразделы о системных таблицах организованы по следующим группам функций.  
  
|||  
|-|-|  
|[Резервное копирование и восстановление таблиц &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)|[Таблицы доставки журналов (Transact-SQL)](../../relational-databases/system-tables/log-shipping-tables-transact-sql.md)|  
|[Изменение таблицы системы отслеживания измененных данных &#40;Transact-SQL&#41;](../../relational-databases/system-tables/change-data-capture-tables-transact-sql.md)|[Таблицы репликации (Transact-SQL)](../../relational-databases/system-tables/replication-tables-transact-sql.md)|  
|[Таблицы плана обслуживания базы данных &#40;Transact-SQL&#41;](../../relational-databases/system-tables/database-maintenance-plan-tables-transact-sql.md)|[Таблицы агента SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)|  
|[Таблицы расширенных событий SQL Server &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/6d52ff03-f5aa-4f0f-8c98-9b49dc76f94e)|[sys.sysoledbusers &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysoledbusers-transact-sql.md)|  
|[Таблицы служб Integration Services &#40;Transact-SQL&#41;](../../relational-databases/system-tables/integration-services-tables-transact-sql.md)|["systranschemas" &#40;Transact-SQL&#41;](../../relational-databases/system-views/systranschemas-transact-sql.md)|  
  
## <a name="see-also"></a>См. также  
 [Представления совместимости &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
