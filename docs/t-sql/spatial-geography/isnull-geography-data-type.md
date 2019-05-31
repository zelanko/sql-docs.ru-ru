---
title: IsNull (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IsNull (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- IsNull method
ms.assetid: c031074f-bfda-4584-a3bf-4e7c324f237f
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: a780172818bd41fa3cff4804437b4d26ad8c95c5
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65937737"
---
# <a name="isnull-geography-data-type"></a>IsNull (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Свойство, которое показывает, имеет ли экземпляр **geography** значение NULL. Возвращает TRUE, если экземпляр — NULL; возвращает 0, если экземпляр отличен от NULL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.IsNull  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Тип CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Метод `IsNull` позволяет проверить, имеет ли экземпляр **geography** значение NULL. Это может привести к неочевидному результату, так как, если экземпляр имеет значение, отличное от NULL, возвращается значение 0, а если экземпляр имеет значение NULL, возвращается значение NULL.  
  
 Этот метод в основном используется инфраструктурой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для проверки, имеет ли экземпляр **geography** значение NULL, рекомендуется использовать предикат T-SQL IS NULL. Дополнительные сведения о предикате T-SQL IS NULL см. в статье [IS NULL (Transact-SQL)](../../t-sql/queries/is-null-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
  
## <a name="see-also"></a>См. также  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
