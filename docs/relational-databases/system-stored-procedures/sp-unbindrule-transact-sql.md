---
description: sp_unbindrule (Transact-SQL)
title: sp_unbindrule (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_unbindrule_TSQL
- sp_unbindrule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_unbindrule
ms.assetid: f54ee155-c3c9-4f1a-952e-632a8339f0cc
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 7ddf241acfb6e82e0cdd67315727017fb9965f77
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89547362"
---
# <a name="sp_unbindrule-transact-sql"></a>sp_unbindrule (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отменяет привязку правила к столбцу или псевдониму типа данных в текущей базе данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Рекомендуется создавать определения по умолчанию с помощью ключевого слова DEFAULT в инструкциях [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) или [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_unbindrule [ @objname = ] 'object_name'   
     [ , [ @futureonly = ] 'futureonly_flag' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @objname = ] 'object_name'` Имя таблицы, столбца или псевдонима типа данных, из которого не связано правило. *object_name* имеет тип **nvarchar (776)** и не имеет значения по умолчанию. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пытается вычислить по идентификаторам, состоящим из двух частей, сначала имена столбцов, а затем псевдонимы типов данных. При отмене привязки правила к псевдониму типа данных для всех столбцов этого типа данных, имеющих то же самое правило, также отменяется привязка. Столбцы этого типа данных с правилами, которые привязаны непосредственно к ним, не затрагиваются.  
  
> [!NOTE]  
>  *object_name* могут содержать квадратные скобки **[]** в качестве символов идентификатора с разделителями. Дополнительные сведения см. в разделе [Идентификаторы баз данных](../../relational-databases/databases/database-identifiers.md).  
  
`[ @futureonly = ] 'futureonly_flag'` Используется только при отмене привязки правила к псевдониму типа данных. *futureonly_flag* имеет тип **varchar (15)** и значение по умолчанию NULL. Когда *futureonly_flag* **futureonly**, существующие столбцы этого типа данных не теряют указанное правило.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Для отображения текста правила выполните процедуру **sp_helptext** с именем правила в качестве аргумента.  
  
 Если правило не привязано, сведения о привязке удаляются из таблицы **sys. Columns** , если правило привязано к столбцу, и из таблицы **sys. types** , если правило привязано к псевдониму типа данных.  
  
 Если отменяется привязка правила к псевдониму типа данных, то она отменяется и для всех столбцов, имеющих этот псевдоним. Правило также может быть привязано к столбцам, типы данных которых позднее изменились предложением ALTER COLUMN инструкции ALTER TABLE, необходимо отдельно отменить привязку правила к этим столбцам, используя **sp_unbindrule** и указав имя столбца.  
  
## <a name="permissions"></a>Разрешения  
 Чтобы отменить привязку правила к столбцу таблицы, требуется разрешение ALTER на таблицу. Чтобы отменить привязку правила к псевдониму типа данных, требуется разрешение CONTROL для типа или разрешение ALTER для схемы, которой тип принадлежит.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-unbinding-a-rule-from-a-column"></a>A. Отмена привязки правила к столбцу  
 В следующем примере отменяется привязка правила к столбцу `startdate` таблицы `employees`.  
  
```  
EXEC sp_unbindrule 'employees.startdate';  
```  
  
### <a name="b-unbinding-a-rule-from-an-alias-data-type"></a>Б. Отмена привязки правила к псевдониму типа данных  
 В следующем примере отменяется привязка правила к псевдониму типа данных `ssn`. Отмена производится как для существующих, так и для будущих столбцов этого типа.  
  
```  
EXEC sp_unbindrule ssn;  
```  
  
### <a name="c-using-futureonly_flag"></a>В. Использование futureonly_flag  
 В следующем примере отменяется привязка правила к псевдониму типа данных `ssn`, не затрагивая существующие столбцы типа `ssn`.  
  
```  
EXEC sp_unbindrule 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>Г. Использование идентификаторов с разделителями  
 В следующем примере показано использование идентификаторов с разделителями в параметре *object_name* .  
  
```  
CREATE TABLE [t.4] (c1 int); -- Notice the period as part of the table   
-- name.  
GO  
CREATE RULE rule2 AS @value > 100;  
GO  
EXEC sp_bindrule rule2, '[t.4].c1' -- The object contains two   
-- periods; the first is part of the table name and the second   
-- distinguishes the table name from the column name.  
GO  
EXEC sp_unbindrule '[t.4].c1';  
```  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE RULE (Transact-SQL)](../../t-sql/statements/create-rule-transact-sql.md)   
 [DROP RULE (Transact-SQL)](../../t-sql/statements/drop-rule-transact-sql.md)   
 [sp_bindrule (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md)   
 [sp_helptext (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
