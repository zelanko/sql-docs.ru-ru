---
title: "Создание главного ключа СТОЛБЦА (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SQL13.SWB.NEWCOLUMNMASTERKEYDEF.GENERAL.F1
- SQL13.SWB.COLUMNMASTERKEYDEF.GENERAL.F1
- CREATE COLUMN MASTER KEY
- COLUMN MASTER KEY
- CREATE_COLUMN_MASTER_KEY_TSQL
- COLUMN_MASTER_KEY_TSQL
- SQL13.SWB.NEWCOLUMNMASTERKEY.GENERAL.F1
- SQL13.SWB.COLUMNMASTERKEY.GENERAL.F1
dev_langs:
- TSQL
helpviewer_keywords:
- column master key definition
- column master key, create
- CREATE COLUMN MASTER KEY statement
- Always Encrypted, create column master key
ms.assetid: f8926b95-e146-4e3f-b56b-add0c0d0a30e
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 871acb46898a9a62b25062f69d4e51bf28658f06
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-column-master-key-transact-sql"></a>CREATE COLUMN MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Создает объект метаданных главного ключа столбца в базе данных. Запись метаданных главного ключа столбца, представляющий ключ, хранящихся во внешнем хранилище ключей, который используется для защиты (шифрования) ключи шифрования столбцов, при использовании [постоянного шифрования &#40; компонент Database Engine &#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md) компонентов. Разрешить несколько главных ключей столбцов для смены ключей; Периодическая Смена ключа в целях повышения безопасности. Можно создать главный ключ столбца в хранилище ключей и соответствующего объекта метаданных в базе данных с помощью обозревателя объектов в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или PowerShell. Дополнительные сведения см. в разделе [Обзор для управления ключами для постоянного шифрования](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CREATE COLUMN MASTER KEY key_name   
    WITH (  
        KEY_STORE_PROVIDER_NAME = 'key_store_provider_name',  
        KEY_PATH = 'key_path'   
         )   
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *key_name*  
 — Это имя, по которому будет доступно главного ключа столбца в базе данных.  
  
 *key_store_provider_name*  
 Задает имя поставщика хранилища ключей, что клиентский программный компонент, который инкапсулирует хранилище ключей, содержащему главный ключ столбца. Драйвер клиента с поддержкой постоянного шифрования использует имя поставщика хранилища ключей для поиска поставщика хранилища ключей в реестре драйвера поставщиков хранилища ключей. Драйвер использует поставщик для расшифровки ключей шифрования столбца, защищенных главным ключом столбца, хранящихся в базовом хранилище ключей. Значение открытого текста ключа шифрования столбца, затем используется для шифрования параметров запроса, соответствующие столбцам зашифрованной базы данных и расшифровки результатов запроса из зашифрованных столбцов.  
  
 Всегда включено шифрование клиентские библиотеки драйверов включают поставщики хранилища ключей для распространенных хранилищ ключей.   
  
Набор доступных поставщиков зависят от типа и версии драйвера клиента. См. в документации постоянного шифрования для определенного драйверов:

[Разработка приложений с помощью постоянного шифрования с поставщик .NET Framework для SQL Server](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)


Ниже таблицы захватывает имена системных поставщиков:  
  
|Имя поставщика хранилища ключей|Хранилище ключей|  
    |-----------------------------|--------------------------|
    |«MSSQL_CERTIFICATE_STORE»|Хранилище сертификатов Windows| 
    |«MSSQL_CSP_PROVIDER»|Хранилище, например аппаратного модуля безопасности (HSM), который поддерживает Microsoft CryptoAPI.|
    |«MSSQL_CNG_STORE»|Хранилище, например аппаратного модуля безопасности (HSM), который поддерживает Cryptography API: следующего поколения.|  
    |«Azure_Key_Vault»|В разделе [Приступая к работе с хранилищем ключей Azure](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)|  
  

 Можно реализовать пользовательский поставщик хранилища ключей, для хранения главных ключей столбцов в хранилище, для которого отсутствует встроенная ключ поставщика хранилища в драйвер клиента с поддержкой постоянного шифрования.  Обратите внимание, что имена пользовательские поставщики хранилища ключей не может начинаться с «MSSQL_», не является префиксом, зарезервированных для [!INCLUDE[msCoName](../../includes/msconame-md.md)] поставщики хранилища ключей. 

  
 key_path  
 Путь в главный ключ столбца ключа хранилища. Путь к ключу должен быть допустимым в контексте каждого клиентского приложения, которая ожидается для шифрования или расшифровки данных, хранящихся в столбце (косвенно) защищен главным ключом столбца, на который указывает ссылка, а клиентскому приложению нужно разрешить доступ к ключу. Формат пути к ключу зависит от поставщика хранилища ключей. Следующий список описывает формат путей ключа для конкретного поставщиков хранилища ключей системы Microsoft.  
  
