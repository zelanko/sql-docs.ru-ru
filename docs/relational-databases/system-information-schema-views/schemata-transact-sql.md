---
title: SCHEMATA (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SCHEMATA_TSQL
- SCHEMATA
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
- SCHEMATA view
ms.assetid: 69617642-0f54-4b25-b62f-5f39c8909601
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a257a28a51a9e54643b14e57ff8c778179ee3bd7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85716626"
---
# <a name="schemata-transact-sql"></a>SCHEMATA (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asdw-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Возвращает по одной строке на каждую схему текущей базы данных. Чтобы получить сведения из этих представлений, укажите полное имя **INFORMATION_SCHEMA.** _view_name_. Чтобы получить сведения обо всех базах данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запросите представление каталога [sys. databases &#40;инструкции TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**CATALOG_NAME**|**sysname**|Имя текущей базы данных.|  
|**SCHEMA_NAME**|**nvarchar (** 128 **)**|Имя схемы.|  
|**SCHEMA_OWNER**|**nvarchar (** 128 **)**|Имя владельца схемы.<br /><br /> **&#42;&#42; важно &#42;&#42;** Не используйте INFORMATION_SCHEMA представления для определения схемы объекта. INFORMATION_SCHEMA представления представляют только подмножество метаданных объекта. Единственный надежный способ найти схему объекта — выполнить запрос к представлению каталога sys.objects.|  
|**DEFAULT_CHARACTER_SET_CATALOG**|**varchar (** 6 **)**|Всегда возвращает значение NULL.|  
|**DEFAULT_CHARACTER_SET_SCHEMA**|**varchar (** 3 **)**|Всегда возвращает значение NULL.|  
|**DEFAULT_CHARACTER_SET_NAME**|**sysname**|Имя установленной по умолчанию кодировки.|  

**Пример**  
В следующем примере возвращаются сведения о схемах в базе данных master:  
```sql  
SELECT * FROM master.INFORMATION_SCHEMA.SCHEMATA;
```  

## <a name="see-also"></a>См. также  
 [Системные представления &#40;&#41;Transact-SQL](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления информационной схемы &#40;&#41;Transact-SQL](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys. schemas &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)   
 [sys.sysнаборов символов &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-syscharsets-transact-sql.md)  
  
  
