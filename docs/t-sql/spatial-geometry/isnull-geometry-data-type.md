---
title: IsNull (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 09/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IsNull (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- IsNull (geometry Data Type)
ms.assetid: f95813a5-26c0-48aa-bfb8-56d2a0980788
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 7cb1cccba4c880fd2e92d707e51c8c4e324fba9c
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86555689"
---
# <a name="isnull-geometry-data-type"></a>IsNull (тип данных geometry)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Тип экземпляра **geometry** — NULL. Возвращает значение 0, если экземпляр отличен от NULL.
  
## <a name="syntax"></a>Синтаксис  
  
```  
.IsNull  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Типы возвращаемых данных
 Тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Тип CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Метод `IsNull` позволяет проверить, имеет ли экземпляр **geometry** значение NULL. `IsNull` возвращает 0, если экземпляр не имеет значение NULL, но возвращает NULL, если экземпляр имеет значение NULL.  
  
 Этот метод в основном используется инфраструктурой SQL Server; не рекомендуется использовать `IsNull`, чтобы проверить, имеет ли экземпляр значение NULL.  
  

## <a name="see-also"></a>См. также:  
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

