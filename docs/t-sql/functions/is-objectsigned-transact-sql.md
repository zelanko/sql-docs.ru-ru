---
title: IS_OBJECTSIGNED (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
manager: craigg
ms.openlocfilehash: 104cf6916beca429e65610106cbdba5a289deeec
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33054871"
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
 **'OBJECT'**  
 Тип защищаемого класса.  
  
 *@object_id*  
 Идентификатор object_id проверяемого объекта. *@object_id* имеет тип **int**.  
  
 *@class*  
 Класс объекта:  
  
-   'certificate'  
  
-   'asymmetric key'  
  
 *@class* имеет тип **sysname**.  
  
 *@thumbprint*  
 SHA-отпечаток объекта. *@thumbprint* имеет тип **varbinary(32)**.  
  
## <a name="returned-types"></a>Возвращаемые типы  
 **int**  
  
## <a name="remarks"></a>Remarks  
 Функция IS_OBJECTSIGNED возвращает следующие значения.  
  
|Возвращаемое значение|Description|  
|------------------|-----------------|  
|NULL|Объект не подписан или недопустим.|  
|0|Объект подписан, но подпись недействительна.|  
|1|Объект подписан.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DEFINITION на сертификат или асимметричный ключ.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-displaying-extended-properties-on-a-database"></a>A. Отображение расширенных свойств базы данных  
 В приведенном ниже примере проверяется, подписана ли таблица spt_fallback_db в базе данных **master** с помощью сертификата подписания схемы.  
  
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
 [sys.fn_check_object_signatures (Transact-SQL)](../../relational-databases/system-functions/sys-fn-check-object-signatures-transact-sql.md)  
  
  
