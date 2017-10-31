---
title: "СОЗДАЙТЕ СЕРТИФИКАТ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CERTIFICATE
- CREATE_CERTIFICATE_TSQL
- sql13.swb.createcertificate.f1
- CERTIFICATE_TSQL
- CREATE CERTIFICATE
- sql13.swb.certificateproperties.f1
dev_langs:
- TSQL
helpviewer_keywords:
- encryption [SQL Server], certificates
- certificates [SQL Server], adding
- certificates [SQL Server]
- adding certificates
- cryptography [SQL Server], certificates
- CREATE CERTIFICATE statement
ms.assetid: a4274b2b-4cb0-446a-a956-1c8e6587515d
caps.latest.revision: 74
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8753e820278eb04fff6f12e405d766fff5292e58
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-certificate-transact-sql"></a>Инструкция CREATE CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Добавляет сертификат в базу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Эта функция несовместима с экспортом базы данных с использованием платформы приложения уровня данных (DACFx). Необходимо удалить все сертификаты перед экспортом.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
CREATE CERTIFICATE certificate_name [ AUTHORIZATION user_name ]   
    { FROM <existing_keys> | <generate_new_keys> }  
    [ ACTIVE FOR BEGIN_DIALOG =  { ON | OFF } ]  
  
<existing_keys> ::=   
    ASSEMBLY assembly_name  
    | {   
        [ EXECUTABLE ] FILE = 'path_to_file'  
        [ WITH PRIVATE KEY ( <private_key_options> ) ]   
      }  
    | {   
        BINARY = asn_encoded_certificate  
        [ WITH PRIVATE KEY ( <private_key_options> ) ]  
      }  
<generate_new_keys> ::=   
    [ ENCRYPTION BY PASSWORD = 'password' ]   
    WITH SUBJECT = 'certificate_subject_name'   
    [ , <date_options> [ ,...n ] ]   
  
<private_key_options> ::=  
      {   
        FILE = 'path_to_private_key'  
         [ , DECRYPTION BY PASSWORD = 'password' ]  
         [ , ENCRYPTION BY PASSWORD = 'password' ]    
      }  
    |  
      {   
        BINARY = private_key_bits  
         [ , DECRYPTION BY PASSWORD = 'password' ]  
         [ , ENCRYPTION BY PASSWORD = 'password' ]    
      }  
  
<date_options> ::=  
    START_DATE = 'datetime' | EXPIRY_DATE = 'datetime'  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
CREATE CERTIFICATE certificate_name   
    { <generate_new_keys> | FROM <existing_keys> }  
    [ ; ]  
  
<generate_new_keys> ::=   
    WITH SUBJECT ='certificate_subject_name'   
    [ , <date_options> [ ,...n ] ]   
  
<existing_keys> ::=   
    {   
      FILE ='path_to_file'  
      WITH PRIVATE KEY   
         (   
           FILE ='path_to_private_key'  
           , DECRYPTION BY PASSWORD ='password'   
         )  
    }  
  
<date_options> ::=  
    START_DATE ='datetime' | EXPIRY_DATE ='datetime'  
