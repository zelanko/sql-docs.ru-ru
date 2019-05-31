---
title: Null (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Null (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- Null (geometry Data Type)
ms.assetid: 67a4b019-9091-4443-85cc-f4836d0cb509
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: ccf081a6f1bac088c4a7539d4efd367f3bb7fade
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65937492"
---
# <a name="null-geometry-data-type"></a>Null (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Свойство только для чтения, которое возвращает экземпляр типа **geometry**, имеющий значение NULL.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Null  
```  
  
## <a name="arguments"></a>Аргументы  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Примеры  
 В следующем экземпляре производится получение экземпляра `geometry`, имеющего значение NULL.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::[Null];  
SELECT @g  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные статические геометрические методы](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

