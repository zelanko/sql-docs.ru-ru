---
title: Шифрование Always Encrypted | Документация Майкрософт
ms.custom: ''
ms.date: 10/30/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Always Encrypted, cryptography system
ms.assetid: ae8226ff-0853-4716-be7b-673ce77dd370
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b0fe0e861e8139416250ffc2677230dbc2aeab6d
ms.sourcegitcommit: 312b961cfe3a540d8f304962909cd93d0a9c330b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73594406"
---
# <a name="always-encrypted-cryptography"></a>Шифрование Always Encrypted
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  В этой статье описаны алгоритмы шифрования и механизмы извлечения шифровальных материалов, которые используются в функции [Постоянное шифрование](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) баз данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)].  
  
## <a name="keys-key-stores-and-key-encryption-algorithms"></a>Ключи, хранилища ключей и алгоритмы шифрования ключей
 Технологии постоянного шифрования используют два типа ключей: главные ключи столбцов и ключи шифрования столбцов.  
  
 Главный ключ столбца — это ключ, который используется для шифрования других ключей. Он находится под контролем клиента и хранится во внешнем хранилище ключей. Драйвер клиента с поддержкой постоянного шифрования взаимодействует с хранилищем ключей через поставщика хранилища главного столбца ключа, который может быть либо частью библиотеки драйверов (системный поставщик или поставщик [!INCLUDE[msCoName](../../../includes/msconame-md.md)]), либо частью клиентского приложения (пользовательский поставщик). На данный момент клиентские библиотеки драйверов включают поставщики хранилища ключей [!INCLUDE[msCoName](../../../includes/msconame-md.md)] для [хранилища сертификатов Windows](/windows/desktop/SecCrypto/using-certificate-stores) и аппаратные модули безопасности (HSM). Текущий список поставщиков см. в статье [CREATE COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-column-master-key-transact-sql.md). Разработчик приложения может задать пользовательского поставщика для произвольного хранилища.  
  
 Ключ шифрования столбца — это ключ шифрования содержимого (например, ключ, используемый для защиты данных). Он защищен главным ключом столбца.  
  
 Все поставщики хранилища главного столбца ключа [!INCLUDE[msCoName](../../../includes/msconame-md.md)] шифруют ключи шифрования столбца при помощи ключа RSA, используя оптимальное асимметричное шифрование с дополнением (RSA-OAEP). Поставщик хранилища ключей, поддерживающий Microsoft Cryptography API: Следующее поколение (CNG) в .NET Framework ([класс SqlColumnEncryptionCngProvider](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncngprovider.aspx)) использует параметры по умолчанию, указанные в RFC 8017, раздел A.2.1. В этих параметрах по умолчанию используется хэш-функция SHA-1 и функция генерации маски MGF1 с помощью SHA-1. Все остальные поставщики хранилищ ключей используют SHA-256. 
  
