---
title: sp_describe_parameter_encryption (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 07/27/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_describe_parameter_encryption
- sp_describe_parameter_encryption_TSQL
- sys.sp_describe_parameter_encryption
- sys.sp_describe_parameter_encryption_TSQL
helpviewer_keywords:
- sp_describe_parameter_encryption
ms.assetid: 706ed441-2881-4934-8d5e-fb357ee067ce
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 243207c6175f5604e7cc887bd7c67085e2d86291
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52507644"
---
# <a name="spdescribeparameterencryption-transact-sql"></a>sp_describe_parameter_encryption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Анализирует указанный [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции и его параметры, чтобы определить, какие параметры соответствуют столбцам базы данных, которые защищены с помощью функции постоянного шифрования. Возвращает метаданные шифрования для параметров, которые соответствуют зашифрованным столбцам.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_describe_parameter_encryption   
    [ @tsql = ] N'Transact-SQL_batch' ,   
    [ @params = ] N'parameters'   
[ ;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ \@tsql =] 'Transact-SQL_batch»  
 Одна или несколько инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)]. Transact SQL_batch может быть nvarchar(n) или nvarchar(max).  
  
 [ \@params =] N'parameters'  
 *\@params* обеспечивает строку объявления параметров для пакета Transact-SQL, которая напоминает sp_executesql. Параметры могут быть nvarchar(n) или nvarchar(max).  
  
 Строка, содержащая определения всех параметров, внедренных в [!INCLUDE[tsql](../../includes/tsql-md.md)]_batch. Строка должна представлять собой константу в Юникоде либо переменную в этом же формате. Определение каждого параметра состоит из имени параметра и типа данных. *n* — заполнитель, указывающий Дополнительные определения параметра. Каждый параметр, указанный в инструкции должен быть определен в  *\@params*. Если [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкция или пакет в инструкции не содержит параметров,  *\@params* не является обязательным. Значением по умолчанию для этого аргумента является NULL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 0 означает успешное завершение. Что-нибудь еще информируют о сбое.  
  
## <a name="result-sets"></a>Результирующие наборы  
 **sp_describe_parameter_encryption** возвращает два результирующих набора:  
  
-   Результирующий набор, описывающий криптографические ключи, настроенные для столбцов базы данных, параметры указанного [!INCLUDE[tsql](../../includes/tsql-md.md)] соответствующие инструкции.  
  
-   Результирующий набор, описывающие каким образом конкретные параметры должны быть зашифрованы. Этот результирующий набор ссылок ключами, описанными в первый результирующий набор.  
  
 Каждая строка первого результирующего набора описывает пару ключей; ключ шифрования зашифрованного столбца и его соответствующий главный ключ столбца.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**column_encryption_key_ordinal**|**int**|Идентификатор строки в результирующем наборе.|  
|**database_id**|**int**|Идентификатор базы данных.|  
|**column_encryption_key_id**|**int**|Идентификатор ключа шифрования столбцов. Примечание: этот идентификатор обозначает строку в [sys.column_encryption_keys &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md) представления каталога.|  
|**column_encryption_key_version**|**int**|Зарезервировано для последующего использования. В настоящее время всегда содержит 1.|  
|**column_encryption_key_metadata_version**|**binary(8)**|Метка времени, представляющий время создания ключа шифрования столбца.|  
|**column_encryption_key_encrypted_value**|**varbinary(4000)**|Зашифрованное значение ключа шифрования столбца.|  
|**column_master_key_store_provider_name**|**sysname**|Имя поставщика для хранилища ключей, который содержит главный ключ столбца, который использовался для создания зашифрованное значение ключа шифрования столбца.|  
|**column_master_key_path**|**nvarchar(4000)**|Путь к ключу главного ключа столбца, который использовался для создания зашифрованное значение ключа шифрования столбца.|  
|**column_encryption_key_encryption_algorithm_name**|**sysname**|Имя алгоритма шифрования, используемого для получения значения шифрования ключа шифрования столбца.|  
  
 Каждая строка второй результирующий набор содержит метаданные шифрования для одного параметра.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**parameter_ordinal**|**int**|Идентификатор строки в результирующем наборе.|  
|**parameter_name**|**sysname**|Имя одного из параметров, указанных в  *\@params* аргумент.|  
|**column_encryption_algorithm**|**tinyint**|Код, указывающий на алгоритм шифрования, настроенным для столбца, параметра соответствует. В настоящее время поддерживаются значения: 2 — **AEAD_AES_256_CBC_HMAC_SHA_256**.|  
|**column_encryption_type**|**tinyint**|Код, указывающий тип шифрования, настроенным для столбца, параметра соответствует. Поддерживаемыми значениями являются:<br /><br /> 0 — в виде обычного текста (столбец не зашифрован)<br /><br /> 1 — случайное шифрование<br /><br /> 2 - детерминированного шифрования.|  
|**column_encryption_key_ordinal**|**int**|Задать код строки в первый результат. Соответствующей строки описывает ключ шифрования столбца, настроенным для столбца, соответствующий параметр.|  
|**column_encryption_normalization_rule_version**|**tinyint**|Номер версии алгоритма тип нормализации.|  
  
## <a name="remarks"></a>Примечания  
 Объект [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер клиента, которые поддерживают постоянное шифрование, автоматически вызывает **sp_describe_parameter_encryption** для получения метаданных шифрования для параметризованных запросов, создаваемых приложением. Как следствие драйвер использует метаданные шифрования для шифрования значения параметров, которые соответствуют столбцам базы данных, защищенных с помощью постоянного шифрования и подставляет значения параметров открытого текста, отправленные приложением, с помощью зашифрованного значения параметров, перед отправкой запроса к ядру СУБД.  
  
## <a name="permissions"></a>Разрешения  
 Требовать **VIEW ANY COLUMN ENCRYPTION KEY DEFINITION** и **VIEW ANY COLUMN MASTER KEY DEFINITION** разрешения в базе данных.  
  
## <a name="examples"></a>Примеры  
  
```  
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
0x016E000001630075007200720065006E00740075007300650072002F006D007  
9002F00610036003600620062003000660036006400640037003000620064006  
6006600300032006200360032006400300066003800370065003300340030003  
200380038006500360066003900330030003500CA0D0CEC74ECADD1804CF991  
37B4BD06BBAB15D7EA74E0C249A779C7768A5B659E0125D24FF827F5EA8CA51  
7A8E197ECA1353BA814C2B0B2E6C8AB36E3AE6A1E972D69C3C573A963ADAB6  
686CF5D24F95FE43140C4F9AF48FBA7DF2D053F3B4A1F5693A1F905440F8015B  
DB43AF8A04BE4E045B89876A0097E5FBC4E6A3B9C3C0D278C540E46C53938B8  
C957B689C4DC095821C465C73117CBA95B758232F9E5B2FCC7950B8CA00AFE3  
74DE42847E3FBC2FDD277035A2DEF529F4B735C20D980073B4965B4542A3472  
3276A1646998FC6E1C40A3FDB6ABCA98EE2B447F114D2AC7FF8C7D51657550E  
C5C2BABFFE8429B851272086DCED94332CF18FA854C1D545A28B1EF4BE64F8E0  
35175C1650F6FC5C4702ACF99850A4542B3747EAEC0CC726E091B36CE24392D8  
01ECAA684DE344FECE05812D12CD72254A014D42D0EABDA41C89FC4F545E88B  
4B8781E5FAF40D7199D4842D2BFE904D209728ED4F527CBC169E2904F6E711FF8  
1A8F4C25382A2E778DD2A58552ED031AFFDA9D9D891D98AD82155F93C58202F  
C24A77F415D4F8EF22419D62E188AC609330CCBD97CEE1AEF8A18B0195883360  
4707FDF03B2B386487CC679D7E352D0B69F9FB002E51BCD814D077E82A09C14E  
9892C1F8E0C559CFD5FA841CEF647DAB03C8191DC46B772E94D579D8C80FE93C  
3827C9F0AE04D5325BC73111E07EEEDBE67F1E2A73580085  
);  
GO  
  
CREATE TABLE t1 (  
c1 INT ENCRYPTED WITH (  
    COLUMN_ENCRYPTION_KEY = [CEK_Auto1],   
    ENCRYPTION_TYPE = Randomized,   
    ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NULL,  
);  
  
EXEC sp_describe_parameter_encryption N'INSERT INTO t1 VALUES(@c1)',  N'@c1 INT';  
```  
  
 Вот первый результирующий набор:  
  
|column_encryption_key_ordinal|database_id|column_encryption_key_id|column_encryption_key_version|column_encryption_key_metadata_version|column_encryption_key_encrypted_value|  
|--------------------------------------|------------------|---------------------------------|--------------------------------------|------------------------------------------------|-----------------------------------------------|  
|1|5|1|1|0x99EDA60083A50000|0x016E000001630075007200720065006E00740075007300650072002F006D0079002F006100360036006200620030006600360064006400370030006200640066006600300032006200360032006400300066003800370065003300340030003200380038006500360066003900330030003500CA0D0CEC74ECADD1804CF99137B4BD06BBAB15D7EA 74E0C249A779C7768A5B659E0125D24FF827F5EA8CA517A8E197ECA1353BA814C2B0B2E6C8AB36E3AE6A1E972D69C3C573A963ADAB6686CF5D24F95FE43140C4F9AF48FBA7DF2D053F3B4A1F5693A1F905440F8015BDB43AF8A04BE4E045B89876A0097E5FBC4E6A3B9C3C0D278C540E46C53938B8C957B689C4DC095821C465C73117CBA95B758232 F9E5B2FCC7950B8CA00AFE374DE42847E3FBC2FDD277035A2DEF529F4B735C20D980073B4965B4542A34723276A1646998FC6E1C40A3FDB6ABCA98EE2B447F114D2AC7FF8C7D51657550EC5C2BABFFE8429B851272086DCED94332CF18FA854C1D545A28B1EF4BE64F8E035175C1650F6FC5C4702ACF99850A4542B3747EAEC0CC726E091B36CE2439 2D801ECAA684DE344FECE05812D12CD72254A014D42D0EABDA41C89FC4F545E88B4B8781E5FAF40D7199D4842D2BFE904D209728ED4F527CBC169E2904F6E711FF81A8F4C25382A2E778DD2A58552ED031AFFDA9D9D891D98AD82155F93C58202FC24A77F415D4F8EF22419D62E188AC609330CCBD97CEE1AEF8A18B01958833604707FDF03B2B3864 87CC679D7E352D0B69F9FB002E51BCD814D077E82A09C14E9892C1F8E0C559CFD5FA841CEF647DAB03C8191DC46B772E94D579D8C80FE93C3827C9F0AE04D5325BC73111E07EEEDBE67F1E2A73580085|  
  
 (Результаты по-прежнему.)  
  
|column_master_key_store_provider_name|column_master_key_path|column_encryption_key_encryption_algorithm_name|  
|------------------------------------------------|-------------------------------|----------------------------------------------------------|  
|MSSQL_CERTIFICATE_STORE|CurrentUser/my/A66BB0F6DD70BDFF02B62D0F87E340288E6F9305|RSA_OAEP|  
  
 Вот второй результирующий набор:  
  
|parameter_ordinal|parameter_name|column_encryption_algorithm|column_encryption_type|  
|------------------------|---------------------|-----------------------------------|------------------------------|  
|1|\@C1|1|1|  
  
 (Результаты по-прежнему.)  
  
|column_encryption_key_ordinal|column_encryption_normalization_rule_version|  
|--------------------------------------|------------------------------------------------------|  
|1|1|  
  
## <a name="see-also"></a>См. также  
 [Постоянное шифрование (компонент Database Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [Постоянное шифрование (разработка клиентских приложений)](../../relational-databases/security/encryption/always-encrypted-client-development.md)  
  
  
