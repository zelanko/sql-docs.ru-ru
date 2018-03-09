---
title: "UPDATE() (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UPDATE()_TSQL
- UPDATE()
dev_langs:
- TSQL
helpviewer_keywords:
- INSERT statement [SQL Server], UPDATE function
- testing column updates
- UPDATE function
- UPDATE() function
- detecting changes
- columns [SQL Server], change detection
- UPDATE statement [SQL Server], UPDATE function
- verifying column updates
- checking column updates
ms.assetid: 8e3be25b-2e3b-4d1f-a610-dcbbd8d72084
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6d5b93a4f98e382ccb6504e1d20d6e974a031f86
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="update---trigger-functions-transact-sql"></a>UPDATE - функции триггера (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает логическое значение, указывающее на попытку применить функцию INSERT или UPDATE к указанному столбцу таблицы или представлению. UPDATE() используется в любом месте внутри тела триггера [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT или UPDATE, чтобы проверить необходимость выполнения определенных действий.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
UPDATE ( column )   
```  
  
## <a name="arguments"></a>Аргументы  
 *столбец*  
 Это имя столбца для проверки на действие INSERT или UPDATE. Так как имя столбца указано в предложении триггера ON, не ставьте имя таблицы перед именем столбца. Столбец может быть любым [тип данных](../../t-sql/data-types/data-types-transact-sql.md) поддерживается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Однако вычисляемые столбцы не могут использоваться в данном контексте.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Логическое значение  
  
## <a name="remarks"></a>Замечания  
 Функция UPDATE() возвращает TRUE независимо от того, была ли попытка применить операторы INSERT или UPDATE удачной.  
  
 Чтобы проверить действие INSERT или UPDATE для нескольких столбцов, задать отдельное обновление (*столбца*) первое предложение. Несколько столбцов также могут быть проверены на действие INSERT или UPDATE при помощи COLUMNS_UPDATED. В результате возвращается битовый шаблон, который указывает на то, какие столбцы были вставлены или обновлены.  
  
 IF UPDATE возвращает значение TRUE по действиям оператора INSERT, так как столбцы содержат либо явные вставленные значения, либо неявные вставленные значения (NULL).  
  
> [!NOTE]  
>  IF UPDATE (*столбцы*n) предложение действует так же, как если, если... ELSE или WHILE и могут использовать BEGIN... КОНЕЧНЫЙ блок. Дополнительные сведения см. в разделе [языка управления потоком &#40; Transact-SQL &#41; ](~/t-sql/language-elements/control-of-flow.md).  
  
 ОБНОВЛЕНИЕ (*столбца*) может использоваться в любом месте внутри тела [!INCLUDE[tsql](../../includes/tsql-md.md)] триггера.  
  
## <a name="examples"></a>Примеры  
 Следующий пример создает триггер, который выдает сообщение клиенту при попытке обновить столбец `StateProvinceID` или `PostalCode` в таблице `Address`.  
  
```  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT name FROM sys.objects  
      WHERE name = 'reminder' AND type = 'TR')  
   DROP TRIGGER Person.reminder;  
GO  
CREATE TRIGGER reminder  
ON Person.Address  
AFTER UPDATE   
AS   
IF ( UPDATE (StateProvinceID) OR UPDATE (PostalCode) )  
BEGIN  
RAISERROR (50009, 16, 10)  
END;  
GO  
-- Test the trigger.  
UPDATE Person.Address  
SET PostalCode = 99999  
WHERE PostalCode = '12345';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Функция COLUMNS_UPDATED &#40; Transact-SQL &#41;](../../t-sql/functions/columns-updated-transact-sql.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)  
  
  
