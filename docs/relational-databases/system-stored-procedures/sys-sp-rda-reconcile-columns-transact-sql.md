---
title: sys. sp_rda_reconcile_columns (Transact-SQL) | Документация Майкрософт
description: Дополнительные сведения о sys. sp_rda_reconcile_columns. Используйте эту хранимую процедуру для согласования столбцов в удаленных таблицах Azure и таблицах SQL Server с поддержкой растяжения.
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_columns
- sys.sp_rda_reconcile_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_columns stored procedure
ms.assetid: 60d9cc4e-1828-450b-9d88-5b8485800d73
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 939bc5cbe299ce144b8617391fd33d740011b08a
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245751"
---
# <a name="syssp_rda_reconcile_columns-transact-sql"></a>sys. sp_rda_reconcile_columns (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Согласовывает столбцы в удаленной таблице Azure со столбцами в таблице SQL Server с поддержкой растяжения.  
    
  **sp_rda_reconcile_columns** добавляет столбцы в удаленную таблицу, которая существует в таблице SQL Server с поддержкой растяжения, но не в удаленной таблице. Эти столбцы могут быть столбцами, которые были случайно удалены из удаленной таблицы. Однако **sp_rda_reconcile_columns** не удаляет столбцы из удаленной таблицы, которая существует в удаленной таблице, но не в таблице SQL Server.
  
  > [!IMPORTANT]
  > Воссоздавая столбцы, случайно стертые из удаленной таблицы, процедура **sp_rda_reconcile_columns** не восстанавливает данные, которые прежде присутствовали в стертых столбцах.
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_rda_reconcile_columns @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>Аргументы  
 \@objname = '* \@ objname*'  
 Имя таблицы SQL Server с поддержкой растяжения.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или >0 (сбой)  
  
## <a name="permissions"></a>Разрешения  
 Требуются db_owner разрешения.  
   
## <a name="remarks"></a>Remarks  
 Если в удаленной таблице Azure есть столбцы, которых больше нет в таблице SQL Server с поддержкой Stretch Database, эти лишние столбцы не препятствуют нормальной работе службы Stretch Database. При желании вы можете удалить такие столбцы вручную.  
  
## <a name="example"></a>Пример  
 Чтобы согласовать столбцы в удаленной таблице Azure, выполните следующую инструкцию.  
  
```sql  
EXEC sp_rda_reconcile_columns @objname = N'StretchEnabledTableName';  
```  
  
  
