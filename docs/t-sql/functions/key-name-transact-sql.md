---
description: KEY_NAME (Transact-SQL)
title: KEY_NAME (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- KEY_NAME_TSQL
- KEY_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- KEY_NAME function
ms.assetid: 7b693e5d-2325-4bf9-9b45-ad6a23374b41
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9ccc9a860218a6fa39596faaee78908eedf6907a
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91115988"
---
# <a name="key_name-transact-sql"></a>KEY_NAME (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает имя симметричного ключа из идентификатора GUID симметричного ключа или зашифрованного текста.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
KEY_NAME ( ciphertext | key_guid )   
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *ciphertext*  
 Текст, зашифрованный симметричным ключом. Аргумент *cyphertext* имеет тип **varbinary(8000)**.  
  
 *key_guid*  
 Идентификатор GUID симметричного ключа. Аргумент *key_guid* имеет тип **uniqueidentifier**.  
  
## <a name="returned-types"></a>Возвращаемые типы  
 **varchar(128)**  
  
## <a name="permissions"></a>Разрешения  
 Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], видимость метаданных ограничивается защищаемыми объектами, которыми пользователь владеет или на которые пользователю было предоставлено разрешение. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-displaying-the-name-of-a-symmetric-key-using-the-key_guid"></a>A. Отображение имени симметричного ключа, полученное с помощью идентификатора key_guid  
 База данных **master** содержит симметричный ключ с именем ##MS_ServiceMasterKey##. В следующем примере показано, как получить идентификатор GUID ключа из динамического административного представления sys.symmetric_keys, присвоить его переменной, а затем передать эту переменную в функцию KEY_NAME, чтобы вернуть имя, соответствующее идентификатору GUID.  
  
```sql  
USE master;  
GO  
DECLARE @guid uniqueidentifier ;  
SELECT @guid = key_guid FROM sys.symmetric_keys  
WHERE name = '##MS_ServiceMasterKey##' ;  
-- Demonstration of passing a GUID to KEY_NAME to receive a name  
SELECT KEY_NAME(@guid) AS [Name of Key];  
```  
  
### <a name="b-displaying-the-name-of-a-symmetric-key-using-the-cipher-text"></a>Б. Отображение имени симметричного ключа, полученное с помощью зашифрованного текста  
 В следующем примере показан весь процесс создания симметричного ключа и загрузки данных в таблицу. После этого в примере показано, как функция KEY_NAME возвращает имя ключа после получения зашифрованного текста.  
  
```sql 
-- Create a symmetric key  
CREATE SYMMETRIC KEY TestSymKey   
   WITH ALGORITHM = AES_128,  
   KEY_SOURCE = 'The square of the hypotenuse is equal to the sum of the squares of the sides',  
   IDENTITY_VALUE = 'Pythagoras'  
   ENCRYPTION BY PASSWORD = 'pGFD4bb925DGvbd2439587y' ;  
GO  
-- Create a table for the demonstration  
CREATE TABLE DemoKey  
(IDCol INT IDENTITY PRIMARY KEY,  
SecretCol VARBINARY(256) NOT NULL)  
GO  
-- Open the symmetric key if not already open  
OPEN SYMMETRIC KEY TestSymKey   
    DECRYPTION BY PASSWORD = 'pGFD4bb925DGvbd2439587y';  
GO  
-- Insert a row into the DemoKey table  
DECLARE @key_GUID uniqueidentifier;  
SELECT @key_GUID = key_guid FROM sys.symmetric_keys  
WHERE name LIKE 'TestSymKey' ;  
INSERT INTO DemoKey(SecretCol)  
VALUES ( ENCRYPTBYKEY (@key_GUID, 'EncryptedText'))  
GO  
-- Verify the DemoKey data  
SELECT * FROM DemoKey;  
GO  
-- Decrypt the data  
DECLARE @ciphertext VARBINARY(256);  
SELECT @ciphertext = SecretCol  
FROM DemoKey WHERE IDCol = 1 ;  
SELECT CAST (  
DECRYPTBYKEY( @ciphertext)  
AS VARCHAR(100) ) AS SecretText ;  
-- Use KEY_NAME to view the name of the key  
SELECT KEY_NAME(@ciphertext) AS [Name of Key] ;  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.symmetric_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [ENCRYPTBYKEY (Transact-SQL)](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [DECRYPTBYKEYAUTOASYMKEY (Transact-SQL)](../../t-sql/functions/decryptbykeyautoasymkey-transact-sql.md)  
  
  