## <a name="data-encryption-algorithm"></a>Алгоритм шифрования данных  
 Для шифрования данных в базе данных в технологии постоянного шифрования данных используется алгоритм **AEAD_AES_256_CBC_HMAC_SHA_256** .  
  
 **AEAD_AES_256_CBC_HMAC_SHA_256** является производным от проекта спецификации, расположенного по адресу [https://tools.ietf.org/html/draft-mcgrew-aead-aes-cbc-hmac-sha2-05](https://tools.ietf.org/html/draft-mcgrew-aead-aes-cbc-hmac-sha2-05). В нем используется схема аутентифицированного шифрования с присоединенными данными, при которой сначала выполняется шифрование сообщения, а затем проверка подлинности. То есть открытый текст сначала шифруется, а затем на основе полученного зашифрованного текста создается имитовставка MAC.  
  
 Чтобы скрыть шаблоны, в алгоритме **AEAD_AES_256_CBC_HMAC_SHA_256** используется метод применения блочного шифра, в котором исходные значения шифруются с использованием вектора инициализации (IV). Полное описание режима CBC можно найти по адресу [ https://csrc.nist.gov/publications/nistpubs/800-38a/sp800-38a.pdf ](https://csrc.nist.gov/publications/nistpubs/800-38a/sp800-38a.pdf).  
  
 Алгоритм**AEAD_AES_256_CBC_HMAC_SHA_256** вычисляет значение зашифрованного текста для заданного значения открытого текста с помощью следующих шагов.  
  
### <a name="step-1-generating-the-initialization-vector-iv"></a>Шаг 1. Создание вектора инициализации  
 Технология постоянного шифрования поддерживает два метода шифрования с помощью алгоритма **AEAD_AES_256_CBC_HMAC_SHA_256**:  
  
-   случайное шифрование;  
  
-   Детерминированное  
  
 При выполнении случайного шифрования вектор инициализации создается произвольно. Во время шифрования открытого текста каждый раз создается другой зашифрованный текст. Это предотвращает утечку информации.  
  
```  
When using randomized encryption: IV = Generate cryptographicaly random 128bits  
```  
  
 При детерминированном шифровании вектор инициализации не создается произвольно. Он извлекается из значения открытого текста с помощью следующего алгоритма:  
  
```  
When using deterministic encryption: IV = HMAC-SHA-256( iv_key, cell_data ) truncated to 128 bits.  
```  
  
 Ключ вектора инициализации извлекается из ключа шифрования столбца следующим образом:  
  
```  
iv_key = HMAC-SHA-256(CEK, "Microsoft SQL Server cell IV key" + algorithm + CEK_length)  
```  
  
 Чтобы привести один блок данных в соответствие с требованиями вектора инициализации, значение HMAC сокращается.
Как результат, при выполнении детерминированного шифрования всегда создается один зашифрованный текст для значений открытого текста. Это позволяет определить одинаковые значения открытого текста, сравнив соответствующие значения зашифрованного текста. Благодаря предотвращению раскрытия информации система базы данных поддерживает возможность сравнения значений зашифрованного столбца на равенство.  
  
 По сравнению с другими способами шифрования (например, использования предварительно определенного значения вектора инициализации), метод детерминированного шифрования более эффективно скрывает шаблоны.  
  
### <a name="step-2-computing-aes_256_cbc-ciphertext"></a>Шаг 2. Вычисление зашифрованного текста AES_256_CBC  
 После вычисления вектора инициализации создается зашифрованный текст **AES_256_CBC** :  
  
```  
aes_256_cbc_ciphertext = AES-CBC-256(enc_key, IV, cell_data) with PKCS7 padding.  
```  
  
 Ключ шифрования извлекается из ключа шифрования столбца следующим образом:  
  
```  
enc_key = HMAC-SHA-256(CEK, "Microsoft SQL Server cell encryption key" + algorithm + CEK_length )  
```  
  
### <a name="step-3-computing-mac"></a>Шаг 3. Вычисление имитовставки  
 Вычисление имитовставки происходит с помощью следующего алгоритма:  
  
```  
MAC = HMAC-SHA-256(mac_key, versionbyte + IV + Ciphertext + versionbyte_length)  
```  
  
 Где:  
  
```  
versionbyte = 0x01 and versionbyte_length = 1
mac_key = HMAC-SHA-256(CEK, "Microsoft SQL Server cell MAC key" + algorithm + CEK_length)  
```  
  
### <a name="step-4-concatenation"></a>Шаг 4. Concatenation  
 Зашифрованное значение создается путем объединения байтовой версии алгоритма, кода проверки подлинности сообщения, значения вектора инициализации и зашифрованного текста AES_256_CBC.  
  
```  
aead_aes_256_cbc_hmac_sha_256 = versionbyte + MAC + IV + aes_256_cbc_ciphertext  
```  
  
## <a name="ciphertext-length"></a>Длина зашифрованного текста  
 Длина (в байтах) конкретных компонентов зашифрованного текста **AEAD_AES_256_CBC_HMAC_SHA_256** :  
  
-   versionbyte: 1  
  
-   MAC: 32  
  
-   IV: 16  
  
-   aes_256_cbc_ciphertext — `(FLOOR (DATALENGTH(cell_data)/ block_size) + 1)* block_size`, где:  
  
    -   block_size — 16 байт;  
  
    -   cell_data — значение открытого текста.  
  
     Таким образом, минимальный размер aes_256_cbc_ciphertext составляет 1 блок. Это равно 16 байтам.  
  
 Длину зашифрованного текста после шифрования значений заданного открытого текста (cell_data) можно вычислить по следующей формуле:  
  
```  
1 + 32 + 16 + (FLOOR(DATALENGTH(cell_data)/16) + 1) * 16  
```  
  
 Пример:  
  
-   После шифрования 4-байтовое значение открытого текста типа **int** станет длинным двоичным значением размером 65 байт.  
  
-   После шифрования 2000-байтовое значение открытого текста типа **nchar(1000)** станет длинным двоичным значением размером 2065 байт.  
  
 Следующая таблица содержит полный список типов данных и длину зашифрованного текста для каждого типа.  
  
|Тип данных|Длина зашифрованного текста (в байтах)|  
|---------------|---------------------------------|  
|**bigint**|65|  
|**binary**|Возможны разные варианты. Рассчитывается по формуле выше.|  
|**bit**|65|  
|**char**|Возможны разные варианты. Рассчитывается по формуле выше.|  
|**date**|65|  
|**datetime**|65|  
|**datetime2**|65|  
|**datetimeoffset**|65|  
|**decimal**|81|  
|**float**|65|  
|**geography**|Не поддерживается.|  
|**geometry**|Не поддерживается.|  
|**hierarchyid**|Не поддерживается.|  
|**image**|Не поддерживается.|  
|**int**|65|  
|**money**|65|  
|**nchar**|Возможны разные варианты. Рассчитывается по формуле выше.|  
|**ntext**|Не поддерживается.|  
|**numeric**|81|  
|**nvarchar**|Возможны разные варианты. Рассчитывается по формуле выше.|  
|**real**|65|  
|**smalldatetime**|65|  
|**smallint**|65|  
|**smallmoney**|65|  
|**sql_variant**|Не поддерживается.|  
|**sysname**|Не поддерживается.|  
|**text**|Не поддерживается.|  
|**time**|65|  
|**timestamp**<br /><br /> (**rowversion**)|Не поддерживается.|  
|**tinyint**|65|  
|**uniqueidentifier**|81|  
|**varbinary**|Возможны разные варианты. Рассчитывается по формуле выше.|  
|**varchar**|Возможны разные варианты. Рассчитывается по формуле выше.|  
|**xml**|Не поддерживается.|  
  
## <a name="net-reference"></a>Справочник по .NET  
 Дополнительные сведения об алгоритмах, описанных в этой статье, см. в файлах **SqlAeadAes256CbcHmac256Algorithm.cs**, **SqlColumnEncryptionCertificateStoreProvider.cs** и **SqlColumnEncryptionCertificateStoreProvider.cs** в [справочнике по .NET](https://referencesource.microsoft.com/).  
  
## <a name="see-also"></a>См. также:  
 - [Постоянное шифрование](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 - [Разработка приложений с помощью Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-client-development.md)  
  
  
