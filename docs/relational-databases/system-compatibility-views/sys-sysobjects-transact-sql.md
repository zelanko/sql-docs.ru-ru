---
title: sys.sysobjects (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sysobjects_TSQL
- sysobjects
- sysobjects_TSQL
- sys.sysobjects
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysobjects compatibility view
- sysobjects system table
ms.assetid: 44fdc387-67b0-4139-8bf5-ed26cf640cd1
caps.latest.revision: 41
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6ab119a6e98bcf7065ec7cf5dd2cd39d6bb57a1b
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43089044"
---
# <a name="syssysobjects-transact-sql"></a>sys.sysobjects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Содержит одну строку для каждого объекта, созданного внутри базы данных, такого, как ограничение, значение по умолчанию, журнал, правило и хранимая процедура.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Имя объекта|  
|идентификатор|**int**|Идентификатор объекта|  
|xtype|**char(2)**|Тип объекта. Может быть одним из следующих типов объекта:<br /><br /> AF = агрегатная функция (среда CLR)<br /><br /> C = ограничение CHECK<br /><br /> D = ограничение по умолчанию или DEFAULT<br /><br /> F = ограничение FOREIGN KEY<br /><br /> L = журнал<br /><br /> FN = скалярная функция<br /><br /> FS = скалярная функция сборки (среда CLR)<br /><br /> FT = функция сборки (среда CLR) с табличным значением<br /><br /> IF = подставляемая табличная функция<br /><br /> IT = внутренняя таблица<br /><br /> P = хранимая процедура<br /><br /> PC = хранимая процедура сборки (среда CLR)<br /><br /> PK = ограничение PRIMARY KEY (тип K)<br /><br /> RF = хранимая процедура фильтра репликации<br /><br /> S = системная таблица<br /><br /> SN = синоним<br /><br /> SQ = очередь обслуживания<br /><br /> TA = триггер DML сборки (среда CLR)<br /><br /> TF = табличная функция<br /><br /> TR = триггер DML SQL<br /><br /> TT = табличный тип<br /><br /> U = пользовательская таблица<br /><br /> UQ = ограничение UNIQUE (тип K)<br /><br /> V = представление<br /><br /> X = расширенная хранимая процедура|  
|uid|**smallint**|Идентификатор схемы владельца объекта. Для баз данных, обновленных из предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Идентификатор схемы эквивалентен идентификатору владельца. Вызывает переполнение или возвращает значение NULL, если количество пользователей и ролей превышает 32 767.<br /><br /> **\*\* Важные \* \***  при использовании одного из следующих [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкции DDL, необходимо использовать [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) представления вместо sys.Objects каталога.<br /><br /> СОЗДАНИЕ &AMP;#124; ALTER &AMP;#124; DROP USER<br /><br /> СОЗДАНИЕ &AMP;#124; ALTER &AMP;#124; DROP ROLE<br /><br /> СОЗДАНИЕ &AMP;#124; ALTER &AMP;#124; DROP APPLICATION ROLE<br /><br /> CREATE SCHEMA<br /><br /> ALTER AUTHORIZATION ON OBJECT|  
|сведения|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|status|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|base_schema_ver|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|replinfo|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|parent_obj|**int**|Идентификатор родительского объекта. Например, идентификатор таблицы, если это триггер или ограничение.|  
|crdate|**datetime**|Дата создания объекта.|  
|ftcatid|**smallint**|Идентификатор полнотекстового каталога для всех пользовательских таблиц, зарегистрированных для полнотекстового индексирования, и 0 для всех пользовательских таблиц, незарегистрированных для полнотекстового индексирования.|  
|schema_ver|**int**|Номер версии, который увеличивается каждый раз при изменении схемы для таблицы. Всегда возвращает значение 0.|  
|stats_schema_ver|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|Тип|**char(2)**|Тип объекта. Может использоваться одно из следующих значений:<br /><br /> AF = агрегатная функция (среда CLR)<br /><br /> C = ограничение CHECK<br /><br /> D = ограничение по умолчанию или DEFAULT<br /><br /> F = ограничение FOREIGN KEY<br /><br /> FN = скалярная функция<br /><br /> FS = скалярная функция сборки (среда CLR)<br /><br /> FT = функция сборки  с табличным значением (среда CLR) IF = подставляемая табличная функция<br /><br /> IT = внутренняя таблица<br /><br /> K = ограничение PRIMARY KEY или UNIQUE<br /><br /> L = журнал<br /><br /> P = хранимая процедура<br /><br /> PC = хранимая процедура сборки (среда CLR)<br /><br /> R = правило<br /><br /> RF = хранимая процедура фильтра репликации<br /><br /> S = системная таблица<br /><br /> SN = синоним<br /><br /> SQ = очередь обслуживания<br /><br /> TA = триггер DML сборки (среда CLR)<br /><br /> TF = табличная функция<br /><br /> TR = триггер DML SQL<br /><br /> TT = табличный тип<br /><br /> U = пользовательская таблица<br /><br /> V = представление<br /><br /> X = расширенная хранимая процедура|  
|userstat|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|sysstat|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|indexdel|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|refdate|**datetime**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|version|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|deltrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|instrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|updtrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|seltrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|категория|**int**|Используется для публикаций, ограничений и идентификаторов.|  
|кэш|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
