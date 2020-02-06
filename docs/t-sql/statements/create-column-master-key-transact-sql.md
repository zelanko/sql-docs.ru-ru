---
title: CREATE COLUMN MASTER KEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: cd6148499c6e9d906d0077632001d3fe32ce9cc3
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "73593897"
---
# <a name="create-column-master-key-transact-sql"></a>CREATE COLUMN MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Создает объект метаданных главного ключа столбца в базе данных. Элемент метаданных главного ключа столбца представляет ключ, хранящийся во внешнем хранилище ключей. Ключ защищает (шифрует) ключи шифрования столбцов, когда вы используете [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md) или [Always Encrypted с безопасными анклавами](../../relational-databases/security/encryption/always-encrypted-enclaves.md). Использование нескольких главных ключей столбца позволяет регулярно сменять их для повышения безопасности. Создайте главный ключ столбца в хранилище ключей и связанный с ним объект метаданных в базе данных с помощью обозревателя объектов в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью PowerShell. Подробные сведения см. в статье [Общие сведения об управлении ключами для постоянного шифрования](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md).  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
 

> [!IMPORTANT]
> Для создания ключей с поддержкой анклава (с вычислениями ENCLAVE_COMPUTATIONS) требуется [шифрование Always Encrypted с безопасными анклавами](../../relational-databases/security/encryption/always-encrypted-enclaves.md).

## <a name="syntax"></a>Синтаксис  

