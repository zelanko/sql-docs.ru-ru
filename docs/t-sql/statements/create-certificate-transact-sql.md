---
title: CREATE CERTIFICATE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: abd46332127b1b15280df0ec5bab5655da5a148a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="create-certificate-transact-sql"></a>Инструкция CREATE CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Добавляет сертификат в базу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]

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
 *certificate_name*  
 Имя сертификата в базе данных.  
  
 AUTHORIZATION *user_name*  
 Имя пользователя, которому принадлежит сертификат.  
  
 ASSEMBLY *assembly_name*  
 Указывает подписанную сборку, уже загруженную в базу данных.  
  
 [ EXECUTABLE ] FILE ='*path_to_file*'  
 Указывает полный путь, включающий имя файла, к файлу, зашифрованному по правилам DER и содержащему сертификат. Если используется параметр EXECUTABLE, то файл является библиотекой DLL, заверенной с использованием данного сертификата. *path_to_file* может быть локальным путем или UNC-путем к расположению в сети. Доступ к файлу осуществляется в контексте безопасности учетной записи службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта учетная запись должна иметь соответствующие разрешения на доступ в файловой системе.  
  
 WITH PRIVATE KEY  
 Указывает, что закрытый ключ сертификата загружен в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это предложение действительно лишь в случае, когда сертификат создается из файла. Для загрузки закрытого ключа сборки следует использовать команду [ALTER CERTIFICATE](../../t-sql/statements/alter-certificate-transact-sql.md).  
  
 FILE ='*path_to_private_key*'  
 Указывает полный путь к закрытому ключу, включая имя файла. *path_to_private_key* может быть локальным путем или UNC-путем к расположению в сети. Доступ к файлу осуществляется в контексте безопасности учетной записи службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта учетная запись должна иметь соответствующие разрешения на доступ в файловой системе.  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
 asn_encoded_certificate  
 Биты закодированного сертификата ASN, указанного в качестве двоичной константы.  
  
 BINARY =*private_key_bits*  
 **Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Биты закрытого ключа, указанного в качестве двоичной константы. Биты могут находиться в зашифрованном виде. Если они зашифрованы, пользователь должен предоставить пароль для расшифровки. Проверка политики паролей для данного пароля не выполняется. Биты закрытого ключа должны быть в формате файла PVK.  
  
 DECRYPTION BY PASSWORD ='*key_password*'  
 Указывает пароль, необходимый для расшифровки закрытого ключа, получаемого из файла. Это предложение необязательно, если закрытый ключ защищен пустым паролем. Не рекомендуется сохранять закрытый ключ в файл без защиты паролем. Если требуется ввод пароля, но верный пароль не указан, выполнение инструкции завершится ошибкой.  
  
 ENCRYPTION BY PASSWORD ='*password*'  
 Указывает пароль для шифрования закрытого ключа. Этот аргумент нужно использовать лишь в том случае, если необходимо зашифровать сертификат с помощью пароля. Если аргумент опущен, закрытый ключ шифруется с использованием главного ключа базы данных. *password* должен соответствовать требованиям политики паролей Windows применительно к компьютеру, на котором запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Политика паролей](../../relational-databases/security/password-policy.md).  
  
 SUBJECT ='*certificate_subject_name*'  
 Термин *subject* (субъект) относится к полю в метаданных сертификата, определяемому стандартом X.509. Длина субъекта не должна превышать 64 символов, и это ограничение действует для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в Linux. Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в Windows он может иметь длину до 128 символов. Субъекты, имеющие длину больше 128 символов, усекаются, если они сохраняются в каталоге, однако в большом двоичном объекте (BLOB), содержащем сертификат, сохранится полное имя субъекта.  
  
 START_DATE ='*datetime*'  
 Дата, начиная с которой сертификат действителен. Если она не указана, в качестве значения START_DATE устанавливается текущая дата. Значение START_DATE имеет формат времени UTC. Это значение можно указать в любом формате, который можно преобразовать в формат даты и времени.  
  
 EXPIRY_DATE ='*datetime*'  
 Дата истечения срока действия сертификата. Если она не указана, для EXPIRY_DATE устанавливается дата через год от START_DATE. Значение EXPIRY_DATE имеет формат времени UTC. Это значение можно указать в любом формате, который можно преобразовать в формат даты и времени. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Компонент Service Broker проверяет дату окончания срока действия. Однако при использовании сертификата для шифрования срок действия не вступает в силу.  
  
 ACTIVE FOR BEGIN_DIALOG = { **ON** | OFF }  
 Делает сертификат доступным для инициатора диалога с компонентом [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Значение по умолчанию — ON.  
  
## <a name="remarks"></a>Remarks  
 Сертификат — это защищаемый объект уровня базы данных, соответствующий стандарту X.509 и поддерживающий поля X.509 V1. Инструкция CREATE CERTIFICATE может загрузить сертификат из файла или сборки. Она также может создать пару ключей и самостоятельно подписанный сертификат.  
  
 Закрытый ключ должен быть \<= 2500 байт в зашифрованном формате. Закрытые ключи, созданные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], имеют длину 1024 бит до [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], и 2048 бит, начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Закрытые ключи, импортированные из внешнего источника, имеют минимальную длину в 384 бит и максимальную длину в 4 096 бит. Длина импортируемого закрытого ключа должна быть кратной 64 бит. Для сертификатов, используемых для прозрачного шифрования данных, размер закрытого ключа ограничен 3456 битами.  
  
 Сохраняется весь серийный номер сертификата, но в представлении каталога sys.certificates отображаются только первые 16 байт.  
  
 Сохраняется все поле издателя, но в представлении каталога sys.certificates отображаются только первые 884 байта.  
  
 Закрытый ключ должен соответствовать открытому ключу, заданному аргументом *certificate_name*.  
  
 При создании сертификата из контейнера загрузка закрытого ключа необязательна. Однако в случае, когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает самостоятельно подписанный сертификат, закрытый ключ создается всегда. По умолчанию закрытый ключ шифруется главным ключом базы данных. Если главного ключа базы данных не существует, а пароль не указан, при выполнении инструкции произойдет ошибка.  
  
 Параметр ENCRYPTION BY PASSWORD не обязателен, если шифрование закрытого ключа выполняется главным ключом базы данных. Использовать этот параметр следует лишь тогда, когда закрытый ключ будет зашифрован паролем. Если пароль не указан, закрытый ключ будет зашифрован с использованием главного ключа базы данных. Отсутствие этого предложения вызовет ошибку, если не удастся открыть главный ключ базы данных.  
  
 Если закрытый ключ зашифрован главным ключом базы данных, указывать пароль расшифровки не требуется.  
  
