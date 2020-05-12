---
title: UPDATE() (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 9845829065b8bafe2f70f7bad8849c631f0a5fb3
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826776"
---
# <a name="update---trigger-functions-transact-sql"></a>Функции триггера — UPDATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает логическое значение, указывающее на попытку применить функцию INSERT или UPDATE к указанному столбцу таблицы или представлению. UPDATE() используется в любом месте внутри тела триггера [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT или UPDATE, чтобы проверить необходимость выполнения определенных действий.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
  
UPDATE ( column )   
```  
  
## <a name="arguments"></a>Аргументы  
 *column*  
 Это имя столбца для проверки на действие INSERT или UPDATE. Так как имя столбца указано в предложении триггера ON, не ставьте имя таблицы перед именем столбца. Столбец может иметь любой [тип данных](../../t-sql/data-types/data-types-transact-sql.md), поддерживаемый [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Однако вычисляемые столбцы не могут использоваться в данном контексте.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Логическое  
  
## <a name="remarks"></a>Remarks  
 Функция UPDATE() возвращает TRUE независимо от того, была ли попытка применить операторы INSERT или UPDATE удачной.  
  
 Чтобы проверить действие операторов INSERT или UPDATE для нескольких столбцов, укажите отдельно предложение UPDATE(*column*), следующее за первым предложением. Несколько столбцов также могут быть проверены на действие INSERT или UPDATE при помощи COLUMNS_UPDATED. В результате возвращается битовый шаблон, который указывает на то, какие столбцы были вставлены или обновлены.  
  
 IF UPDATE возвращает значение TRUE по действиям оператора INSERT, так как столбцы содержат либо явные вставленные значения, либо неявные вставленные значения (NULL).  
  
> [!NOTE]  
>  Функции предложения IF UPDATE(*column*) аналогичны предложениям IF, IF...ELSE или WHILE и могут использовать блок BEGIN...END. Дополнительные сведения см. в разделе [Язык управления потоком (Transact-SQL)](~/t-sql/language-elements/control-of-flow.md).  
  
 UPDATE(*column*) может применяться в любой части текста триггера [!INCLUDE[tsql](../../includes/tsql-md.md)].  
 
Если триггер применяется к столбцу, значение `UPDATED` будет возвращаться в виде `true` или `1`, даже если значение столбца остается неизменным. Это нормальное поведение, и триггер должен реализовывать бизнес-логику, которая определяет, допустимы ли операции вставки, обновления и удаления. 
  
## <a name="examples"></a>Примеры  
 Следующий пример создает триггер, который выдает сообщение клиенту при попытке обновить столбец `StateProvinceID` или `PostalCode` в таблице `Address`.  
  
```sql  
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
 [COLUMNS_UPDATED (Transact-SQL)](../../t-sql/functions/columns-updated-transact-sql.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)  
  
  