```  
  
## <a name="arguments"></a>Аргументы  
 *имя_сертификата*  
 — Это имя для сертификата в базе данных.  
  
 АВТОРИЗАЦИЯ *имя_пользователя*  
 — Это имя пользователя, которому принадлежит этот сертификат.  
  
 СБОРКА *assembly_name*  
 Указывает подписанную сборку, уже загруженную в базу данных.  
  
 [ИСПОЛНЯЕМЫЙ ФАЙЛ] ФАЙЛ = "*путь_к_файлу*"  
 Указывает полный путь, включающий имя файла, к файлу, зашифрованному по правилам DER и содержащему сертификат. Если используется параметр EXECUTABLE, то файл является библиотекой DLL, заверенной с использованием данного сертификата. *путь_к_файлу* может быть локальным путем или UNC-путь в сетевую папку. К файлу осуществляется в контексте безопасности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи службы. Эта учетная запись должна иметь соответствующие разрешения на доступ в файловой системе.  
  
 WITH PRIVATE KEY  
 Указывает, что закрытый ключ сертификата загружен в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это предложение действительно лишь в случае, когда сертификат создается из файла. Для загрузки закрытого ключа сборки, используйте [ALTER CERTIFICATE](../../t-sql/statements/alter-certificate-transact-sql.md).  
  
 ФАЙЛ = "*path_to_private_key*"  
 Указывает полный путь к закрытому ключу, включая имя файла. *path_to_private_key* может быть локальным путем или UNC-путь в сетевую папку. К файлу осуществляется в контексте безопасности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи службы. Эта учетная запись должна иметь соответствующие разрешения на доступ в файловой системе.  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
 asn_encoded_certificate  
 Биты закодированного сертификата ASN, указанного в качестве двоичной константы.  
  
 ДВОИЧНЫЙ =*private_key_bits*  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Биты закрытого ключа, указанного в качестве двоичной константы. Биты могут находиться в зашифрованном виде. Если они зашифрованы, пользователь должен предоставить пароль для расшифровки. Проверка политики паролей для данного пароля не выполняется. Биты закрытого ключа должны быть в формате файла PVK.  
  
 DECRYPTION BY PASSWORD = "*key_password*"  
 Указывает пароль, необходимый для расшифровки закрытого ключа, получаемого из файла. Это предложение необязательно, если закрытый ключ защищен пустым паролем. Не рекомендуется сохранять закрытый ключ в файл без защиты паролем. Если требуется пароль, но пароль не указан, инструкция завершится ошибкой.  
  
 ENCRYPTION BY PASSWORD = "*пароль*"  
 Указывает пароль, используемый для шифрования закрытого ключа. Этот аргумент нужно использовать лишь в том случае, если необходимо зашифровать сертификат с помощью пароля. Если это предложение опущено, закрытый ключ шифруется с помощью главного ключа базы данных. *пароль* должен соответствовать требованиям политики паролей Windows компьютера, на котором выполняется экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Password Policy](../../relational-databases/security/password-policy.md).  
  
 Тема = "*certificate_subject_name*"  
 Термин *субъекта* ссылается на поле в метаданных сертификата, как определено в стандарте X.509. Субъект должен быть не более 64 символов, и это ограничение действует для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в Linux. Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в Windows, субъекта может содержать до 128 символов. Вопросы, которые больше 128 символов усекаются, если они хранятся в каталоге, но в большом двоичном объекте (BLOB), содержащий сертификат хранит полное имя субъекта.  
  
 Start_date = "*datetime*"  
 Дата, начиная с которой сертификат действителен. Если не указан, START_DATE устанавливается равной текущей дате. Значение START_DATE имеет формат времени UTC. Это значение можно указать в любом формате, который можно преобразовать в формат даты и времени.  
  
 EXPIRY_DATE = "*datetime*"  
 Дата истечения срока действия сертификата. Если не указана, EXPIRY_DATE будет присвоено через год после START_DATE. Значение EXPIRY_DATE имеет формат времени UTC. Это значение можно указать в любом формате, который можно преобразовать в формат даты и времени. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Компонент Service Broker проверяет дату истечения срока действия. Однако срок действия не выполняется, когда этот сертификат используется для шифрования.  
  
 ACTIVE FOR BEGIN_DIALOG = { **ON** | {OFF}  
 Делает сертификат доступным для инициатора диалога с компонентом [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Значение по умолчанию — ON.  
  
## <a name="remarks"></a>Замечания  
 Сертификат — это защищаемый объект уровня базы данных, соответствующий стандарту X.509 и поддерживающий поля X.509 V1. Инструкция CREATE CERTIFICATE может загрузить сертификат из файла или сборки. Она также может создать пару ключей и самостоятельно подписанный сертификат.  
  
 Закрытый ключ должен быть \<= 2500 байт в зашифрованном виде. Закрытые ключи, созданные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 1024 бит long с использованием [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и 2048 бит длиннее начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Закрытые ключи, импортированные из внешнего источника, имеют минимальную длину в 384 бит и максимальную длину в 4 096 бит. Длина импортируемого закрытого ключа должна быть кратной 64 бит. Для сертификатов, используемых для прозрачного шифрования данных, размер закрытого ключа ограничен 3456 битами.  
  
 Хранится весь серийный номер сертификата, но отображаются только первые 16 байтов в представлении каталога sys.certificates.  
  
 Всего поля издателя сертификата сохраняется, но только первые 884 байты sys.certificates представления каталога.  
  
 Закрытый ключ должен соответствовать открытый ключ, заданный *имя_сертификата*.  
  
 При создании сертификата из контейнера загрузка закрытого ключа необязательна. Однако в случае, когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает самостоятельно подписанный сертификат, закрытый ключ создается всегда. По умолчанию закрытый ключ шифруется главным ключом базы данных. Если главный ключ базы данных не существует, а пароль не указан, инструкция завершается ошибкой.  
  
 Параметр ENCRYPTION BY PASSWORD не требуется, если закрытый ключ зашифрован главным ключом базы данных. Используйте этот параметр только в том случае, если закрытый ключ зашифрован с паролем. Если пароль не указан, закрытый ключ будет зашифрован с использованием главного ключа базы данных. Если не удается открыть главный ключ базы данных, отсутствие этого предложения вызовет ошибку.  
  
 Если закрытый ключ зашифрован главным ключом базы данных, указывать пароль расшифровки не требуется.  
  
> [!NOTE]  
>  Встроенные функции шифрования и цифровой подписи не проверяют даты истечения срока действия сертификатов. Пользователи этих функций должны самостоятельно определять, когда следует проверять сроки действия сертификатов.  
  
 Двоичное описание сертификата можно создать с помощью [CERTENCODED &#40; Transact-SQL &#41; ](../../t-sql/functions/certencoded-transact-sql.md) и [CERTPRIVATEKEY &#40; Transact-SQL &#41; ](../../t-sql/functions/certprivatekey-transact-sql.md) функции. Пример, использующий **CERTPRIVATEKEY** и **CERTENCODED** для копирования сертификата в другую базу данных, см. пример Б в разделе [CERTENCODED &#40; Transact-SQL &#41; ](../../t-sql/functions/certencoded-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Требуется разрешение CREATE CERTIFICATE в базе данных. Только имена входа Windows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сертификаты могут принадлежать имена входа и ролям приложений. Сертификаты не могут принадлежать группам и ролям.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-self-signed-certificate"></a>A. Создание самозаверяющего сертификата  
 В следующем примере будет создан сертификат под названием `Shipping04`. Закрытый ключ этого сертификата защищен паролем.  
  
```  
CREATE CERTIFICATE Shipping04   
   ENCRYPTION BY PASSWORD = 'pGFD4bb925DGvbd2439587y'  
   WITH SUBJECT = 'Sammamish Shipping Records',   
   EXPIRY_DATE = '20201031';  
