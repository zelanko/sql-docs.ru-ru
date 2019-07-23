---
title: STIsValid (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIsValid (geometry Data Type)
- STIsValid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STIsValid (geometry Data Type)
ms.assetid: 6da39bea-0f67-4660-98fc-d7214f9b2138
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 3aa054a04b236c419b833df42ba668926e97e312
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68030872"
---
# <a name="stisvalid-geometry-data-type"></a>STIsValid (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает значение true, если экземпляр **geometry** является экземпляром правильного формата на основе соответствующего типа OGC. Возвращает значение false, если экземпляр **geometry** является экземпляром недопустимого формата.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STIsValid ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Тип возвращаемого значения CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Тип OGC экземпляра **geometry** можно определить с помощью метода [STGeometryType()](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует только допустимые экземпляры **geometry**, однако позволяет хранить и получать недопустимые экземпляры. Допустимый экземпляр, представляющий тот же набор точек, что и любой недопустимый экземпляр, может быть получен с помощью метода `MakeValid()`.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `geometry` и используется метод `STIsValid()`, чтобы проверить, допустим ли экземпляр.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STIsValid();  
```  
  
## <a name="see-also"></a>См. также:  
 [STGeometryType (тип данных geometry)](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)   
 [MakeValid (тип данных geometry)](../../t-sql/spatial-geometry/makevalid-geometry-data-type.md)   
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

