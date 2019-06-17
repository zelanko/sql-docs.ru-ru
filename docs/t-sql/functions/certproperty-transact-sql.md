---
title: CERTPROPERTY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: c27111dac0da8d9248bea1b7d7408cd70130d01b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65948806"
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
Значение идентификатора сертификата, имеющее тип данных int.
  
*Expiry_Date*  
Дата окончания действия сертификата.
  
*Start_Date*  
Дата вступления сертификата в силу.
  
*Issuer_Name*  
Имя издателя сертификата.
  
*Cert_Serial_Number*  
Серийный номер сертификата.
  
*Тема*  
Субъект сертификата.
  
 *SID*  
Идентификатор защиты (SID) сертификата. А также это SID любого имени входа или пользователя, сопоставленного этому сертификату.
  
*String_SID*  
Идентификатор защиты (SID) сертификата в виде символьной строки. А также это SID любого имени входа или пользователя, сопоставленного этому сертификату.
  
## <a name="return-types"></a>Типы возвращаемых данных
Задание свойства должно заключаться в одинарные кавычки.
  
Тип возвращаемого значения зависит от свойства, указанного при вызове функции. Тип возвращаемого значения **sql_variant** создает оболочку для всех возвращаемых значений.
-   *Expiry_Date* и *Start_Date* возвращают значения типа **datetime**.  
-   *Cert_Serial_Number*, *Issuer_Name*, *String_SID* и *Subject* возвращают значения типа **nvarchar**.  
-   *SID* возвращает значение типа **varbinary**.  
  
## <a name="remarks"></a>Remarks  
См. сведения о сертификате в представлении каталога [sys.certificates](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md).
  
## <a name="permissions"></a>Разрешения  
Требуются соответствующие разрешения на сертификат, кроме того, у участника не должно быть запрещено разрешение VIEW на этот сертификат. Дополнительные сведения о разрешениях сертификата см. в разделах [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md) и [GRANT CERTIFICATE PERMISSIONS (Transact-SQL)](../../t-sql/statements/grant-certificate-permissions-transact-sql.md).
  
## <a name="examples"></a>Примеры  
В следующем примере возвращается предмет сертификата.
  
```sql
-- First create a certificate.  
CREATE CERTIFICATE Marketing19 WITH   
    START_DATE = '04/04/2004' ,  
    EXPIRY_DATE = '07/07/2040' ,  
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
  
  