``` sql 
CREATE COLUMN MASTER KEY key_name   
    WITH (  
        KEY_STORE_PROVIDER_NAME = 'key_store_provider_name',  
        KEY_PATH = 'key_path'   
        [,ENCLAVE_COMPUTATIONS (SIGNATURE = signature)]
         )   
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
*key_name*  
Имя главного ключа столбца в базе данных.  
  
*key_store_provider_name*  
Указывает имя поставщика хранилища ключей. Поставщиком хранилища ключей называется программный компонент на стороне клиента, который содержит хранилище ключей с главным ключом столбца. 

Драйвер клиента с поддержкой Always Encrypted выполняет следующие действия:

- принимает имя поставщика хранилища ключей; 
- ищет нужный поставщик хранилища ключей в своем реестре поставщиков хранилищ ключей; 

затем он применяет поставщик для расшифровки ключей шифрования столбцов. Ключи шифрования столбцов шифруются главным ключом столбца. Главный ключ столбца хранится в базовом хранилище ключей. Затем значение ключа шифрования столбца в виде открытого текста используется для шифрования параметров запроса, соответствующих зашифрованным столбцам базы данных. Он также нужен для расшифровки результатов запроса из зашифрованных столбцов.  
  
Библиотеки драйвера клиента с поддержкой Always Encrypted включают в себя поставщики хранилища ключей для распространенных хранилищ ключей.   
  
Набор доступных поставщиков зависит от типа и версии драйвера клиента. Сведения о конкретных драйверах см. в документации по Always Encrypted: [Разработка приложений с помощью Always Encrypted](../../relational-databases/security/encryption/always-encrypted-client-development.md).


В следующей таблице показаны имена системных поставщиков.  
  
|Имя поставщика хранилища ключей|Базовое хранилище ключей|  
    |-----------------------------|--------------------------|
    |'MSSQL_CERTIFICATE_STORE'|Хранилище сертификатов Windows| 
    |'MSSQL_CSP_PROVIDER'|Хранилище, например аппаратный модуль безопасности (HSM), которое поддерживает интерфейс Microsoft CryptoAPI.|
    |'MSSQL_CNG_STORE'|Хранилище, например аппаратный модуль безопасности (HSM), с поддержкой API шифрования следующего поколения.|  
    |AZURE_KEY_VAULT|См. статью [Приступая к работе с хранилищем ключей Azure](https://azure.microsoft.com/documentation/articles/key-vault-get-started/).|  
    |MSSQL_JAVA_KEYSTORE| Хранилище ключей Java.}
  

Вы можете настроить пользовательский поставщик хранилища ключей в драйвере клиента Always Encrypted, чтобы хранить главные ключи столбцов, для которых нет встроенного поставщика хранилища ключей. Обратите внимание на то, что имена пользовательских поставщиков хранилища ключей не могут начинаться с префикса MSSQL_, так как он зарезервирован для поставщиков хранилищ ключей [!INCLUDE[msCoName](../../includes/msconame-md.md)]. 

  
key_path  
Путь к ключу в хранилище главных ключей столбцов. Путь к ключу должен быть допустимым для каждого клиентского приложения, которое будет шифровать или расшифровывать данные. Данные хранятся в столбце, который (косвенно) защищен главным ключом столбца. Клиентскому приложению нужен доступ к этому ключу. Формат пути к ключу зависит от поставщика хранилища ключей. Ниже представлен список форматов путей к ключам для системных поставщиков хранилища ключей Майкрософт.  
  
-   **Имя поставщика:** MSSQL_CERTIFICATE_STORE  
  
    **Формат пути к ключу:** *Имя_хранилища_сертификатов*/*Расположение_хранилища_сертификатов*/*Отпечаток_сертификата*  
  
     Где:  
  
    *РасположениеХранилищаСертификатов*  
    Расположение хранилища сертификатов: текущий пользователь или локальный компьютер. Дополнительные сведения см. в статье [Хранилища сертификатов "Локальный компьютер" и "Текущий пользователь"](https://msdn.microsoft.com/library/windows/hardware/ff548653.aspx).  
  
    *ИмяХранилищаСертификатов*  
    Имя хранилища сертификатов, например My.  
  
    *ОтпечатокСертификата*  
    Отпечаток сертификата.  
  
    **Примеры:**  
  
    ```  
    N'CurrentUser/My/BBF037EC4A133ADCA89FFAEC16CA5BFA8878FB94'  
  
    N'LocalMachine/My/CA5BFA8878FB94BBF037EC4A133ADCA89FFAEC16'  
    ```  
  
-   **Имя поставщика:** MSSQL_CSP_PROVIDER  
  
    **Формат пути к ключу:** *Имя_поставщика*/*Идентификатор_ключа*  
  
    Где:  
  
    *ProviderName*  
    Имя поставщика службы шифрования (CSP) с поддержкой CAPI, который предоставляет хранилище главных ключей столбцов. Если в качестве хранилища ключей используется модуль HSM, здесь следует указать имя поставщика службы шифрования, предоставляемого поставщиком модуля HSM. Поставщик должен быть установлен на клиентском компьютере.  
  
    *ИдентификаторКлюча*  
    Идентификатор ключа, используемого в качестве главного ключа столбца, в хранилище ключей.  
  
    **Примеры:**  
  
    ```  
    N'My HSM CSP Provider/AlwaysEncryptedKey1'  
    ```  
  
-   **Имя поставщика:** MSSQL_CNG_STORE  
  
    **Формат пути к ключу:** *Имя_поставщика*/*Идентификатор_ключа*  
  
    Где:  
  
    *ProviderName*  
    Имя поставщика хранилища ключей с поддержкой API шифрования следующего поколения, который предоставляет хранилище главных ключей столбцов. Если в качестве хранилища ключей используется модуль HSM, здесь следует указать имя поставщика хранилища ключей, предоставляемого изготовителем модуля HSM. Поставщик должен быть установлен на клиентском компьютере.  
  
    *ИдентификаторКлюча*  
    Идентификатор ключа, используемого в качестве главного ключа столбца, в хранилище ключей.  
  
    **Примеры:**  
  
    ```  
    N'My HSM CNG Provider/AlwaysEncryptedKey1'  
    ```  

-   **Имя поставщика:** AZURE_KEY_STORE  
  
    **Формат пути к ключу:** *KeyUrl*  
  
    Где:  
  
    *KeyUrl*  
    URL-адрес ключа в Azure Key Vault.

ENCLAVE_COMPUTATIONS  
Указывает, что главный ключ столбца поддерживает анклав. Все ключи шифрования столбцов, зашифрованные с помощью главного ключа столбца, можно предоставить в совместный доступ для безопасного анклава на стороне сервера и использовать их для вычислений внутри анклава. Дополнительные сведения см. в статье [Always Encrypted с безопасными анклавами](../../relational-databases/security/encryption/always-encrypted-enclaves.md).

*signature*  
Двоичный литерал, полученный путем подписывания *пути к ключу* и значения параметра ENCLAVE_COMPUTATIONS главным ключом столбца. Эта подпись отражает, включен ли параметр ENCLAVE_COMPUTATIONS. Подпись защищает подписанные значения от изменений неавторизованными пользователями. Драйвер клиента с включенной поддержкой шифрования Always Encrypted проверяет подпись и возвращает ошибку в приложение, если подпись недопустима. Подпись должна быть создана с помощью средств на стороне клиента. Дополнительные сведения см. в статье [Always Encrypted с безопасными анклавами](../../relational-databases/security/encryption/always-encrypted-enclaves.md).
  
  
## <a name="remarks"></a>Remarks  

Элемент метаданных главного ключа столбца следует создать, прежде чем создавать элемент метаданных ключа шифрования столбца в базе данных и применять Always Encrypted для шифрования столбцов в базе данных. Элемент главного ключа столбца в метаданных не содержит фактического значения главного ключа столбца. Главный ключ столбца должен храниться во внешнем хранилище ключей столбца (за пределами SQL Server). Имя поставщика хранилища ключей и путь к главному ключу столбца в метаданных должны быть допустимыми для клиентского приложения. Клиентскому приложению следует использовать главный ключ столбца для расшифровки ключа шифрования столбца. Ключ шифрования столбца шифруется с помощью главного ключа столбца. Клиентскому приложению также нужно выполнять запросы по зашифрованным столбцам.

Для управления главным ключами столбцов рекомендуется использовать такие средства, как SQL Server Management Studio (SSMS) или PowerShell. Такие средства создают подписи (если используется Always Encrypted с безопасными анклавами) и автоматически выдают инструкции `CREATE COLUMN MASTER KEY` для создания объектов метаданных ключа шифрования столбцов. См. разделы [Подготовка ключей Always Encrypted с помощью SQL Server Management Studio](../../relational-databases/security/encryption/configure-always-encrypted-keys-using-ssms.md) и [Подготовка ключей Always Encrypted с помощью PowerShell](../../relational-databases/security/encryption/configure-always-encrypted-keys-using-powershell.md). 

  
## <a name="permissions"></a>Разрешения  
Необходимо разрешение **ALTER ANY COLUMN MASTER KEY**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-column-master-key"></a>A. Создание главного ключа столбца  
Следующий пример создает элемент метаданных главного ключа столбца для главного ключа столбца. Главный ключ столбца сохраняется в хранилище сертификатов, чтобы предоставить доступ к нему клиентским приложениям, которые используют поставщик MSSQL_CERTIFICATE_STORE.  
  
```sql  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
     KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',   
     KEY_PATH = 'Current User/Personal/f2260f28d909d21c642a3d8e0b45a830e79a1420'  
   );  
