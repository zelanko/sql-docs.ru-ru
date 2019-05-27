---
title: ':: (разрешение области) (Transact-SQL) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 764d8f91-957b-4037-997b-a9b6b533c504
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6d721d6f39b33b553d0a00c55ddbc58df006029a
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65981835"
---
# <a name="-scope-resolution-transact-sql"></a>:: (разрешение области) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Оператор разрешения области **::** обеспечивает доступ к статическим элементам составного типа данных. Составной тип данных содержит несколько простых типов данных и методов. К составным типам данных относятся встроенные типы CLR и настраиваемые пользовательские типы (UDT) SQLCLR.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как применять оператор разрешения области для доступа к элементу `GetRoot()` типа данных `hierarchyid`.  
  
```  
DECLARE @hid hierarchyid;  
SELECT @hid = hierarchyid::GetRoot();  
PRINT @hid.ToString();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `/`  
  
## <a name="see-also"></a>См. также:  
 [Операторы (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)  
 