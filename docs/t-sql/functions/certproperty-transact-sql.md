---
title: "CERTPROPERTY (Transact-SQL) | Документы Microsoft"
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
- CERTPROPERTY
- CERTPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], schema names
- schemas [SQL Server], names
- CERTPROPERTY function
ms.assetid: 966c09aa-bc4e-45b0-ba53-c8381871f638
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4b43b587688b574c6d6395b72c5b368b82e617fd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="certproperty-transact-sql"></a>CERTPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает значение указанного свойства сертификата.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CertProperty ( Cert_ID , '<PropertyName>' )  
  
<PropertyName> ::=  
   Expiry_Date | Start_Date | Issuer_Name   
   | Cert_Serial_Number | Subject | SID | String_SID   
```  
  
## <a name="arguments"></a>Аргументы  
*Cert_ID*  
Идентификатор сертификата. *Cert_ID* имеет тип int.
  
*Expiry_Date*  
Дата истечения срока действия сертификата.
  
*Start_Date*  
Дата вступления сертификата в силу.
  
*Issuer_Name*  
Имя выдавшего сертификат.
  
*Cert_Serial_Number*  
Серийный номер сертификата.
  
*Тема*  
Предмет сертификата.
  
 *ИД БЕЗОПАСНОСТИ*  
Идентификатор защиты (SID) сертификата. А также это SID любого имени входа или пользователя, сопоставленного этому сертификату.
  
*String_SID*  
Идентификатор защиты (SID) сертификата в виде символьной строки. А также это SID любого имени входа или пользователя, сопоставленного этому сертификату.
  
## <a name="return-types"></a>Возвращаемые типы
Задание свойства должно заключаться в одинарные кавычки.
  
Возвращаемый тип зависит от свойства, указанного при вызове функции. Все возвращаемые значения упаковываются в возвращаемый тип **sql_variant**.
-   *Expiry_Date* и *Start_Date* возвращают **datetime**.  
-   *Cert_Serial_Number*, *Issuer_Name*, *субъекта*, и *String_SID* возвращают **nvarchar**.  
-   *SID* возвращает **varbinary**.  
  
## <a name="remarks"></a>Замечания  
Сведения о сертификатах можно увидеть в [sys.certificates](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md) представления каталога.
  
## <a name="permissions"></a>Permissions  
Требуется ряд разрешений на сертификат, кроме того у участника не должно быть запрещено разрешение VIEW DEFINITION на этот сертификат.
  
## <a name="examples"></a>Примеры  
В следующем примере возвращается предмет сертификата.
  
```sql
-- First create a certificate.  
CREATE CERTIFICATE Marketing19 WITH   
    START_DATE = '04/04/2004' ,  
    EXPIRY_DATE = '07/07/2007' ,  
    SUBJECT = 'Marketing Print Division';  
GO  
  
-- Now use CertProperty to examine certificate  
-- Marketing19's properties.  
DECLARE @CertSubject sql_variant;  
set @CertSubject = CertProperty( Cert_ID('Marketing19'), 'Subject');  
PRINT CONVERT(nvarchar, @CertSubject);  
GO  
```  
  
## <a name="see-also"></a>См. также:
[CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)  
[ALTER CERTIFICATE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-certificate-transact-sql.md)  
[CERT_ID &#40; Transact-SQL &#41; ](../../t-sql/functions/cert-id-transact-sql.md) 
 [Иерархии шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)
[sys.certificates &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md) 
 [Представления каталога безопасности &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)
  
  

