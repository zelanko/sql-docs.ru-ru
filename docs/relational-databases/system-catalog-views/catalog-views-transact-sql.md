---
title: Каталог представления (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/02/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sql13.SysViewExpandPortal.f1
dev_langs:
- TSQL
helpviewer_keywords:
- catalog metadata [SQL Server]
- system views [SQL Server], catalog
- metadata [SQL Server], views
- catalogs [SQL Server], metadata
- catalog views [SQL Server]
- Database Engine [SQL Server], metadata
- catalog views [SQL Server], about catalog views
ms.assetid: 13bccc2f-ed3c-4b58-abd0-ca8bf34a66b8
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5c0bbdf6ddd65621eff80301ec01f650ea1ca011
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68050863"
---
# <a name="system-catalog-views-transact-sql"></a>Системные представления каталога (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Представления каталога возвращают данные, используемые компонентом [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Рекомендуется, чтобы использовались представления каталога, потому что они имеют наиболее универсальный интерфейс к метаданным каталога и предоставляют наиболее эффективный способ для получения, преобразования и представления настроенных форм этих данных. Все доступные для пользователя метаданные каталога предоставляются через представления каталога.  
  
> [!NOTE]  
>  Представления каталога не содержат сведений о репликации, резервном копировании, плане обслуживания базы данных и данных каталога агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Некоторые представления каталога наследуют строки других представлений каталога. Например [sys.tables](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md) наследует от представления каталога [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) представления каталога. Представление каталога sys.objects называется базовым представлением, а представление sys.tables называется производным представлением. Представление каталога sys.tables возвращает столбцы, определенные для таблиц, а также все столбцы, которые возвращает представление каталога sys.objects. Представление каталога sys.objects возвращает строки для объектов, отличных от таблиц, например для хранимых процедур или представлений. После создания таблицы ее метаданные возвращаются в обоих представлениях. Хотя оба представления каталога возвращают различные уровни сведений о таблице, в метаданных этой таблицы существует только одна запись с одним именем и одним object_id. Это может быть описано следующим образом.  
  
-   Базовое представление содержит подмножество столбцов и надмножество строк.  
  
-   Производное представление содержит надмножество столбцов и подмножество строк.  
  
> [!IMPORTANT]  
>  В будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] может расширить определение любого представления системного каталога путем добавления столбцов в конец списка столбцов. Мы не рекомендуем использовать синтаксис SELECT \* FROM *sys.catalog_view_name* в рабочей среде код так, как число возвращаемых столбцов может изменить и нарушить работу приложения.  
  
 Представления каталога в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] организованы в следующие категории:  
  
|||  
|-|-|  
|[Представления каталога групп доступности Always On &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)|[Сообщения &#40;ошибок&#41; представления каталога &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/8ac78c53-7b97-41b3-9cbd-5f97c179f1f2)|  
|[Представления каталога базы данных Azure SQL](../../relational-databases/system-catalog-views/azure-sql-database-catalog-views.md)|[Объект представления каталога &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)|  
|[Представления каталога отслеживания изменений &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/6e8fd949-5560-4b34-879f-4e25aa24b183)|[Представления каталога функции секционирования &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)|  
|[Представления каталога сборки среды CLR &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)|[Административные представления на основе политик (Transact-SQL)](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)|  
|[Представления сборщика данных &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)|[Представления каталога регулятора ресурсов &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)|  
|[Пространства данных &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)|[Представления каталога хранилища запросов (Transact-SQL)](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)|  
|[Mail представления базы данных &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/database-mail-views-transact-sql.md)|[Представления каталога скалярных типов &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)|  
|[Представления каталога свидетеля зеркального отображения базы данных &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/8a0c9053-5d76-4aa9-a18d-0ea1c514034d)|[Представления каталога схем &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/c516fb1c-b6ed-48ae-99c7-a78bc4336c8e)|  
|[Представления каталога баз данных и файлов &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)|[Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)|  
|[Представления каталога конечных точек &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)|[Представления каталога компонента Service Broker (Transact-SQL)](../../relational-databases/system-catalog-views/service-broker-catalog-views-transact-sql.md)|  
|[Представления каталога расширенных событий (Transact-SQL)](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)|[Представления каталогов конфигурации на уровне сервера &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)|  
|[Представления каталога расширенных свойств (Transact-SQL)](https://msdn.microsoft.com/library/f39fd324-efd4-4468-884c-bf77ed1a026f)|[Представления каталога пространственных данных](../../relational-databases/system-catalog-views/spatial-data-catalog-views.md)|  
|[Представления каталога внешних операций &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/external-operations-catalog-views-transact-sql.md)|[Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)|  
|[Представления каталога FileTable FileStream и &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)|[Stretch Database представления каталога &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/bee78e39-e07d-4b0f-b8ad-09a01a5eb795)|  
|[Представления каталога, Full-Text Search и семантический поиск &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/full-text-search-and-semantic-search-catalog-views-transact-sql.md)|[XML-схем &#40;системой типов XML&#41; представления каталога &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)|  
|[Представления каталога связанных серверов &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)||  
  
## <a name="see-also"></a>См. также  
 [Представления информационной схемы &#40;Transact-SQL&#41;](../../relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [Системные таблицы &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)   
 [Часто задаваемые вопросы о запросах к системному каталогу SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