```  
  
Создайте элемент метаданных главного ключа столбца для главного ключа столбца. Клиентские приложения, которые используют поставщик MSSQL_CNG_STORE, получат доступ к главному ключу столбца:  
  
```sql  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'MSSQL_CNG_STORE',    
    KEY_PATH = N'My HSM CNG Provider/AlwaysEncryptedKey'  
);  
```  
  
Создайте элемент метаданных главного ключа столбца для главного ключа столбца. Главный ключ столбца сохраняется в Azure Key Vault, чтобы предоставить доступ к нему клиентским приложениям, которые используют поставщик AZURE_KEY_VAULT.  
  
```sql  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'AZURE_KEY_VAULT',  
    KEY_PATH = N'https://myvault.vault.azure.net:443/keys/  
        MyCMK/4c05f1a41b12488f9cba2ea964b6a700');  
```  
  
Создайте элемент метаданных главного ключа столбца для главного ключа столбца. Главный ключ столбца сохраняется в пользовательском хранилище главных ключей столбцов.  
  
```sql  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = 'CUSTOM_KEY_STORE',    
    KEY_PATH = 'https://contoso.vault/sales_db_tce_key'  
);  
```  
### <a name="b-creating-an-enclave-enabled-column-master-key"></a>Б. Создание главного ключа столбца с поддержкой анклава  
Следующий пример создает элемент метаданных главного ключа столбца для главного ключа столбца с поддержкой анклава. Главный ключ столбца с поддержкой анклава сохраняется в хранилище сертификатов, чтобы предоставить доступ к нему клиентским приложениям, которые используют поставщик MSSQL_CERTIFICATE_STORE.  
  
```sql  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
     KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',   
     KEY_PATH = 'Current User/Personal/f2260f28d909d21c642a3d8e0b45a830e79a1420'  
     ENCLAVE_COMPUTATIONS (SIGNATURE = 0xA80F5B123F5E092FFBD6014FC2226D792746468C901D9404938E9F5A0972F38DADBC9FCBA94D9E740F3339754991B6CE26543DEB0D094D8A2FFE8B43F0C7061A1FFF65E30FDDF39A1B954F5BA206AAC3260B0657232020542419990261D878318CC38EF4E853970ED69A8D4A306693B8659AAC1C4E4109DE5EB148FD0E1FDBBC32F002C1D8199D313227AD689279D8DEEF91064DF122C19C3767C463723AB663A6F8412AE17E745922C0E3A257EAEF215532588ACCBD440A03C7BC100A38BD0609A119E1EF7C5C6F1B086C68AB8873DBC6487B270340E868F9203661AFF0492CEC436ABF7C4713CE64E38CF66C794B55636BFA55E5B6554AF570CF73F1BE1DBD)
  );  
