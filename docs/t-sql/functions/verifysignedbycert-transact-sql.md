---
title: VERIFYSIGNEDBYCERT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- VERIFYSIGNEDBYCERT
- VERIFYSIGNEDBYCERT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- digitally signed data for changes [SQL Server]
- verifying digitally signed data for changes
- testing digitally signed data for changes
- checking digitally signed data for changes
- VERIFYSIGNEDBYCERT
- signatures [SQL Server]
- digital signatures [SQL Server]
ms.assetid: 4e041f33-60c4-4190-91c7-220d51dd6c8f
caps.latest.revision: 41
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1b90413b1163bb3edac09e09ee8905106c7050f7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33062261"
---
# <a name="verifysignedbycert-transact-sql"></a>VERIFYSIGNEDBYCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Проверяет, изменялись ли данные с цифровой подписью с момента подписи.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
VerifySignedByCert( Cert_ID , signed_data , signature )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Cert_ID*  
 Идентификатор сертификата в базе данных. Аргумент *Cert_ID* имеет тип **int**.  
  
 *signed_data*  
 Переменная типа **nvarchar**, **char**, **varchar** или **nchar**, содержащая данные, которые были подписаны с помощью сертификата.  
  
 *signature*  
 Это подпись, которая была прикреплена к подписанным данным. Аргумент *signature* имеет тип **varbinary**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **int**  
  
 Возвращает 1, если подписанные данные не были изменены, и 0 — в противном случае.  
  
## <a name="remarks"></a>Remarks  
 **VerifySignedBycert** расшифровывает подпись данных с помощью открытого ключа указанного сертификата и сравнивает расшифрованное значение с новым хэшем MD5, вычисленным для данных. Если значения совпадают, подтверждается допустимость подписи.  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения VIEW DEFINITION на сертификат.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-verifying-that-signed-data-has-not-been-tampered-with"></a>A. Проверка подписанных данных на предмет подделки  
 В следующем примере данные, содержащиеся в `Signed_Data`, тестируются на предмет изменения с момента подписи с сертификатом под именем `Shipping04`. Подпись хранится в `DataSignature`. Сертификат `Shipping04` передается в `Cert_ID`, которая возвращает идентификатор сертификата в базу данных. Если `VerifySignedByCert` возвращает 1, подпись верна. Если же `VerifySignedByCert` возвращает 0, данные в `Signed_Data` не являются теми данными, которые использовались для формирования `DataSignature`. В этом случае либо `Signed_Data` были изменены с момента подписи, либо `Signed_Data` были подписаны с другим сертификатом.  
  
```  
SELECT Data, VerifySignedByCert( Cert_Id( 'Shipping04' ),  
    Signed_Data, DataSignature ) AS IsSignatureValid  
FROM [AdventureWorks2012].[SignedData04]   
WHERE Description = N'data signed by certificate ''Shipping04''';  
GO  
```  
  
### <a name="b-returning-only-records-that-have-a-valid-signature"></a>Б. Возвращение только записей, имеющих действительную подпись  
 Этот запрос возвращает только те записи, которые не менялись с тех пор, как они были подписаны с использованием сертификата `Shipping04`.  
  
```  
SELECT Data FROM [AdventureWorks2012].[SignedData04]   
WHERE VerifySignedByCert( Cert_Id( 'Shipping04' ), Data,   
    DataSignature ) = 1   
AND Description = N'data signed by certificate ''Shipping04''';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CERT_ID (Transact-SQL)](../../t-sql/functions/cert-id-transact-sql.md)   
 [SIGNBYCERT (Transact-SQL)](../../t-sql/functions/signbycert-transact-sql.md)   
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE (Transact-SQL)](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE (Transact-SQL)](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE (Transact-SQL)](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
