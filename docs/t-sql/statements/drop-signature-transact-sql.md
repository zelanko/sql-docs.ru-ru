---
title: "DROP SIGNATURE (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP SIGNATURE
- DROP_SIGNATURE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting signatures
- dropping signatures
- DROP SIGNATURE statement
- removing signatures
- signatures [SQL Server]
- digital signatures [SQL Server]
ms.assetid: 8a1fd8c5-0e75-4b2f-9d3c-c296bed56cc7
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e9c58cc536c6ffa929dce2466f8a7c4c27528ba4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="drop-signature-transact-sql"></a>DROP SIGNATURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Удаляет цифровую подпись из хранимой процедуры, функции, триггера или сборки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP [ COUNTER ] SIGNATURE FROM module_name   
    BY <crypto_list> [ ,...n ]  
  
<crypto_list> ::=  
    CERTIFICATE cert_name  
    | ASYMMETRIC KEY Asym_key_name  
```  
  
## <a name="arguments"></a>Аргументы  
 *module_name*  
 Имя хранимой процедуры, функции, сборки или триггера.  
  
 CERTIFICATE *cert_name*  
 Имя сертификата, с помощью которого подписана хранимая процедура, функция, сборка или триггер.  
  
 ASYMMETRIC KEY *Asym_key_name*  
 Имя асимметричного ключа, с помощью которого подписана хранимая процедура, функция, сборка или триггер.  
  
## <a name="remarks"></a>Remarks  
 Сведения о подписях содержатся в представлении каталога sys.crypt_properties.  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения ALTER на объект и разрешение CONTROL на сертификат или асимметричный ключ. Если соответствующий закрытый ключ защищен паролем, то у пользователя также должен быть этот пароль.  
  
## <a name="examples"></a>Примеры  
 На следующем примере показано, как удаляется подпись сертификата `HumanResourcesDP` из хранимой процедуры `HumanResources.uspUpdateEmployeeLogin`.  
  
```  
USE AdventureWorks2012;  
DROP SIGNATURE FROM HumanResources.uspUpdateEmployeeLogin   
    BY CERTIFICATE HumanResourcesDP;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.crypt_properties (Transact-SQL)](../../relational-databases/system-catalog-views/sys-crypt-properties-transact-sql.md)   
 [ADD SIGNATURE (Transact-SQL)](../../t-sql/statements/add-signature-transact-sql.md)  
  
  
