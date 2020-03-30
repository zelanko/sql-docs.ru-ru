---
title: STLength (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STLength (geography Data Type)
- STLength_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STLength method
ms.assetid: 774560ab-4a4a-4058-b043-1e67cf6fb9eb
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 61487b976322f8725f9398e54f8292919ff0ca58
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68139109"
---
# <a name="stlength-geography-data-type"></a>STLength (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает общую длину элементов в экземпляре **geography** или в экземплярах **geography** в коллекции **GeometryCollection**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STLength ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **float**  
  
 Тип возвращаемых данных CLR: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 Если экземпляр **geography** замкнут, его длина вычисляется как общая длина пути обхода экземпляра; длина любого многоугольника есть его периметр, а длина точки — 0. Длина коллекции **GeometryCollection** находится путем вычисления суммы длин всех экземпляров **geography**, содержащихся в коллекции.  
  
 STLength() работает и с допустимыми и с недопустимыми объектами LineString. Обычно LineString является недопустимым вследствие перекрывающихся сегментов, которые могут быть вызваны аномалиями, например неточными трассировками GPS. STLength() не удаляет перекрывающиеся или недопустимые сегменты. Он включает перекрывающиеся и недопустимые сегменты в возвращаемое значение длины. Метод MakeValid() может удалять перекрывающиеся сегменты из LineString.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `LineString` и используется метод `STLength()` для получения его длины.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STLength();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
