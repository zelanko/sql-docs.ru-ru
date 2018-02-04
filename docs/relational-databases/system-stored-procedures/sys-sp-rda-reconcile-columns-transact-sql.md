---
title: "sys.sp_rda_reconcile_columns (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_columns
- sys.sp_rda_reconcile_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_columns stored procedure
ms.assetid: 60d9cc4e-1828-450b-9d88-5b8485800d73
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ac447329552758ad6070cf4a22489c9d1ed44e64
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="syssprdareconcilecolumns-transact-sql"></a>sys.sp_rda_reconcile_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Согласование столбцов удаленной таблицы Azure со столбцами в таблице с включенным Stretch SQL Server.  
    
  **sp_rda_reconcile_columns** добавляет столбцы удаленной таблицы, существующие в таблице с включенным Stretch SQL Server, но не в удаленной таблице. Эти столбцы могут оказаться столбцы, случайно стертые из удаленной таблицы. Тем не менее **sp_rda_reconcile_columns** не удалять столбцы из удаленной таблицы, существующие в удаленной таблице, но не в таблице SQL Server.
  
  > [!IMPORTANT]
  > Воссоздавая столбцы, случайно стертые из удаленной таблицы, процедура **sp_rda_reconcile_columns** не восстанавливает данные, которые прежде присутствовали в стертых столбцах.
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_rda_reconcile_columns @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>Аргументы  
 @objname = '*@objname*'  
 Имя таблицы с включенным Stretch SQL Server.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или >0 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Требуются права db_owner.  
   
## <a name="remarks"></a>Remarks  
 Если в удаленной таблице Azure есть столбцы, больше не существующие в таблице SQL Server с поддержкой Stretch, они не мешают нормальной работе Stretch Database. При желании вы можете удалить такие столбцы вручную.  
  
## <a name="example"></a>Пример  
 Для согласования столбцов в удаленной таблице Azure, выполните следующую инструкцию.  
  
```sql  
EXEC sp_rda_reconcile_columns @objname = N'StretchEnabledTableName';  
```  
  
  
