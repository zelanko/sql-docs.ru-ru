---
title: "FILEGROUPPROPERTY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FILEGROUPPROPERTY_TSQL
- FILEGROUPPROPERTY
dev_langs: TSQL
helpviewer_keywords:
- filegroups [SQL Server], property values
- FILEGROUPPROPERTY function
- viewing filegroup properties
- displaying filegroup properties
ms.assetid: b3a930e6-df05-4034-929c-f681f5f6fc6e
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 06a63d753f2f38864889dc78b24e7ff47e78c331
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="filegroupproperty-transact-sql"></a>FILEGROUPPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает значение указанного свойства файловой группы по имени файловой группы и имени свойства.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FILEGROUPPROPERTY ( filegroup_name , property )  
```  
  
## <a name="arguments"></a>Аргументы  
 *filegroup_name*  
 Является выражением типа **sysname** , представляющее имя файловой группы, для которой возвращается информация об именованном свойстве.  
  
 *Свойство*  
 Является выражением типа **varchar(128)** содержит имя свойства файловой группы, для возврата. *Свойство* может принимать одно из следующих значений.  
  
|Значение|Description|Возвращенное значение|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|Файловая группа доступна только для чтения.|1 = True<br /><br /> 0 = False.<br /><br /> NULL = Введенные значения недопустимы.|  
|**IsUserDefinedFG**|Файловая группа является пользовательской.|1 = True<br /><br /> 0 = False.<br /><br /> NULL = Введенные значения недопустимы.|  
|**IsDefault**|Файловая группа является файловой группой по умолчанию.|1 = True<br /><br /> 0 = False.<br /><br /> NULL = Введенные значения недопустимы.|  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
## <a name="remarks"></a>Замечания  
 *filegroup_name* соответствует **имя** столбца в **sys.filegroups** представления каталога.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает значение свойства `IsDefault` первичной файловой группы в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
  
SELECT FILEGROUPPROPERTY('PRIMARY', 'IsDefault') AS 'Default Filegroup';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Default Filegroup   
---------------------   
1  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:  
 [FILEGROUP_ID &#40; Transact-SQL &#41;](../../t-sql/functions/filegroup-id-transact-sql.md)   
 [FILEGROUP_NAME &#40; Transact-SQL &#41;](../../t-sql/functions/filegroup-name-transact-sql.md)   
 [Функции метаданных &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [sys.filegroups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)  
  
  
