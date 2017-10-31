---
title: "Чтение (компонент Database Engine) | Документы Microsoft"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Read_TSQL
- Read
dev_langs:
- TSQL
helpviewer_keywords:
- Read [Database Engine]
ms.assetid: f2b8207c-b69f-4327-a874-100b3a1f27d8
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 21f27c627a36f747d9e3ecbb52d14d1ac6bc5d28
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="read-database-engine"></a>Read (компонент Database Engine)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Чтение считывает двоичное представление **SqlHierarchyId** из переданного **BinaryReader** и задает **SqlHierarchyId** это значение объекту. Чтение не может вызываться с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]. Пользуйтесь вместо этого инструкцией CAST или CONVERT.
  
## <a name="syntax"></a>Синтаксис  
  
```sql
void Read( BinaryReader r )   
```  
  
## <a name="arguments"></a>Аргументы  
*r*  
 **BinaryReader** объект, который формирует двоичный поток, соответствующий двоичное представление **hierarchyid** узла.  
  
## <a name="return-types"></a>Возвращаемые типы
 **Возвращаемый тип CLR: void**  
  
## <a name="remarks"></a>Замечания  
 Чтение не выполняет проверку входных данных. Если указан недопустимый входных данных binary чтения может вызвать исключение. Или он может быть успешным с выдачей недопустимого **SqlHierarchyId** объекту, методы которого выдают непредсказуемые результаты или вызывают исключение.  
  
 Чтения может быть вызван только на вновь созданный **SqlHierarchyId** объекта.  
  
 Чтение, используются внутренними механизмами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] когда это необходимо, например, при записи данных в **hierarchyid** столбца. Чтение также можно вызвать изнутри, когда преобразование между **varbinary** и **hierarchyid**.  
  
## <a name="examples"></a>Примеры  
  
```sql
Byte[] encoding = new byte[] { 0x58 };  
MemoryStream stream = new MemoryStream(encoding, false /*not writable*/);  
BinaryReader br = new BinaryReader(stream);  
SqlHierarchyId hid = new SqlHierarchyId();  
hid.Read(br);   
```  
  
## <a name="see-also"></a>См. также:  
[Запись &#40; компонент Database Engine &#41;](../../t-sql/data-types/write-database-engine.md)  
[ToString &#40; компонент Database Engine &#41;](../../t-sql/data-types/tostring-database-engine.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Справочник по методам типа данных hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  

