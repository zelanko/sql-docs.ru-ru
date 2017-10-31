---
title: "@@CURSOR_ROWS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@CURSOR_ROWS'
- '@@CURSOR_ROWS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@CURSOR_ROWS function'
- cursors [SQL Server], last-opened
- last-opened cursor
- asynchronous cursors [SQL Server]
ms.assetid: 31bd7a97-7f28-42a8-ba24-24d16d22973d
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 10a3a6cabae8d25de670cbacb037a62f4c5a2d54
ms.contentlocale: ru-ru
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40cursorrows-transact-sql"></a>& #x 40; & #x 40; CURSOR_ROWS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает число выбранных строк, имеющихся в последнем открытом курсоре в данном соединении. Для повышения производительности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может выполнять заполнение большого набора ключей и статических курсоров асинхронно. @@CURSOR_ROWS можно вызвать, чтобы определить, что количество строк, определенных для курсора получено во время вызова @@CURSOR_ROWS вызывается.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```
@@CURSOR_ROWS  
```  
  
## <a name="return-types"></a>Возвращаемые типы
**integer**
  
## <a name="return-value"></a>Возвращаемое значение  
  
|Возвращаемое значение|Description|  
|---|---|
|-*m*|Курсор заполнен асинхронно. Возвращаемое значение (-*m*) — число строк в наборе ключей.|  
|-1|Курсор является динамическим. Так как динамический курсор отражает все изменения, количество строк для курсора постоянно изменяется. Никогда не может быть точно определено, что все отмеченные строки были получены.|  
|0|Ни один курсор не был открыт, не было строк для последнего открытого курсора или последний открытый курсор закрыт или освобожден.|  
|*n*|Курсор полностью заполнен. Возвращаемое значение (*n*) — общее количество строк в курсоре.|  
  
## <a name="remarks"></a>Замечания  
Число, возвращенное@CURSOR_ROWS является отрицательным, если последний курсор открыт асинхронно. Управляемые набором ключей или статические курсоры открываются асинхронно, если значение параметра хранимой процедуры sp_configure cursor threshold больше 0 и количество строк в результирующем наборе курсора больше, чем пороговое значение курсора.
  
## <a name="examples"></a>Примеры  
В следующем примере определяется курсор и выполняется инструкция `SELECT` для вывода на экран значения `@@CURSOR_ROWS`. Эта настройка имеет значение `0` перед открытием курсора; значение `-1` указывает на то, что набор ключей курсора заполняется асинхронно.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT @@CURSOR_ROWS;  
DECLARE Name_Cursor CURSOR FOR  
SELECT LastName ,@@CURSOR_ROWS FROM Person.Person;  
OPEN Name_Cursor;  
FETCH NEXT FROM Name_Cursor;  
SELECT @@CURSOR_ROWS;  
CLOSE Name_Cursor;  
DEALLOCATE Name_Cursor;  
GO             
```  
  
Ниже приведены результирующие наборы.
  
```
-----------
0  
```

```
LastName
---------------
Sanchez
```

```
-----------
-1
```  
  
## <a name="see-also"></a>См. также:
[Функции работы с курсорами &#40; Transact-SQL &#41;](../../t-sql/functions/cursor-functions-transact-sql.md)  
[ОТКРЫТЬ &#40; Transact-SQL &#41;](../../t-sql/language-elements/open-transact-sql.md)
  
  

