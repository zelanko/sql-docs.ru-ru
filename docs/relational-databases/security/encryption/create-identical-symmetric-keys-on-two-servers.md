---
title: Создание идентичных симметричных ключей на двух серверах | Документация Майкрософт
ms.custom: ''
ms.date: 01/02/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- symmetric keys [SQL Server], creating
ms.assetid: a13d0b21-a43b-43c0-9c22-7ba8f3d15e80
author: aliceku
ms.author: aliceku
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d2f8de3783e7d169e1458170d10db61ad9ac680a
ms.sourcegitcommit: fa2f85b6deeceadc0f32aa7f5f4e2b6e4d99541c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/03/2019
ms.locfileid: "53997566"
---
# <a name="create-identical-symmetric-keys-on-two-servers"></a>Создание идентичных симметричных ключей на двух серверах
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В этом разделе описывается создание идентичных симметричных ключей на двух разных серверах в среде [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Для расшифровки текста необходим ключ, который был использован для его шифрования. Если шифрование и расшифровка происходят в одной и той же базе данных, ключ хранится в базе данных и доступен для шифрования и расшифровки в зависимости от разрешений. Но если шифрование и расшифровка происходят в разных базах данных или на разных серверах, ключ хранится в одной из них и недоступен для использования в другой.
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="limitations-and-restrictions"></a>Ограничения  
  
- После создания симметричный ключ должен быть зашифрован с помощью хотя бы одного из следующих средств: сертификат, пароль, симметричный ключ, асимметричный ключ или PROVIDER. Ключ может быть зашифрован более чем один раз для каждого типа шифрования. Другими словами, один симметричный ключ может быть зашифрован с использованием нескольких сертификатов, симметричных ключей и асимметричных ключей одновременно.  
  
- Если симметричный ключ шифруется с использованием пароля вместо открытого ключа главного ключа базы данных, то используется алгоритм шифрования TRIPLE DES. Поэтому ключи, созданные с помощью сильных алгоритмов шифрования, таких как AES, защищены с помощью более слабого алгоритма.  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER ANY SYMMETRIC KEY на базу данных. Если указан аргумент AUTHORIZATION, то требуется разрешение IMPERSONATE для пользователя базы данных или разрешение ALTER для роли приложения. Если для шифрования использовался сертификат или асимметричный ключ, то требуется разрешение VIEW DEFINITION для сертификата или асимметричного ключа. Симметричные ключи могут принадлежать только именам входа Windows, именам входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и ролям приложений. Симметричные ключи не могут принадлежать группам и ролям.  
  
## <a name="using-transact-sql"></a>Использование Transact-SQL  
  
### <a name="to-create-identical-symmetric-keys-on-two-different-servers"></a>Создание идентичных симметричных ключей на двух разных серверах  
  
1. В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2. На стандартной панели выберите пункт **Создать запрос**.  
  
3. Создайте ключ, выполнив следующие инструкции CREATE MASTER KEY, CREATE CERTIFICATE и CREATE SYMMETRIC KEY.  
  
    ```sql
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'My p@55w0Rd';  
    GO  
    CREATE CERTIFICATE [cert_keyProtection] WITH SUBJECT = 'Key Protection';  
    GO  
    CREATE SYMMETRIC KEY [key_DataShare] WITH  
        KEY_SOURCE = 'My key generation bits. This is a shared secret!',  
        ALGORITHM = AES_256,   
        IDENTITY_VALUE = 'Key Identity generation bits. Also a shared secret'  
        ENCRYPTION BY CERTIFICATE [cert_keyProtection];  
    GO  
    ```  
  
4. Подключитесь к отдельному экземпляру сервера, откройте новое окно запросов и выполните приведенные выше SQL-инструкции для создания того же ключа на втором сервере.  
  
5. Проверьте ключи, запустив на одном сервере вначале инструкцию OPEN SYMMETRIC KEY, а затем инструкцию SELECT.  
  
    ```sql
    OPEN SYMMETRIC KEY [key_DataShare]   
        DECRYPTION BY CERTIFICATE cert_keyProtection;  
    GO  
    SELECT encryptbykey(key_guid('key_DataShare'), 'MyData' )  
    GO  
    -- For example, the output might look like this: 0x2152F8DA8A500A9EDC2FAE26D15C302DA70D25563DAE7D5D1102E3056CE9EF95CA3E7289F7F4D0523ED0376B155FE9C3  
    ```  
  
6. На втором сервере вставьте результат выполнения инструкции SELECT в приведенный ниже программный код в качестве значения `@blob` и выполните его, чтобы убедиться, что данные расшифровываются вторым ключом.  
  
    ```sql
    OPEN SYMMETRIC KEY [key_DataShare]   
        DECRYPTION BY CERTIFICATE cert_keyProtection;  
    GO  
    DECLARE @blob varbinary(8000);  
    SET @blob = SELECT CONVERT(varchar(8000), decryptbykey(@blob));  
    GO  
    ```  
  
7. Закройте симметричные ключи на обоих серверах.  
  
    ```sql
    CLOSE SYMMETRIC KEY [key_DataShare];  
    GO  
    ```  
  
 Дополнительные сведения см. в следующих разделах:  
  
-   [CREATE MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-master-key-transact-sql.md)  
  
-   [CREATE CERTIFICATE (Transact-SQL)](../../../t-sql/statements/create-certificate-transact-sql.md)  
  
-   [CREATE SYMMETRIC KEY (Transact-SQL)](../../../t-sql/statements/create-symmetric-key-transact-sql.md)  
  
-   [ENCRYPTBYKEY (Transact-SQL)](../../../t-sql/functions/encryptbykey-transact-sql.md)  
  
-   [DECRYPTBYKEY (Transact-SQL)](../../../t-sql/functions/decryptbykey-transact-sql.md)  
  
-   [OPEN SYMMETRIC KEY (Transact-SQL)](../../../t-sql/statements/open-symmetric-key-transact-sql.md)  
