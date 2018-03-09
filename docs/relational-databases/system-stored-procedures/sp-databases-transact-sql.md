---
title: "sp_databases (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_databases_TSQL
- sp_databases
dev_langs:
- TSQL
helpviewer_keywords:
- sp_databases
ms.assetid: 2a83b92a-9ecc-43c4-8ff4-e91e3a940b5a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 444dc643385d2bf26cbc95984473f0b68519c92a
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2018
---
# <a name="spdatabases-transact-sql"></a>sp_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выдает список баз данных, которые размещаются в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или доступны через шлюз базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_databases  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**ИМЯ_БАЗЫ_ДАННЫХ**|**sysname**|Имя базы данных. В [!INCLUDE[ssDE](../../includes/ssde-md.md)], этот столбец представляет имя базы данных, хранящихся в **sys.databases** представления каталога.|  
|**DATABASE_SIZE**|**int**|Размер базы данных в килобайтах.|  
|**ПРИМЕЧАНИЯ**|**varchar(254)**|Для компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] это поле всегда возвращает значение NULL.|  
  
## <a name="remarks"></a>Remarks  
 Возвращаемые имена баз данных могут использоваться в качестве параметров в инструкции USE для изменения текущего контекста базы данных.  
  
 **sp_databases** не имеет эквивалента в Open Database Connectivity (ODBC).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CREATE DATABASE, ALTER ANY DATABASE или VIEW ANY DEFINITION; кроме того, должно быть разрешение на доступ к базе данных. Разрешение VIEW ANY DEFINITION не может быть запрещено.  
  
## <a name="examples"></a>Примеры  
 Следующий пример демонстрирует выполнение процедуры `sp_databases`.  
  
```sql  
USE master;  
GO  
EXEC sp_databases;  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [Функция HAS_DBACCESS &#40; Transact-SQL &#41;](../../t-sql/functions/has-dbaccess-transact-sql.md)  
  
  
