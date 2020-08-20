---
description: Read (ядро СУБД) с CSharp
title: Read (ядро СУБД) | Документы Майкрософт
ms.custom: ''
ms.date: 04/16/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Read_TSQL
- Read
dev_langs:
- TSQL
helpviewer_keywords:
- Read [Database Engine]
ms.assetid: f2b8207c-b69f-4327-a874-100b3a1f27d8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1fa01bbaa018e53bba906a0c2b9b53d8b75df02d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88479906"
---
# <a name="read-database-engine-by-using-csharp"></a>Read (ядро СУБД) с CSharp
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Метод Read считывает двоичное представление значения **SqlHierarchyId** из переданного объекта **BinaryReader** и присваивает это значение объекту **SqlHierarchyId**. Метод Read невозможно вызвать с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]. Пользуйтесь вместо этого инструкцией CAST или CONVERT.
  
## <a name="syntax"></a>Синтаксис  

<!--
This is not T-SQL, despite the ```sql colorizer specified.
Neither should this be ```syntaxsql.
Rather, this is C# (or C# syntax).  Same for the later code blocks.
I am making this fix now, from ```sql to ```cs, on 2020/04/16.  GeneMi.
-->

```csharp
void Read( BinaryReader r )   
```  

## <a name="arguments"></a>Аргументы
*r*  
 Объект **BinaryReader**, который формирует двоичный поток, соответствующий двоичному представлению узла **hierarchyid**.  
  
## <a name="return-types"></a>Типы возвращаемых данных
 **Возвращаемый тип CLR:void**  
  
## <a name="remarks"></a>Remarks  
 Входные данные метода Read не проверяются. Если двоичные входные данные недопустимы, то метод Read может вызвать исключение. Его выполнение также может завершиться успешно, причем будет создан недопустимый объект **SqlHierarchyId**, методы которого будут давать непредсказуемые результаты или вызывать исключение.  
  
 Метод Read можно вызывать только для новых объектов **SqlHierarchyId**.  
  
 Метод Read используется в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для внутренних целей, например при записи данных в столбец **hierarchyid**. Read также вызывается для внутренних целей, когда выполняется преобразование между **varbinary** и **hierarchyid**.  
  
## <a name="examples"></a>Примеры  
  
```csharp
Byte[] encoding = new byte[] { 0x58 };  
MemoryStream stream = new MemoryStream(encoding, false /*not writable*/);  
BinaryReader br = new BinaryReader(stream);  
SqlHierarchyId hid = new SqlHierarchyId();  
hid.Read(br);   
```  
  
## <a name="see-also"></a>См. также:  
[Write (ядро СУБД)](../../t-sql/data-types/write-database-engine.md)  
[ToString (ядро СУБД)](../../t-sql/data-types/tostring-database-engine.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Справочник по методам типа данных hierarchyid](https://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  
