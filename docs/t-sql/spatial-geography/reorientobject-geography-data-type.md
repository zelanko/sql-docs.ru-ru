---
title: ReorientObject (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f211a962185f903437c40a29d0c6803729f08c91
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38002652"
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
 *geography*  
 Другой экземпляр **geography**, для которого вызван метод `ReorientObject()`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
## <a name="remarks"></a>Примечания  
 Этот метод изменяет ориентацию кольца для всех **Polygons** в коллекции **GeometryCollection**, но не удаляет и не изменяет **Points** или **Linestrings** в данной коллекции.  
  
 Если коллекция **GeometryCollection** будет передана этому методу, то для каждого экземпляра в коллекции будет изменена ориентация, однако для коллекции целиком ориентация не меняется.  
  
## <a name="examples"></a>Примеры  
  
```  
DECLARE @R GEOGRAPHY = GEOGRAPHY::Parse('Polygon((-10 -10, -10 10, 10 10, 10 -10, -10 -10))');  
SELECT @R.ReorientObject().STAsText();  
--Result: POLYGON ((10 10, -10 10, -10 -10, 10 -10, 10 10))  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
