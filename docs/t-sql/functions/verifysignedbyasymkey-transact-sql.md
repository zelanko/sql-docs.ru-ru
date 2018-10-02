---
title: VERIFYSIGNEDBYASYMKEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- VERIFYSIGNEDBYASYMKEY_TSQL
- VERIFYSIGNEDBYASYMKEY
dev_langs:
- TSQL
helpviewer_keywords:
- verifying digitally signed data for changes
- VERIFYSIGNEDBYASYMKEY
- testing digitally signed data for changes
- checking digitally signed data for changes
- signatures [SQL Server]
- digital signatures [SQL Server]
ms.assetid: 9f7c6e0b-5ba4-4dbb-994d-5bd59f4908de
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0b932435b65d7c3638e575b9ee3a86fd709f2985
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47799452"
---
# <a name="verifysignedbyasymkey-transact-sql"></a>VERIFYSIGNEDBYASYMKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Проверяет, изменялись ли данные с цифровой подписью с момента подписи.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
VerifySignedByAsymKey( Asym_Key_ID , clear_text , signature )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Asym_Key_ID*  
 Идентификатор сертификата с асимметричным ключом в базе данных.  
  
 *clear_text*  
 Незашифрованные текстовые данные, проверку которых нужно произвести.  
  
 *signature*  
 Это подпись, которая была прикреплена к подписанным данным. Аргумент *signature* имеет тип **varbinary**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **int**  
  
 Возвращает 1 в случае совпадения подписей и 0 — в противном случае.  
  
## <a name="remarks"></a>Remarks  
 **VerifySignedByAsymKey** выполняет расшифровку подписи данных с помощью открытого ключа указанного асимметричного ключа и сравнивает расшифрованное значение с новым вычисленным хэшем MD5 данных. Если значения совпадают, подтверждается допустимость подписи.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение VIEW DEFINITION на асимметричный ключ.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-testing-for-data-with-a-valid-signature"></a>A. Проверка данных с правильной подписью  
 Следующий пример возвращает 1, если выбранные данные не изменялись с момента их подписи ассиметричным ключом `WillisKey74`. Пример возвращает 0, если данные были испорчены.  
  
```  
SELECT Data,  
     VerifySignedByAsymKey( AsymKey_Id( 'WillisKey74' ), SignedData,  
     DataSignature ) as IsSignatureValid  
FROM [AdventureWorks2012].[SignedData04]   
WHERE Description = N'data encrypted by asymmetric key ''WillisKey74''';  
GO  
RETURN;  
```  
  
### <a name="b-returning-a-result-set-that-contains-data-with-a-valid-signature"></a>Б. Получение результирующего набора, содержащего данные с правильной подписью  
 В следующем примере возвращаются строки из `SignedData04`, содержащие данные, которые не изменялись с момента их подписи асимметричным ключом `WillisKey74`. Пример вызывает функцию `AsymKey_ID` для получения идентификатора асимметричного ключа из базы данных.  
  
```  
SELECT Data   
FROM [AdventureWorks2012].[SignedData04]   
WHERE VerifySignedByAsymKey( AsymKey_Id( 'WillisKey74' ), Data,  
     DataSignature ) = 1  
AND Description = N'data encrypted by asymmetric key ''WillisKey74''';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ASYMKEY_ID (Transact-SQL)](../../t-sql/functions/asymkey-id-transact-sql.md)   
 [SIGNBYASYMKEY (Transact-SQL)](../../t-sql/functions/signbyasymkey-transact-sql.md)   
 [CREATE ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)   
 [DROP ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
