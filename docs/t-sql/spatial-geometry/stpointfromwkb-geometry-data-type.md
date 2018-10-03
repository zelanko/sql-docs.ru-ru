---
title: STPointFromWKB (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STPointFromWKB (geometry Data Type)
- STPointFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STPointFromWKB (geometry Data Type)
ms.assetid: 1157c172-2dc7-4393-bae6-b85406171a34
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3cef65b2d51cba199b3a908ee8f71880663aee53
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600442"
---
# <a name="stpointfromwkb-geometry-data-type"></a>STPointFromWKB (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает экземпляр **geometryPoint** из WKB-представления OGC.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
STPointFromWKB ( 'WKB_point' , SRID )  
```  
  
## <a name="arguments"></a>Аргументы  
 *WKB_point*  
 Представление в формате WKB возвращаемого экземпляра **geometryPoint**. *WKB_point* — это выражение типа **varbinary(max)**.  
  
 *SRID*  
 Выражение типа **int**, представляющее идентификатор пространственной ссылки (SRID) возвращаемого экземпляра **geometryPoint**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемых данных CLR: **SqlGeometry**  
  
 Тип OGC: **Point**  
  
## <a name="remarks"></a>Remarks  
 Этот метод вызывает исключение **FormatException**, если входные данные представлены в неверном формате.  
  
## <a name="examples"></a>Примеры  
 В следующем примере метод `STPointFromWKB()` применяется для создания экземпляра `geometry`.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::STPointFromWKB(0x010100000000000000000059400000000000005940, 0);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>См. также  
 [Статические геометрические методы OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

