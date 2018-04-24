---
title: cursor (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- cursor data type
ms.assetid: fbea16ef-f2cc-4734-9149-ec2598fd3cca
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 083e748e9b0f01bb9c1e7386a7e35b345b1ffd5e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="cursor-transact-sql"></a>cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Тип данных для переменных или выходных параметров хранимых процедур, которые содержат ссылку на курсор.
  
## <a name="remarks"></a>Remarks  
Операции, которые могут выполняться с переменными и параметрами, имеющими тип данных **cursor**:
-   Инструкции DECLARE *@local_variable* и SET *@local_variable*.  
-   Инструкции над курсором OPEN, FETCH, CLOSE и DEALLOCATE.  
-   Выходные параметры хранимой процедуры.  
-   Функция CURSOR_STATUS.  
-   Системные хранимые процедуры **sp_cursor_list**, **sp_describe_cursor**, **sp_describe_cursor_tables** и **sp_describe_cursor_columns**.  
  
Выходной столбец **cursor_name** хранимых процедур **sp_cursor_list** и **sp_describe_cursor** возвращает имя переменной курсора.
  
Любая переменная, созданная с типом данных **cursor**, может принимать значение NULL.
  
Тип данных **cursor** не может использоваться для столбца в операторе CREATE TABLE.
  
## <a name="see-also"></a>См. также раздел
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CURSOR_STATUS (Transact-SQL)](../../t-sql/functions/cursor-status-transact-sql.md)  
[Преобразование типов данных (ядро СУБД)](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE CURSOR (Transact-SQL)](../../t-sql/language-elements/declare-cursor-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  
