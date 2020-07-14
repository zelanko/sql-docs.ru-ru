---
title: Справочник по системным объектам зеркального отображения базы данных | Документация Майкрософт
description: 'См. сведения о системных объектах зеркального отображения баз данных: системных представлениях каталога, системных динамических административных представлениях и системных таблицах.'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c37c75f9824f85705f92d1fabb6519303a76fafb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85754712"
---
# <a name="database-mirroring-system-object-reference"></a>Справочник по системным объектам зеркального отображения базы данных
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="system-catalog-views"></a>Представления системного каталога

| Представление системного каталога | Описание|
| :------ | :----------------------------- |
| [sys.database_mirroring_witnesses](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   | Содержит по одной строке для каждой из следящих ролей, исполняемых сервером при участии в зеркальном отображении базы данных. |
| &nbsp; | &nbsp; |

## <a name="system-dynamic-management-views"></a>Системные динамические административные представления

| Системное динамическое административное представление | Описание|
| :------ | :----------------------------- |
| [sys.dm_db_mirroring_auto_page_repair](../../relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-auto-page-repair.md)   | Возвращает строку для каждой попытки автоматического восстановления страниц во всех зеркально отображаемых баз данных на экземпляре сервера.  |
| [sys.dm_db_mirroring_connections](../../relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-connections.md)    | Возвращает строку для каждого установленного соединения зеркального отображения базы данных. |
| &nbsp; | &nbsp; |

## <a name="system-tables"></a>Системные таблицы

| Системная таблица | Описание|
| :------ | :----------------------------- |
| [sysdbmaintplan_databases](../../relational-databases/system-tables/sysdbmaintplan-databases-transact-sql.md)   | Возвращает сведения о планах обслуживания для зеркального отображения базы данных. |
| [sysdbmaintplan_history](../../relational-databases/system-tables/sysdbmaintplan-history-transact-sql.md)    | Возвращает сведения о журнале планов обслуживания для зеркального отображения базы данных. |
| [sysdbmaintplan_jobs](../../relational-databases/system-tables/sysdbmaintplan-jobs-transact-sql.md)    |Возвращает сведения о заданиях планов обслуживания для зеркального отображения базы данных.  |
| [sysdbmaintplans](../../relational-databases/system-tables/sysdbmaintplans-transact-sql.md)    | Возвращает сведения о планах зеркального отображения баз данных.  |
| &nbsp; | &nbsp; |


## <a name="see-also"></a>См. также:  
 [Зеркальное отображение базы данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   

  
  
