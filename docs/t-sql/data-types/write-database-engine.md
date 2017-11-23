---
title: "Write (компонент Database Engine) | Документы Microsoft"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Write_TSQL
- Write
dev_langs: TSQL
helpviewer_keywords: Write [Database Engine]
ms.assetid: 7c554334-d2d9-4eae-a4ae-097aa4020e1a
caps.latest.revision: "13"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 11980f26c4af4a2dabb57e5cce242d7e89028d16
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="write-database-engine"></a>Write (компонент Database Engine)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Записи записывает двоичное представление **SqlHierarchyId** на переданный **BinaryWriter**. Записи не может вызываться с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]. Пользуйтесь вместо этого инструкцией CAST или CONVERT.
  
## <a name="syntax"></a>Синтаксис  
  
```sql
void Write( BinaryWriter w )   
```  
  
## <a name="arguments"></a>Аргументы  
*w*  
Объект **BinaryWriter** объекта, к которому двоичное представление **hierarchyid** узел будет записано.
  
## <a name="return-types"></a>Типы возвращаемых значений  
**Возвращаемый тип CLR: void**
  
## <a name="remarks"></a>Замечания  
Записи, используются внутренними механизмами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] когда это необходимо, например, при загрузке данных из **hierarchyid** столбца. Записи также можно вызвать изнутри, когда преобразование между **hierarchyid** и **varbinary**.
  
## <a name="examples"></a>Примеры  
  
```sql
MemoryStream stream = new MemoryStream();  
BinaryWriter bw = new BinaryWriter(stream);  
hid.Write(bw);  
byte[] encoding = stream.ToArray();  
  
```  
  
## <a name="see-also"></a>См. также:
[Чтение &#40; компонент Database Engine &#41;](../../t-sql/data-types/read-database-engine.md)  
[ToString &#40; компонент Database Engine &#41;](../../t-sql/data-types/tostring-database-engine.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Справочник по методам типа данных hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  