GO  
```  
  
### <a name="b-creating-a-certificate-from-a-file"></a>Б. Создание сертификата из файла  
 В следующем примере будет создан сертификат в базе данных путем загрузки пары ключей из файлов.  
  
```  
CREATE CERTIFICATE Shipping11   
    FROM FILE = 'c:\Shipping\Certs\Shipping11.cer'   
    WITH PRIVATE KEY (FILE = 'c:\Shipping\Certs\Shipping11.pvk',   
    DECRYPTION BY PASSWORD = 'sldkflk34et6gs%53#v00');  
GO   
```  
  
### <a name="c-creating-a-certificate-from-a-signed-executable-file"></a>В. Создание сертификата из заверенного исполняемого файла  
  
```  
CREATE CERTIFICATE Shipping19   
    FROM EXECUTABLE FILE = 'c:\Shipping\Certs\Shipping19.dll';  
GO  
```  
  
 Возможно также создание сборки из файла библиотеки `dll`, а затем создание сертификата из сборки.  
  
```  
CREATE ASSEMBLY Shipping19   
    FROM ' c:\Shipping\Certs\Shipping19.dll'   
    WITH PERMISSION_SET = SAFE;  
GO  
CREATE CERTIFICATE Shipping19 FROM ASSEMBLY Shipping19;  
GO  
```  
  
### <a name="d-creating-a-self-signed-certificate"></a>Г. Создание самозаверяющего сертификата  
 В следующем примере создается сертификат под названием `Shipping04` без указания пароль шифрования. В этом примере можно использовать с [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].
  
```  
CREATE CERTIFICATE Shipping04   
   WITH SUBJECT = 'Sammamish Shipping Records';  
GO  
```  
  
  
## <a name="see-also"></a>См. также:  
 [ALTER CERTIFICATE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [УДАЛИТЬ СЕРТИФИКАТ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE (Transact-SQL)](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [CERTENCODED &#40; Transact-SQL &#41;](../../t-sql/functions/certencoded-transact-sql.md)   
 [CERTPRIVATEKEY &#40; Transact-SQL &#41;](../../t-sql/functions/certprivatekey-transact-sql.md)  
  
  