> [!NOTE]  
>  Встроенные функции шифрования и цифровой подписи не проверяют даты истечения срока действия сертификатов. Пользователи этих функций должны самостоятельно определять, когда следует проверять сроки действия сертификатов.  
  
 Двоичное описание сертификата можно создать с помощью функций [CERTENCODED (Transact-SQL)](../../t-sql/functions/certencoded-transact-sql.md) и [CERTPRIVATEKEY (Transact-SQL)](../../t-sql/functions/certprivatekey-transact-sql.md). Пример использования функций **CERTPRIVATEKEY** и **CERTENCODED** для копирования сертификата в другую базу данных см. в примере Б из раздела [CERTENCODED (Transact-SQL)](../../t-sql/functions/certencoded-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение CREATE CERTIFICATE в базе данных. Сертификаты могут принадлежать только именам входа Windows, именам входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и ролям приложений. Сертификаты не могут принадлежать группам и ролям.  
  
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
 В следующем примере создается сертификат `Shipping04` без указания пароля шифрования. Этот пример можно использовать с [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].
  
```  
CREATE CERTIFICATE Shipping04   
   WITH SUBJECT = 'Sammamish Shipping Records';  
GO  
```  
  
  
## <a name="see-also"></a>См. также:  
 [ALTER CERTIFICATE (Transact-SQL)](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE (Transact-SQL)](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE (Transact-SQL)](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [CERTENCODED (Transact-SQL)](../../t-sql/functions/certencoded-transact-sql.md)   
 [CERTPRIVATEKEY (Transact-SQL)](../../t-sql/functions/certprivatekey-transact-sql.md)  
  
  


