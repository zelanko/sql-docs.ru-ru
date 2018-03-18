---
title: "CERTPROPERTY (Transact-SQL) | Документы Майкрософт"
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
- CERTPROPERTY
- CERTPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], schema names
- schemas [SQL Server], names
- CERTPROPERTY function
ms.assetid: 966c09aa-bc4e-45b0-ba53-c8381871f638
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d63968d8b07a37ea49662bd0727632a1675b3913
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="certproperty-transact-sql"></a>CERTPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
Идентификатор сертификата. Аргумент *Cert_ID* имеет тип int.
  
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
  
 *SID*  
Идентификатор защиты (SID) сертификата. А также это SID любого имени входа или пользователя, сопоставленного этому сертификату.
  
*String_SID*  
Идентификатор защиты (SID) сертификата в виде символьной строки. А также это SID любого имени входа или пользователя, сопоставленного этому сертификату.
  
## <a name="return-types"></a>Типы возвращаемых данных
Задание свойства должно заключаться в одинарные кавычки.
  
Возвращаемый тип зависит от свойства, указанного при вызове функции. Все возвращаемые значения упаковываются в возвращаемый тип **sql_variant**.
-   *Expiry_Date* и *Start_Date* возвращают значения типа **datetime**.  
-   *Cert_Serial_Number*, *Issuer_Name*, *Subject* и *String_SID* возвращают значения типа **nvarchar**.  
-   *SID* возвращает значение типа **varbinary**.  
  
## <a name="remarks"></a>Remarks  
Сведения о сертификатах можно увидеть в представлении каталога [sys.certificates](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md).
  
## <a name="permissions"></a>Разрешения  
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
  
## <a name="see-also"></a>См. также раздел
[CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)  
[ALTER CERTIFICATE (Transact-SQL)](../../t-sql/statements/alter-certificate-transact-sql.md)  
[CERT_ID (Transact-SQL)](../../t-sql/functions/cert-id-transact-sql.md)
[Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)
[sys.certificates (Transact-SQL)](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)
[Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)
  
  
