---
title: "ReorientObject (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ReorientObject
- ReorientObject_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ReorientObject method (geography)
ms.assetid: e2a1a4f1-211b-4e82-abed-03fc7140a83c
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3a32dc43776511881697b972c9279d143af917c2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="reorientobject-geography-data-type"></a>ReorientObject (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает **geography** экземпляр со взаимозаменяемыми внутренними и внешними областями.  
  
 Это **geography** поддерживает метод тип **FullGlobe** экземпляры или Пространственные экземпляры, размер которых превышает полусферу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.ReorientObject (geography)  
```  
  
## <a name="arguments"></a>Аргументы  
 *geography*  
 Другой **geography** экземпляр, на котором `ReorientObject()` вызывается.  
  
## <a name="return-value"></a>Возвращаемое значение  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="remarks"></a>Замечания  
 Этот метод изменяет ориентацию кольца для всех **многоугольников** в **GeometryCollection** , но не удалить или изменить какие-либо **точки** или **Linestrings** в заданной коллекции.  
  
 Если **GeometryCollection** передается этому методу, каждый экземпляр в коллекции будет изменена ориентация, но коллекции целиком ориентация не меняется.  
  
## <a name="examples"></a>Примеры  
  
```  
DECLARE @R GEOGRAPHY = GEOGRAPHY::Parse('Polygon((-10 -10, -10 10, 10 10, 10 -10, -10 -10))');  
SELECT @R.ReorientObject().STAsText();  
--Result: POLYGON ((10 10, -10 10, -10 -10, 10 -10, 10 10))  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы в экземплярах географических объектов](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  

