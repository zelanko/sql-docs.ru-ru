---
title: "CERT_ID (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1186308529dc9f4c7c7c4f792dc1e24aeb448c47
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="certid-transact-sql"></a>CERT_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает идентификатор сертификата.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
Cert_ID ( 'cert_name' )  
```  
  
## <a name="arguments"></a>Аргументы  
**"** *cert_name* **"**  
Имя сертификата в базе данных.
  
## <a name="return-types"></a>Возвращаемые типы
 **int**  
  
## <a name="remarks"></a>Замечания  
Имена сертификатов перечислены в [sys.certificates](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md) представления каталога.
  
## <a name="permissions"></a>Permissions  
Требуется ряд разрешений на сертификат, кроме того у участника не должно быть запрещено разрешение VIEW DEFINITION на этот сертификат.
  
## <a name="examples"></a>Примеры  
В следующем примере возвращается идентификатор сертификата с именем `ABerglundCert3`.
  
```sql
SELECT Cert_ID('ABerglundCert3');  
GO  
```  
  
## <a name="see-also"></a>См. также:
[sys.certificates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)  
[CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)  
[Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)
  
  

