---
title: '@@CURSOR_ROWS (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
manager: craigg
ms.openlocfilehash: a608d12c790b9b9808ef0f1d84264f1423ba472b
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="x40x40cursorrows-transact-sql"></a>&#x40;&#x40;CURSOR_ROWS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает число выбранных строк, имеющихся в последнем открытом курсоре в данном соединении. Для повышения производительности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может выполнять заполнение большого набора ключей и статических курсоров асинхронно. Функцию `@@CURSOR_ROWS` можно вызвать для определения того, получено ли количество строк, определенных для курсора, во время вызова @@CURSOR_ROWS.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```
@@CURSOR_ROWS  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных
**integer**
  
## <a name="return-value"></a>Возвращаемое значение  
  
|Возвращаемое значение|Описание|  
|---|---|
|-*m*|Курсор заполняется асинхронно. Возвращаемое значение (–*m*) является текущим числом строк в наборе ключей.|  
|-1|Курсор является динамическим. Так как динамический курсор отражает все изменения, количество строк для курсора постоянно изменяется. Курсор не обязательно извлекает все определенные строки.|  
|0|Ни один курсор не был открыт, не было строк для последнего открытого курсора или последний открытый курсор закрыт или освобожден.|  
|*n*|Курсор полностью заполнен. Возвращенное значение (*n*) является общим количеством строк в курсоре.|  
  
## <a name="remarks"></a>Remarks  
`@@CURSOR_ROWS` возвращает отрицательное число, если последний курсор был открыт асинхронно. Управляемые набором ключей или статические курсоры открываются асинхронно, если значение параметра cursor threshold процедуры sp_configure больше 0, а количество строк в результирующем наборе курсора больше, чем пороговое значение курсора.
  
## <a name="examples"></a>Примеры  
В приведенном ниже примере объявляется курсор и выполняется инструкция `SELECT` для вывода на экран значения `@@CURSOR_ROWS`. Параметр имеет значение `0` перед открытием курсора, а затем принимает значение `-1`, которое указывает на то, что набор ключей курсора заполняется асинхронно.
  
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
  
## <a name="see-also"></a>См. также раздел
[Функции работы с курсорами (Transact-SQL)](../../t-sql/functions/cursor-functions-transact-sql.md)  
[OPEN (Transact-SQL)](../../t-sql/language-elements/open-transact-sql.md)
  
  
