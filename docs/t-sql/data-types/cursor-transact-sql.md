---
title: "курсор (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- cursor data type
ms.assetid: fbea16ef-f2cc-4734-9149-ec2598fd3cca
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4b0b96a3bc147f51102fa10f2dff96b7f1761759
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="cursor-transact-sql"></a>cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Тип данных для переменных или выходных параметров хранимых процедур, которые содержат ссылку на курсор.
  
## <a name="remarks"></a>Замечания  
Операции, которые могут ссылаться на переменные и параметрами, имеющими **курсор** , тип данных:
-   DECLARE  *@local_variable*  , а  *@local_variable*  инструкции.  
-   Инструкции над курсором OPEN, FETCH, CLOSE и DEALLOCATE.  
-   Выходные параметры хранимой процедуры.  
-   Функция CURSOR_STATUS.  
-   **Sp_cursor_list**, **sp_describe_cursor**, **sp_describe_cursor_tables**, и **sp_describe_cursor_columns** системные хранимые процедуры.  
  
**Cursor_name** выходной столбец **sp_cursor_list** и **sp_describe_cursor** возвращает имя переменной курсора.
  
Любая переменная, созданная с **курсор** тип данных допускает значения NULL.
  
**Курсор** тип данных не может использоваться для столбца в инструкции CREATE TABLE.
  
## <a name="see-also"></a>См. также:
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CURSOR_STATUS &#40; Transact-SQL &#41;](../../t-sql/functions/cursor-status-transact-sql.md)  
[Преобразование типов данных &#40; компонент Database Engine &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE CURSOR &#40; Transact-SQL &#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  

