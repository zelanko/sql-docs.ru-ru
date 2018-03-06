---
title: "CERT_ID (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 07/24/2017
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
- CERT_ID
- CERT_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- identification numbers [SQL Server], certificates
- CERT_ID function
- IDs [SQL Server], certificates
- certificates [SQL Server], IDs
ms.assetid: 59cc06f5-272e-4936-8afe-afba7aba8eea
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3abed6a762708581344c189ecf4ef6c0fd5331d7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="certid-transact-sql"></a>CERT_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает идентификатор сертификата.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
Cert_ID ( 'cert_name' )  
```  
  
## <a name="arguments"></a>Аргументы  
**'** *cert_name* **'**  
Имя сертификата в базе данных.
  
## <a name="return-types"></a>Типы возвращаемых данных
 **int**  
  
## <a name="remarks"></a>Remarks  
Имена сертификатов перечислены в представлении каталога [sys.certificates](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md).
  
## <a name="permissions"></a>Разрешения  
Требуется ряд разрешений на сертификат, кроме того у участника не должно быть запрещено разрешение VIEW DEFINITION на этот сертификат.
  
## <a name="examples"></a>Примеры  
В следующем примере возвращается идентификатор сертификата с именем `ABerglundCert3`.
  
```sql
SELECT Cert_ID('ABerglundCert3');  
GO  
```  
  
## <a name="see-also"></a>См. также раздел
[sys.certificates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)  
[CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)  
[Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)
  
  
