---
title: DROP SIGNATURE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
caps.latest.revision: 32
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6eb9c6644976452a3a98ff63e3be2abd4d9d9870
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37980976"
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
  
  
