---
title: sys.fn_check_object_signatures (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.fn_check_object_signatures_TSQL
- fn_check_object_signatures_TSQL
- fn_check_object_signatures
- sys.fn_check_object_signatures
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_check_object_signatures function
ms.assetid: 47509566-d3d7-46a9-89c1-91b4895d56b9
caps.latest.revision: 15
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 9ed5b999619de7958d0ca180b6e2bdd1a2b14283
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39544864"
---
# <a name="sysfncheckobjectsignatures-transact-sql"></a>sys.fn_check_object_signatures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Возвращает список всех подписываемых объектов и показывает, был ли объект подписан указанным сертификатом или асимметричным ключом. Если объект подписан указанным сертификатом или асимметричным ключом, возвращает также данные о том, является ли подпись объекта допустимой.  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn_ check_object_signatures (   
    { '@class' } , { @thumbprint }   
  )   
```  
  
## <a name="arguments"></a>Аргументы  
 {"\@*класс*"}  
 Идентифицирует тип предоставляемого отпечатка:  
  
-   'certificate'  
  
-   'asymmetric key'  
  
 \@*Класс* — **sysname**.  
  
 { \@ *отпечаток* }  
 Хэш SHA-1 сертификата, с помощью которого был зашифрован ключ, или идентификатор GUID асимметричного ключа, которым был зашифрован этот ключ. \@*отпечаток* — **varbinary(20)**.  
  
## <a name="tables-returned"></a>Возвращаемые таблицы  
 В следующей таблице перечислены столбцы, **fn_check_object_signatures** возвращает.  
  
|Столбец|Тип|Описание|  
|------------|----------|-----------------|  
|Тип|**nvarchar(120)**|Возвращает описание типа или сборки.|  
|entity_id|**int**|Возвращает идентификатор оцениваемого объекта.|  
|is_signed|**int**|Возвращает значение 0, если объект не был подписан с помощью предоставленного отпечатка. Возвращает значение 1, если объект подписан с помощью предоставленного отпечатка.|  
|is_signature_valid|**int**|Если значение is_signed равно 1, возвращает значение 0, если подпись не является допустимой. Возвращает значение 1, если подпись является допустимой.<br /><br /> Если значение is_signed равно 0, всегда возвращает 0.|  
  
## <a name="remarks"></a>Примечания  
 Используйте **fn_check_object_signatures** для подтверждения того, что пользователи-злоумышленники не изменены с объектами.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DEFINITION на сертификат или асимметричный ключ.  
  
## <a name="examples"></a>Примеры  
 В следующем примере выполняется поиск сертификата подписывания схемы для базы данных `master`, а также возвращается значение `is_signed`, равное 1, и значение `is_signature_valid`, равное 1, для тех объектов, которые подписаны сертификатом подписывания схемы и имеют допустимые подписи.  
  
```  
USE master;  
-- Declare a variable to hold the thumbprint.  
DECLARE @thumbprint varbinary(20) ;  
-- Populate the thumbprint variable with the master database schema signing certificate.  
SELECT @thumbprint = thumbprint   
FROM sys.certificates   
WHERE name LIKE '%SchemaSigningCertificate%' ;  
-- Evaluates the objects signed by the schema signing certificate  
SELECT type, entity_id, OBJECT_NAME(entity_id) AS [object name], is_signed, is_signature_valid  
FROM sys.fn_check_object_signatures ('certificate', @thumbprint) ;  
GO  
  
```  
  
## <a name="see-also"></a>См. также  
 [IS_OBJECTSIGNED &#40;Transact-SQL&#41;](../../t-sql/functions/is-objectsigned-transact-sql.md)  
  
  