```  
  
Создайте элемент метаданных главного ключа столбца для главного ключа столбца с поддержкой анклава. Главный ключ столбца с поддержкой анклава сохраняется в Azure Key Vault, чтобы предоставить доступ к нему клиентским приложениям, которые используют поставщик AZURE_KEY_VAULT.  
  
```sql  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'AZURE_KEY_VAULT',  
    KEY_PATH = N'https://myvault.vault.azure.net:443/keys/MyCMK/4c05f1a41b12488f9cba2ea964b6a700');
    ENCLAVE_COMPUTATIONS (SIGNATURE = 0xA80F5B123F5E092FFBD6014FC2226D792746468C901D9404938E9F5A0972F38DADBC9FCBA94D9E740F3339754991B6CE26543DEB0D094D8A2FFE8B43F0C7061A1FFF65E30FDDF39A1B954F5BA206AAC3260B0657232020582413990261D878318CC38EF4E853970ED69A8D4A306693B8659AAC1C4E4109DE5EB148FD0E1FDBBC32F002C1D8199D313227AD689279D8DEEF91064DF122C19C3767C463723AB663A6F8412AE17E745922C0E3A257EAEF215532588ACCBD440A03C7BC100A38BD0609A119E1EF7C5C6F1B086C68AB8873DBC6487B270340E868F9203661AFF0492CEC436ABF7C4713CE64E38CF66C794B55636BFA55E5B6554AF570CF73F1BE1DBD)
  );
```  
  
## <a name="see-also"></a>См. также:
 
* [DROP COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/drop-column-master-key-transact-sql.md)   
* [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](../../t-sql/statements/create-column-encryption-key-transact-sql.md)
* [sys.column_master_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)
* [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
* [Always Encrypted с безопасными анклавами](../../relational-databases/security/encryption/always-encrypted-enclaves.md)   
* [Общие сведения об управлении ключами для постоянного шифрования](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)   
* [Управление ключами для Always Encrypted с безопасными анклавами](../../relational-databases/security/encryption/always-encrypted-enclaves-manage-keys.md)   
  
