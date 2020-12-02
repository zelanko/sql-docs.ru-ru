---
description: ':: (разрешение области) (Transact-SQL)'
title: ':: (разрешение области) (Transact-SQL) | Документы Майкрософт'
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
ms.openlocfilehash: 6c319d0e7e67605f09954e88434842be9b8ae1df
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96124397"
---
# <a name="-scope-resolution-transact-sql"></a>:: (разрешение области) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Оператор разрешения области **::** обеспечивает доступ к статическим элементам составного типа данных. Составной тип данных содержит несколько простых типов данных и методов. К составным типам данных относятся встроенные типы CLR и настраиваемые пользовательские типы (UDT) SQLCLR.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как применять оператор разрешения области для доступа к элементу `GetRoot()` типа данных `hierarchyid`.  
  
```sql  
DECLARE @hid hierarchyid;  
SELECT @hid = hierarchyid::GetRoot();  
PRINT @hid.ToString();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `/`  
  
## <a name="see-also"></a>См. также  
 [Операторы (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)  
 
