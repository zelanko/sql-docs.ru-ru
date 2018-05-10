---
title: STNumCurves (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STNumCurves
- STNumCurves_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumCurves method (geography)
ms.assetid: e98a56c2-8496-4dfd-9b37-7f3c4ca9b2b5
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e2acda5ed4fa89dbda902b64afec541d38ba3b84
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="stnumcurves-geography-data-type"></a>STNumCurves (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает количество кривых в одномерном экземпляре **geography**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STNumCurves()  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 К одномерным пространственным типам данных относятся **LineString**, **CircularString** и **CompoundCurve**. Пустой одномерный экземпляр **geography** возвращает значение 0.  
  
 Функция `STNumCurves`() поддерживает только простые типы; она не поддерживает коллекции **geography**, такие как **MultiLineString**. Возвращается значение **NULL**, если экземпляр **geography** не является одномерным типом данных.  
  
 Возвращает **NULL** для неинициализированных экземпляров **geography**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-stnumcurves-on-a-circularstring-instance"></a>A. Использование метода STNumCurves() в экземпляре CircularString  
 В следующем примере описывается получение определенного количества кривых в экземпляре `CircularString`:  
  
```
 DECLARE @g geography; 
 SET @g = geography::Parse('CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)');  
 SELECT @g.STNumCurves();
 ```  
  
### <a name="b-using-stnumcurves-on-a-compoundcurve-instance"></a>Б. Использование метода STNumCurves() в экземпляре CompoundCurve  
 В следующем примере метод `STNumCurves()` используется для возврата определенного количества кривых в экземпляре `CompoundCurve`.  
  
```
 DECLARE @g geography;  
 SET @g = geography::Parse('COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))');  
 SELECT @g.STNumCurves();
 ```  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о типах пространственных данных](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
