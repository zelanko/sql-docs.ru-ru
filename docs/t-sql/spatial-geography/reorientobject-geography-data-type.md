---
title: ReorientObject (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ReorientObject
- ReorientObject_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ReorientObject method (geography)
ms.assetid: e2a1a4f1-211b-4e82-abed-03fc7140a83c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cda6f09124127d04c8ded1773feab4e9ffbf2ba9
ms.sourcegitcommit: 01e17c5f1710e7058bad8227c8011985a9888d36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265231"
---
# <a name="reorientobject-geography-data-type"></a>ReorientObject (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Возвращает экземпляр **geography** со взаимозаменяемыми внутренними и внешними областями.  
  
Этот метод типа данных **geography** поддерживает экземпляры **FullGlobe** или пространственные экземпляры, размер которых больше полушария.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.ReorientObject (geography)  
```  
  
## <a name="arguments"></a>Аргументы  
_geography_  
Другой экземпляр **geography**, для которого вызван метод `ReorientObject()`.  
  
## <a name="return-value"></a>Возвращаемое значение  
Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
Этот метод изменяет ориентацию кольца для всех **Polygons** в коллекции **GeometryCollection**, но не удаляет и не изменяет **Points** или **LineStrings** в данной коллекции.  
  
Если передать коллекцию **GeometryCollection** этому методу, то для каждого экземпляра в коллекции будет изменена ориентация, однако ориентация всей коллекции не изменится.  
  
## <a name="examples"></a>Примеры  
  
```  
DECLARE @R GEOGRAPHY = GEOGRAPHY::Parse('Polygon((-10 -10, -10 10, 10 10, 10 -10, -10 -10))');  
SELECT @R.ReorientObject().STAsText();  
--Result: POLYGON ((10 10, -10 10, -10 -10, 10 -10, 10 10))  
```  
  
## <a name="see-also"></a>См. также  
[Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
