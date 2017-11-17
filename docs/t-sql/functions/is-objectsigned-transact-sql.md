---
title: "IS_OBJECTSIGNED (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IS_OBJECTSIGNED
- IS_OBJECTSIGNED_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IS_OBJECTSIGNED function
ms.assetid: afbc4f7f-8266-4ee6-9802-14a2dbe69ef6
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e346fb803e18d9a43afe15984166985ff0a3e408
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="isobjectsigned-transact-sql"></a>IS_OBJECTSIGNED (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Указывает, подписан ли объект с помощью определенного сертификата или асимметричного ключа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IS_OBJECTSIGNED (   
'OBJECT', @object_id, @class, @thumbprint  
  )   
```  
  
## <a name="arguments"></a>Аргументы  
 **«ОБЪЕКТ»**  
 Тип защищаемого класса.  
  
 *@object_id*  
 Идентификатор object_id проверяемого объекта. *@object_id*Тип **int**.  
  
 *@class*  
 Класс объекта:  
  
-   'certificate'  
  
-   'asymmetric key'  
  
 *@class*— **sysname**.  
  
 *@thumbprint*  
 SHA-отпечаток объекта. *@thumbprint*Тип **varbinary(32)**.  
  
## <a name="returned-types"></a>Возвращаемые типы  
 **int**  
  
## <a name="remarks"></a>Замечания  
 Функция IS_OBJECTSIGNED возвращает следующие значения.  
  
|Возвращаемое значение|Description|  
|------------------|-----------------|  
|NULL|Объект не подписан, или объект не является допустимым.|  
|0|Объект подписан, но подпись не является допустимым.|  
|1|Объект подписан.|  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение VIEW DEFINITION на сертификат или асимметричный ключ.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-displaying-extended-properties-on-a-database"></a>A. Отображение расширенных свойств базы данных  
 В следующем примере проверяется, подписана ли таблица spt_fallback_db в **master** подписан сертификатом подписания схемы базы данных.  
  
```  
USE master;  
-- Declare a variable to hold a thumbprint and an object name  
DECLARE @thumbprint varbinary(20), @objectname sysname;  
  
-- Populate the thumbprint variable with the thumbprint of   
-- the master database schema signing certificate  
SELECT @thumbprint = thumbprint   
FROM sys.certificates   
WHERE name LIKE '%SchemaSigningCertificate%';  
  
-- Populate the object name variable with a table name in master  
SELECT @objectname = 'spt_fallback_db';  
  
-- Query to see if the table is signed by the thumbprint  
SELECT @objectname AS [object name],  
IS_OBJECTSIGNED(  
'OBJECT', OBJECT_ID(@objectname), 'certificate', @thumbprint  
) AS [Is the object signed?] ;  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.fn_check_object_signatures &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-check-object-signatures-transact-sql.md)  
  
  

