---
title: "IsNull (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IsNull (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- IsNull method
ms.assetid: c031074f-bfda-4584-a3bf-4e7c324f237f
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9b9f65a3860b1b0d54231d3243fdfdf1902ae8ca
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="isnull-geography-data-type"></a>IsNull (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Свойство, которое указывает, если **geography** экземпляр имеет значение null. Возвращает TRUE, если экземпляр — NULL; возвращает 0, если экземпляр отличен от NULL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.IsNull  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип: **бит**  
  
 Тип CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Замечания  
 `IsNull`можно использовать для тестирования ли **geography** экземпляр имеет значение null. Это может привести к неочевидному результату, так как, если экземпляр имеет значение, отличное от NULL, возвращается значение 0, а если экземпляр имеет значение NULL, возвращается значение NULL.  
  
 Этот метод в основном используется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инфраструктуре; рекомендуется использовать предикат T-SQL IS NULL, чтобы проверить ли **geography** экземпляр имеет значение null. Дополнительные сведения о T-SQL, предикат IS NULL см. в разделе [IS NULL & #40; Transact-SQL & #41; ](../../t-sql/queries/is-null-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы в экземплярах географических объектов](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  

