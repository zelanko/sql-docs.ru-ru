---
title: STLength (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STLength_TSQL
- STLength (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STLength (geometry Data Type)
ms.assetid: e34dc620-2a65-4248-b099-fff91830ab98
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 39e20be532250bf4a18ad64b97d47f8d42783202
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38048578"
---
# <a name="stlength-geometry-data-type"></a>STLength (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает общую длину элементов в экземпляре **geometry**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STLength ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **float**  
  
 Тип возвращаемых данных CLR: **SqlDouble**  
  
## <a name="remarks"></a>Примечания  
 Если экземпляр **geometry** замкнут, его длина вычисляется как общая длина пути обхода экземпляра; длина любого многоугольника есть его периметр, а длина точки — 0. Размер любого типа **geometrycollection** находится путем вычисления суммы размеров всех содержащихся в нем экземпляров **geometry**.  
  
 STLength() работает и с допустимыми и с недопустимыми объектами LineString. Обычно LineString является недопустимым вследствие перекрывающихся сегментов, которые могут быть вызваны аномалиями, например неточными трассировками GPS. STLength() не удаляет перекрывающиеся или недопустимые сегменты. Он включает перекрывающиеся и недопустимые сегменты в возвращаемое значение длины. Метод MakeValid() может удалять перекрывающиеся сегменты из LineString.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `LineString` и используется метод `STLength()` для получения его длины.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STLength();  
```  
  
## <a name="see-also"></a>См. также  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

