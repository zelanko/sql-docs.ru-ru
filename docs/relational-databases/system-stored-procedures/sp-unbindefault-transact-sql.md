---
description: Хранимая процедура sp_unbindefault (Transact-SQL)
title: sp_unbindefault (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_unbindefault_TSQL
- sp_unbindefault
dev_langs:
- TSQL
helpviewer_keywords:
- sp_unbindefault
ms.assetid: c96a6c5e-f3ca-4c1e-b64b-0d8ef6986af8
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b8a0ee77c73c6edcee17d6baad363c6c02eb52c3
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543013"
---
# <a name="sp_unbindefault-transact-sql"></a>Хранимая процедура sp_unbindefault (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отменяет привязку или удаляет значение по умолчанию из столбца или псевдонима типа данных в текущей базе данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Рекомендуется создавать определения по умолчанию с помощью ключевого слова DEFAULT в инструкциях [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) или [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_unbindefault [ @objname = ] 'object_name'   
     [ , [ @futureonly = ] 'futureonly_flag' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @objname = ] 'object_name'` Имя таблицы, столбца или псевдонима типа данных, из которого будет отменена привязка по умолчанию. *object_name* имеет тип **nvarchar (776)** и не имеет значения по умолчанию. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пытается вычислить по идентификаторам, состоящим из двух частей, сначала имена столбцов, а затем псевдонимы типов данных.  
  
 При отмене привязки для псевдонима типа данных привязка также отменяется для всех столбцов этого типа данных, имеющих такое же значение по умолчанию. Столбцы с этим типом данных, имеющие непосредственную привязку значений по умолчанию, не затрагиваются.  
  
> [!NOTE]  
>  *object_name* могут содержать квадратные скобки **[]** в качестве символов идентификатора с разделителями. Дополнительные сведения см. в разделе [Идентификаторы баз данных](../../relational-databases/databases/database-identifiers.md).  
  
`[ @futureonly = ] 'futureonly_flag'` Используется только при отмене привязки значения по умолчанию к псевдониму типа данных. *futureonly_flag* имеет тип **varchar (15)** и значение по умолчанию NULL. Если *futureonly_flag* **futureonly**, существующие столбцы типа данных не теряют указанное значение по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Чтобы отобразить текст значения по умолчанию, выполните **sp_helptext** с именем по умолчанию в качестве параметра.  
  
## <a name="permissions"></a>Разрешения  
 Для отмены привязки значения по умолчанию в столбце таблицы требуется разрешение ALTER для этой таблицы. Для отмены привязки значения по умолчанию в псевдониме типа данных требуется разрешение CONTROL на этот тип или разрешение ALTER для схемы, которой принадлежит этот тип.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-unbinding-a-default-from-a-column"></a>A. Отмена привязки значения по умолчанию в столбце  
 В следующем примере отменяется привязка значения по умолчанию в столбце `hiredate` таблицы `employees`.  
  
```  
EXEC sp_unbindefault 'employees.hiredate';  
```  
  
### <a name="b-unbinding-a-default-from-an-alias-data-type"></a>Б. Отмена привязки значения по умолчанию для псевдонима типа данных  
 В следующем примере отменяется привязка значения по умолчанию для псевдонима типа данных `ssn`. Отменяется привязка существующих и будущих столбцов этого типа.  
  
```  
EXEC sp_unbindefault 'ssn';  
```  
  
### <a name="c-using-the-futureonly_flag"></a>В. Использование аргумента futureonly_flag  
 Следующий пример отменяет привязку использования в будущем псевдонима типа данных `ssn`, не затрагивая существующие столбцы `ssn`.  
  
```  
EXEC sp_unbindefault 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>Г. Использование идентификаторов с разделителями  
 В следующем примере показано использование идентификаторов с разделителями в параметре *object_name* .  
  
```  
CREATE TABLE [t.3] (c1 int); -- Notice the period as part of the table   
-- name.  
CREATE DEFAULT default2 AS 0;  
GO  
EXEC sp_bindefault 'default2', '[t.3].c1' ;  
-- The object contains two periods;  
-- the first is part of the table name and the second   
-- distinguishes the table name from the column name.  
EXEC sp_unbindefault '[t.3].c1';  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE DEFAULT (Transact-SQL)](../../t-sql/statements/create-default-transact-sql.md)   
 [DROP DEFAULT (Transact-SQL)](../../t-sql/statements/drop-default-transact-sql.md)   
 [sp_bindefault (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)   
 [sp_helptext (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
