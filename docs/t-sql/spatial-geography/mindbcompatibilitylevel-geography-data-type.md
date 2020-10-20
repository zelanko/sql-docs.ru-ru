---
description: MinDbCompatibilityLevel (тип данных geography)
title: MinDbCompatibilityLevel (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- MinDbCompatibilityLevel
- MinDbCompatibilityLevel_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MinDbCompatibilityLevel method (geography)
ms.assetid: a9e44748-4a9e-4179-abc4-7631597be5a7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: cfce4111cfcfb296689754e18aeea37878636543
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92038087"
---
# <a name="mindbcompatibilitylevel-geography-data-type"></a>MinDbCompatibilityLevel (тип данных geography)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает минимальный уровень совместимости базы данных, при котором поддерживается тип данных **geography**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
. MinDbCompatibilityLevel ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Типы возвращаемых данных
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **int**  
  
 Тип возвращаемых данных CLR: **int**  
  
## <a name="remarks"></a>Комментарии  
 Используйте `MinDbCompatibilityLevel()` для проверки пространственного объекта на совместимость, прежде чем менять уровень совместимости базы данных. В случае недопустимого типа **geography** возвращается значение 110.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-testing-circularstring-type-for-compatibility-with-compatibility-level-110"></a>A. Проверка типа CircularString на совместимость с уровнем совместимости 110  
 В следующем примере экземпляр `CircularString` проверяется на совместимость с более ранней версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
```  
DECLARE @g geometry = 'CIRCULARSTRING(-120.533 46.566, -118.283 46.1, -122.3 47.45)';  
IF @g.MinDbCompatibilityLevel() <= 110  
BEGIN  
    SELECT @g.ToString();  
END  
  
```  
  
### <a name="b-testing-linestring-type-for-compatibility-with-compatibility-level-100"></a>Б. Проверка типа LineString на совместимость с уровнем совместимости 100  
 В следующем примере экземпляр `LineString` проверяется на совместимость с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]:  
  
```  
DECLARE @g geometry = 'LINESTRING(-120.533 46.566, -118.283 46.1, -122.3 47.45)';  
IF @g.MinDbCompatibilityLevel() <= 100  
BEGIN  
    SELECT @g.ToString();  
END  
  
```  
  
### <a name="c-testing-the-value-of-a-geography-instance-for-compatibility"></a>В. Проверка значения экземпляра географического объекта на совместимость  
 В следующем примере показаны уровни совместимости для двух экземпляров `geography`. Один меньше полушария, а другой — больше.  
  
```  
DECLARE @g geography = geography::Parse('POLYGON((0 -10, 120 -10, 240 -10, 0 -10))');  
DECLARE @h geography = geography::Parse('POLYGON((0 10, 120 10, 240 10, 0 10))');  
IF (@g.EnvelopeAngle() >= 90)  
BEGIN  
SELECT @g.MinDbCompatibilityLevel();  
END     
IF (@h.EnvelopeAngle() < 90)  
BEGIN  
SELECT @h.MinDbCompatibilityLevel();  
END  
  
```  
  
 Первая инструкция SELECT возвращает 110, а вторая инструкция SELECT возвращает 100.  
  
## <a name="see-also"></a>См. также:  
 [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
 [Обратная совместимость компонента ядра СУБД SQL Server](../../database-engine/discontinued-database-engine-functionality-in-sql-server.md)  
  
