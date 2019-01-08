---
title: sp_refresh_parameter_encryption (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sp_refresh_parameter_encryption
- sp_refresh_parameter_encryption_TSQL
- sys.sp_refresh_parameter_encryption
- sys.sp_refresh_parameter_encryption_TSQL
helpviewer_keywords:
- sp_refresh_parameter_encryption
- Always Encrypted, sp_refresh_parameter_encryption
ms.assetid: 00b44baf-fcf0-4095-aabe-49fa87e77316
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a9a24c843ed45a42fe4072b47c5642d81520a75e
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53214143"
---
# <a name="sprefreshparameterencryption-transact-sql"></a>sp_refresh_parameter_encryption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Обновляет метаданные Always Encrypted для параметры указанной хранимой процедуры не привязанных к схеме, определяемой пользователем функции, представления, DML триггера, триггер DDL уровня базы данных, или триггер DDL уровня сервера в текущей базе данных. 

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sys.sp_refresh_parameter_encryption [ @name = ] 'module_name' 
    [ , [ @namespace = ] '<class>' ]
[ ; ]

<class> ::=
{ DATABASE_DDL_TRIGGER | SERVER_DDL_TRIGGER }
```

## <a name="arguments"></a>Аргументы

[  **@name =** ] **"***module_name***"**   
Имя хранимой процедуры, определяемой пользователем функции, представления, триггера DML, триггера DDL уровня базы данных или триггера DDL уровня сервера. *module_name* не может быть общеязыковая среда выполнения (CLR) хранимая процедура или функция среды CLR. *module_name* не может быть привязана к схеме. *module_name* является `nvarchar`, не имеет значения по умолчанию. *module_name* может быть составным идентификатором, но может ссылаться только на объекты в текущей базе данных.

[  **@namespace =** ] **"** < класс > **"**   
Класс указанного модуля. Когда *module_name* является триггером DDL, `<class>` является обязательным. Параметр `<class>` равен `nvarchar(20)`. Допустимыми входными значениями являются `DATABASE_DDL_TRIGGER` и `SERVER_DDL_TRIGGER`.    

## <a name="return-code-values"></a>Значения кода возврата  

0 (успешное завершение) или ненулевое значение (неуспешное завершение)


## <a name="remarks"></a>Примечания

Метаданные шифрования для параметров модуля может устареть, если:   
* Свойства шифрования столбца в таблице ссылки модуля, были обновлены. Например столбец был удален и добавлен новый столбец с тем же именем, но другой тип шифрования, ключ шифрования или алгоритма шифрования.  
* Модуль ссылается на другой модуль с помощью метаданных шифрования устаревший параметр.  

При изменении свойств шифрования таблицы, `sp_refresh_parameter_encryption` должна запускаться для каких-либо модулей, прямо или косвенно ссылается на таблицу. Эта хранимая процедура может вызываться в этих модулях в любом порядке, требуя от пользователя для первого обновления внутренний модуль перед перемещением вызывающим объектам.

`sp_refresh_parameter_encryption` не влияет на любые разрешения, расширенные свойства, или `SET` параметры, связанные с объектом. 

Чтобы обновить триггер DDL уровня сервера, необходимо выполнить эту хранимую процедуру в контексте любой базы данных.

> [!NOTE]
>  Любые подписи, связанные с объектом, удаляются при выполнении `sp_refresh_parameter_encryption`.

## <a name="permissions"></a>Разрешения

Требуется `ALTER` разрешение на выполнение модуля и `REFERENCES` разрешение на все определяемые пользователем типы среды CLR и коллекций XML-схем, на которые ссылается объект.   

Если указанный модуль является триггером DDL уровня базы данных, требует `ALTER ANY DATABASE DDL TRIGGER` разрешение в текущей базе данных.    

Если указанный модуль является триггером DDL уровня сервера, требует `CONTROL SERVER` разрешение.

Для модулей, которые определяются с помощью `EXECUTE AS` предложение, `IMPERSONATE` требуется разрешение для указанного участника. Как правило, обновление объекта не изменяет его `EXECUTE AS` участника, если модуль не был определен с `EXECUTE AS USER` и имя пользователя участника теперь разрешает другому пользователю, чем во время модуль был создан.
 
## <a name="examples"></a>Примеры

В следующем примере создается таблица и процедуры, ссылающиеся на таблицу, настраивает постоянное шифрование и затем демонстрируется изменение таблицы и под управлением `sp_refresh_parameter_encryption` процедуры.  

Сначала создайте первоначальной таблицы и хранимой процедуры, ссылающиеся на таблицу.
```sql
CREATE TABLE [Patients]([PatientID] [int] IDENTITY(1,1) NOT NULL,
    [SSN] [char](11), 
    [FirstName] [nvarchar](50) NULL,
    [LastName] [nvarchar](50) NOT NULL,
    [MiddleName] [nvarchar](50) NULL,
    [StreetAddress] [nvarchar](50) NOT NULL,
    [City] [nvarchar](50) NOT NULL,
    [ZipCode] [char](5) NOT NULL,
    [State] [char](2) NOT NULL,
    [BirthDate] [date] NOT NULL,
 CONSTRAINT [PK_Patients] PRIMARY KEY CLUSTERED 
(
    [PatientID] ASC
) WITH 
    (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, 
     IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, 
     ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY];
GO

CREATE PROCEDURE [find_patient] @SSN [char](11)
AS
BEGIN
    SELECT * FROM [Patients] WHERE SSN=@SSN
END;
GO
```

Затем настройте ключей постоянного шифрования.
```sql
CREATE COLUMN MASTER KEY [CMK1]
WITH
(
       KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',
    KEY_PATH = N'CurrentUser/my/A66BB0F6DD70BDFF02B62D0F87E340288E6F9305'
);
GO

CREATE COLUMN ENCRYPTION KEY [CEK1]
WITH VALUES
(
       COLUMN_MASTER_KEY = [CMK1],
    ALGORITHM = 'RSA_OAEP',
    ENCRYPTED_VALUE = 
       0x016E000001630075007200720065006E00740075007300650072002F006D0079002F006100360036006200620030006600360064006400370030006200640066006600300032006200360032006400300066003800370065003300340030003200380038006500360066003900330030003500CA0D0CEC74ECADD1804CF99137B4BD06BBAB15D7EA74E0C249A779C7768A5B659E0125D24FF827F5EA8CA517A8E197ECA1353BA814C2B0B2E6C8AB36E3AE6A1E972D69C3C573A963ADAB6686CF5D24F95FE43140C4F9AF48FBA7DF2D053F3B4A1F5693A1F905440F8015BDB43AF8A04BE4E045B89876A0097E5FBC4E6A3B9C3C0D278C540E46C53938B8C957B689C4DC095821C465C73117CBA95B758232F9E5B2FCC7950B8CA00AFE374DE42847E3FBC2FDD277035A2DEF529F4B735C20D980073B4965B4542A34723276A1646998FC6E1C40A3FDB6ABCA98EE2B447F114D2AC7FF8C7D51657550EC5C2BABFFE8429B851272086DCED94332CF18FA854C1D545A28B1EF4BE64F8E035175C1650F6FC5C4702ACF99850A4542B3747EAEC0CC726E091B36CE24392D801ECAA684DE344FECE05812D12CD72254A014D42D0EABDA41C89FC4F545E88B4B8781E5FAF40D7199D4842D2BFE904D209728ED4F527CBC169E2904F6E711FF81A8F4C25382A2E778DD2A58552ED031AFFDA9D9D891D98AD82155F93C58202FC24A77F415D4F8EF22419D62E188AC609330CCBD97CEE1AEF8A18B01958833604707FDF03B2B386487CC679D7E352D0B69F9FB002E51BCD814D077E82A09C14E9892C1F8E0C559CFD5FA841CEF647DAB03C8191DC46B772E94D579D8C80FE93C3827C9F0AE04D5325BC73111E07EEEDBE67F1E2A73580085
);
GO
```


Наконец мы заменить столбца SSN зашифрованного столбца, а затем запускает `sp_refresh_parameter_encryption` процедуры для обновления компонентов Always Encrypted.
```sql
ALTER TABLE [Patients] DROP COLUMN [SSN];
GO

ALTER TABLE [Patients] 
    ADD [SSN] [char](11) COLLATE Latin1_General_BIN2 
    ENCRYPTED WITH 
        (COLUMN_ENCRYPTION_KEY = [CEK1], 
        ENCRYPTION_TYPE = Deterministic, 
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') 
    NOT NULL;
GO

EXEC sp_refresh_parameter_encryption [find_patient];
GO
```

## <a name="see-also"></a>См. также 

[Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
[Мастер постоянного шифрования](../../relational-databases/security/encryption/always-encrypted-wizard.md)   

