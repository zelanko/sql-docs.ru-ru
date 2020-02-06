---
title: STNumGeometries (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STNumGeometries (geometry Data Type)
- STNumGeometries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumGeometries (geometry Data Type)
ms.assetid: 9402b03d-3039-42ca-ac59-f96b7f1a48de
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 5a0c123b367fa2a85a1a3732200452a474b032c6
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68088923"
---
# <a name="stnumgeometries-geometry-data-type"></a>STNumGeometries (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает количество геометрических объектов, составляющих экземпляр **geometry**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STNumGeometries ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **int**  
  
 Тип возвращаемых данных CLR: **SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 Этот метод возвращает значение 1, если экземпляр **geometry** не является экземпляром **MultiPoint**, **MultiLineString**, **MultiPolygon** или **GeometryCollection**, либо значение 0, если экземпляр **geometry** пуст.  
  
> [!NOTE]  
>  Если в коллекции **GeometryCollection** есть пустые вложенные элементы, то функция `STNumGeometries()` не возвратит значение 0. Несмотря на то, что элементы из экземпляра **GeometryCollection** пусты, сам экземпляр не является пустым набором.  
  
  

