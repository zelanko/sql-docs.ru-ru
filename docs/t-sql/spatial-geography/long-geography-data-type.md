---
title: Long (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Long_TSQL
- Long
dev_langs:
- TSQL
helpviewer_keywords:
- Long method
ms.assetid: bedbeced-70b8-4569-84f3-f86bfb04ce50
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 2287205c91f2ceaef44af7bf8322d3c31e201c0c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65937664"
---
# <a name="long-geography-data-type"></a>Long (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает свойство долготы для экземпляра **geography**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.Long  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **float**  
  
 Тип CLR: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 В модели OpenGIS метод Long определен только для экземпляров **geography**, состоящих из одной точки. Это свойство возвращает значение NULL, если экземпляры **geography** содержат несколько точек. Это свойство является точным и доступно только для чтения.  
  
## <a name="examples"></a>Примеры  
 Это пример создает экземпляр **Point** и получает долготу точки.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.Long;  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
