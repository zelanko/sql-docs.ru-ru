---
title: Write (ядро СУБД) | Документы Майкрософт
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Write_TSQL
- Write
dev_langs:
- TSQL
helpviewer_keywords:
- Write [Database Engine]
ms.assetid: 7c554334-d2d9-4eae-a4ae-097aa4020e1a
caps.latest.revision: 13
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d5976050ef20e2f6d63aa6e6d121a7b05229d724
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37429755"
---
# <a name="write-database-engine"></a>Write (компонент Database Engine)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Write записывает двоичное представление идентификатора **SqlHierarchyId** в передаваемый на входе объект **BinaryWriter**. Write невозможно вызвать с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]. Пользуйтесь вместо этого инструкцией CAST или CONVERT.
  
## <a name="syntax"></a>Синтаксис  
  
```sql
void Write( BinaryWriter w )   
```  
  
## <a name="arguments"></a>Аргументы  
*w*  
Объект **BinaryWriter**, в который будет записано двоичное представление этого узла **hierarchyid**.
  
## <a name="return-types"></a>Типы возвращаемых данных  
**Возвращаемый тип CLR:void**
  
## <a name="remarks"></a>Remarks  
При необходимости Write используется в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для внутренних целей, например при загрузке данных из столбца **hierarchyid**. Write также используется для внутренних целей, когда выполняется преобразование между **hierarchyid** и **varbinary**.
  
## <a name="examples"></a>Примеры  
  
```sql
MemoryStream stream = new MemoryStream();  
BinaryWriter bw = new BinaryWriter(stream);  
hid.Write(bw);  
byte[] encoding = stream.ToArray();  
  
```  
  
## <a name="see-also"></a>См. также раздел
[Read (ядро СУБД)](../../t-sql/data-types/read-database-engine.md)  
[ToString (ядро СУБД)](../../t-sql/data-types/tostring-database-engine.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Справочник по методам типа данных hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  
