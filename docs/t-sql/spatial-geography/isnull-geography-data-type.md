---
title: "IsNull (тип данных geography) | Документы Майкрософт"
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
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c07ddb41209c507845da7e790035ab54ed1044f1
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="isnull-geography-data-type"></a>IsNull (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Свойство, которое показывает, имеет ли экземпляр **geography** значение NULL. Возвращает TRUE, если экземпляр — NULL; возвращает 0, если экземпляр отличен от NULL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.IsNull  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Тип CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Метод `IsNull` позволяет проверить, имеет ли экземпляр **geography** значение NULL. Это может привести к неочевидному результату, так как, если экземпляр имеет значение, отличное от NULL, возвращается значение 0, а если экземпляр имеет значение NULL, возвращается значение NULL.  
  
 Этот метод в основном используется инфраструктурой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для проверки, имеет ли экземпляр **geography** значение NULL, рекомендуется использовать предикат T-SQL IS NULL. Дополнительные сведения о предикате T-SQL IS NULL см. в статье [IS NULL (Transact-SQL)](../../t-sql/queries/is-null-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
