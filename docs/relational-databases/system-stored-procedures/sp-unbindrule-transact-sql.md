---
title: "sp_unbindrule (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_unbindrule_TSQL
- sp_unbindrule
dev_langs: TSQL
helpviewer_keywords: sp_unbindrule
ms.assetid: f54ee155-c3c9-4f1a-952e-632a8339f0cc
caps.latest.revision: "34"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0bc157565f86eaa3490240cb6c1e71523741ff23
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spunbindrule-transact-sql"></a>sp_unbindrule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отменяет привязку правила к столбцу или псевдониму типа данных в текущей базе данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]Рекомендуется создавать определения по умолчанию с помощью ключевого слова DEFAULT в [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) или [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) инструкции вместо него.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_unbindrule [ @objname = ] 'object_name'   
     [ , [ @futureonly = ] 'futureonly_flag' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@objname=** ] **"***object_name***"**  
 Имя таблицы и столбца или псевдоним типа данных, для которого отменяется привязка правила. *object_name* — **nvarchar(776)**, не имеет значения по умолчанию. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пытается вычислить по идентификаторам, состоящим из двух частей, сначала имена столбцов, а затем псевдонимы типов данных. При отмене привязки правила к псевдониму типа данных для всех столбцов этого типа данных, имеющих то же самое правило, также отменяется привязка. Столбцы этого типа данных с правилами, которые привязаны непосредственно к ним, не затрагиваются.  
  
> [!NOTE]  
>  *object_name* может содержать квадратные скобки **[]** качестве символов идентификатора с разделителем. Дополнительные сведения см. в разделе [Database Identifiers](../../relational-databases/databases/database-identifiers.md).  
  
 [  **@futureonly=** ] **"***аргумента futureonly_flag***"**  
 Используется только при отмене привязки правила к псевдониму типа данных. *Аргумент futureonly_flag* — **varchar(15)**, значение по умолчанию NULL. Когда *аргумента futureonly_flag* — **futureonly**, существующие столбцы этого типа данных не теряют указанного правила.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Для отображения текста правила выполните **sp_helptext** с именем правила в качестве параметра.  
  
 Если отменяется привязка правила, сведения о привязке, удаляется из **sys.columns** таблица, если правило было привязано к столбцу, а также из **sys.types** таблица, если правило было привязано к псевдониму типа данных.  
  
 Если отменяется привязка правила к псевдониму типа данных, то она отменяется и для всех столбцов, имеющих этот псевдоним. Правило по-прежнему могут быть привязаны к столбцам, типы данных которых изменены позже с помощью предложения ALTER COLUMN инструкции ALTER TABLE, необходимо специально отменить привязку правила из этих столбцов с помощью **sp_unbindrule** и указания Имя столбца.  
  
## <a name="permissions"></a>Permissions  
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
  
### <a name="c-using-futureonlyflag"></a>В. Использование futureonly_flag  
 В следующем примере отменяется привязка правила к псевдониму типа данных `ssn`, не затрагивая существующие столбцы типа `ssn`.  
  
```  
EXEC sp_unbindrule 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>Г. Использование идентификаторов с разделителями  
 В следующем примере показано использование идентификаторов с разделителями в *object_name* параметра.  
  
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
 [Компонент Database Engine хранимой процедуры &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE RULE (Transact-SQL)](../../t-sql/statements/create-rule-transact-sql.md)   
 [УДАЛИТЬ правило &#40; Transact-SQL &#41;](../../t-sql/statements/drop-rule-transact-sql.md)   
 [sp_bindrule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md)   
 [sp_helptext (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