-   **Имя поставщика:** MSSQL_CERTIFICATE_STORE  
  
     **Формат пути к ключу:** *CertificateStoreName*/*CertificateStoreLocation*/*CertificateThumbprint*  
  
     Где:  
  
     *CertificateStoreLocation*  
     Расположение хранилища сертификатов, который должен быть текущего пользователя или локального компьютера. Дополнительные сведения см. в разделе [хранилища сертификатов текущего пользователя и локального компьютера](https://msdn.microsoft.com/library/windows/hardware/ff548653.aspx).  
  
     *CertificateStore*  
     Имя хранилища сертификатов, например «My».  
  
     *CertificateThumbprint*  
     Отпечаток сертификата.  
  
     **Примеры:**  
  
    ```  
    N'CurrentUser/My/BBF037EC4A133ADCA89FFAEC16CA5BFA8878FB94'  
  
    N'LocalMachine/My/CA5BFA8878FB94BBF037EC4A133ADCA89FFAEC16'  
    ```  
  
-   **Имя поставщика:** MSSQL_CSP_PROVIDER  
  
     **Формат пути к ключу:** *ProviderName*/*KeyIdentifier*  
  
     Где:  
  
     *ProviderName*  
     Имя шифрования поставщика служб (CSP), реализующий CAPI, для хранилища главных ключей столбцов. Если используется аппаратный модуль безопасности в качестве хранилища ключей, это должно быть имя поставщика CSP поставщику аппаратного модуля безопасности предоставляет. Поставщик должен быть установлен на клиентском компьютере.  
  
     *KeyIdentifier*  
     Идентификатор ключа, используется в качестве главного ключа столбца, в хранилище ключей.  
  
     **Примеры:**  
  
    ```  
    N'My HSM CSP Provider/AlwaysEncryptedKey1'  
    ```  
  
-   **Имя поставщика:** MSSQL_CNG_STORE  
  
     **Формат пути к ключу:** *ProviderName*/*KeyIdentifier*  
  
     Где:  
  
     *ProviderName*  
     Имя объекта поставщик хранилища ключей (KSP), который реализует Cryptography: следующего поколения (CNG) API, для хранилища главных ключей столбцов. Если используется аппаратный модуль безопасности в качестве хранилища ключей, это должен быть имя KSP поставщику аппаратного модуля безопасности предоставляет. Поставщик должен быть установлен на клиентском компьютере.  
  
     *KeyIdentifier*  
     Идентификатор ключа, используется в качестве главного ключа столбца, в хранилище ключей.  
  
     **Примеры:**  
  
    ```  
    N'My HSM CNG Provider/AlwaysEncryptedKey1'  
    ```  

-   **Имя поставщика:** AZURE_KEY_STORE  
  
     **Формат пути к ключу:** *значение KeyUrl*  
  
     Где:  
  
     *Значение KeyUrl*  
     URL-адрес ключа в хранилище ключей Azure


Пример
 
`N'https://myvault.vault.azure.net:443/keys/MyCMK/4c05f1a41b12488f9cba2ea964b6a700'`  
  
## <a name="remarks"></a>Замечания  

Создание запись метаданных главного ключа столбца является обязательным, чтобы можно было создать запись метаданных ключа шифрования столбца, в базе данных, и перед любой столбец в базе данных могут быть зашифрованы с помощью постоянного шифрования. Обратите внимание, что запись главного ключа столбца в метаданных не содержит фактическое главного ключа столбца, который должен храниться в хранилище ключей внешний столбец (за пределами SQL Server). Имя поставщика хранилища ключей и путь к главному ключу столбца в метаданных должен быть допустимым для клиентского приложения иметь возможность использовать главный ключ столбца для расшифровки ключа шифрования столбца, зашифрованные с помощью главного ключа столбца, а также запрашивать зашифрованные столбцы.


  
## <a name="permissions"></a>Permissions  
 Требуется **ALTER ANY COLUMN MASTER KEY** разрешение.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-column-master-key"></a>A. Создание главного ключа столбца  
 При создании запись метаданных главного ключа столбца для главного ключа столбца, хранящихся в хранилище сертификатов для клиентских приложений, использующих поставщик MSSQL_CERTIFICATE_STORE для доступа к главному ключу столбца:  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
     KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',   
     KEY_PATH = 'Current User/Personal/f2260f28d909d21c642a3d8e0b45a830e79a1420'  
   );  
```  
  
 Создание запись метаданных главного ключа столбца для главного ключа столбца, доступ к которому клиентские приложения, использующие поставщика MSSQL_CNG_STORE.  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'MSSQL_CNG_STORE',    
    KEY_PATH = N'My HSM CNG Provider/AlwaysEncryptedKey'  
);  
```  
  
 Создание главного ключа столбца хранятся в хранилище ключей Azure для клиентских приложений, использующих поставщик AZURE_KEY_VAULT, чтобы получить доступ к главному ключу столбца.  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'AZURE_KEY_VAULT',  
    KEY_PATH = N'https://myvault.vault.azure.net:443/keys/  
        MyCMK/4c05f1a41b12488f9cba2ea964b6a700');  
```  
  
 При создании CMK, хранящихся в хранилище главного ключа пользовательские столбца:  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = 'CUSTOM_KEY_STORE',    
    KEY_PATH = 'https://contoso.vault/sales_db_tce_key'  
);  
```  
  
## <a name="see-also"></a>См. также:
 
* [DROP COLUMN MASTER KEY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-column-master-key-transact-sql.md)   
* [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](../../t-sql/statements/create-column-encryption-key-transact-sql.md)
* [sys.column_master_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)
* [Постоянное шифрование (компонент Database Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
* [Общие сведения об управлении ключами для постоянного шифрования](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
  

