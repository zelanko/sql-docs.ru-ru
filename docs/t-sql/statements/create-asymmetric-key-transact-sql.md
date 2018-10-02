---
title: CREATE ASYMMETRIC KEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ASYMMETRIC_KEY_TSQL
- CREATE ASYMMETRIC KEY
- CREATE_ASYMMETRIC_KEY_TSQL
- ASYMMETRIC KEY
dev_langs:
- TSQL
helpviewer_keywords:
- asymmetric keys [SQL Server], creating
- encryption [SQL Server], asymmetric keys
- CREATE ASYMMETRIC KEY statement
- asymmetric keys [SQL Server]
- cryptography [SQL Server], asymmetric keys
ms.assetid: 141bc976-7631-49f6-82bd-a235028645b1
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d318349e792cb7579efcc2062ca8eb1b5521db48
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600723"
---
# <a name="create-asymmetric-key-transact-sql"></a>CREATE ASYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает асимметричный ключ в базе данных.  
  
 Эта функция несовместима с экспортом базы данных с использованием платформы приложения уровня данных (DACFx). Необходимо удалить все асимметричные ключи перед экспортом.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CREATE ASYMMETRIC KEY Asym_Key_Name   
   [ AUTHORIZATION database_principal_name ]  
   [ FROM <Asym_Key_Source> ]  
   [ WITH <key_option> ] 
   [ ENCRYPTION BY <encrypting_mechanism> ] 
   [ ; ]
  
<Asym_Key_Source>::=  
     FILE = 'path_to_strong-name_file'  
   | EXECUTABLE FILE = 'path_to_executable_file'  
   | ASSEMBLY Assembly_Name  
   | PROVIDER Provider_Name  
  
<key_option> ::=  
   ALGORITHM = <algorithm>  
      |  
   PROVIDER_KEY_NAME = 'key_name_in_provider'  
      |  
      CREATION_DISPOSITION = { CREATE_NEW | OPEN_EXISTING }  
  
<algorithm> ::=  
      { RSA_4096 | RSA_3072 | RSA_2048 | RSA_1024 | RSA_512 }   
  
<encrypting_mechanism> ::=  
    PASSWORD = 'password'   
```  
  
## <a name="arguments"></a>Аргументы  
 FROM *Asym_Key_Source*  
 Задает источник, из которого нужно загрузить пару асимметричных ключей.  
  
 AUTHORIZATION *database_principal_name*  
 Задает владельца асимметричного ключа. Владелец не может быть ролью или группой. Если этот параметр опущен, владельцем будет текущий пользователь.  
  
 FILE ='*path_to_strong-name_file*'  
 Указывает путь надежного имени файла, из которого будет загружена пара ключей.  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
 EXECUTABLE FILE ='*path_to_executable_file*'  
 Указывает файл сборки, из которого будет загружен открытый ключ. Ограничен 260 символами MAX_PATH из API интерфейса Windows.  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
 ASSEMBLY *Assembly_Name*  
 Указывает имя сборки, из которой будет загружен открытый ключ.  
  
ENCRYPTION BY *\<key_name_in_provider>* Указывает способ шифрования ключа. Это может быть сертификат, пароль или асимметричный ключ.  
  
 KEY_NAME ='*key_name_in_provider*'  
 Указывает имя ключа из внешнего поставщика. Дополнительные сведения о расширенном управлении ключами см. в разделе [Расширенное управление ключами (EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
 CREATION_DISPOSITION = CREATE_NEW  
 Создает новый ключ на устройстве расширенного управления ключами. Свойство PROV_KEY_NAME должно использоваться для указания имени ключа на устройстве. Если ключ уже существует в устройстве, оператор завершается с ошибкой.  
  
 CREATION_DISPOSITION = OPEN_EXISTING  
 Сопоставляет асимметричный ключ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с существующим ключом системы расширенного управления ключами. Свойство PROV_KEY_NAME должно использоваться для указания имени ключа на устройстве. Если выражение CREATION_DISPOSITION = OPEN_EXISTING не предусмотрено, значением по умолчанию является CREATE_NEW.  
  
 ALGORITHM = \<algorithm>  
 Доступны пять алгоритмов: RSA_4096, RSA_3072, RSA_2048, RSA_1024 и RSA_512.  
  
 RSA_1024 и RSA_512 являются устаревшими. Чтобы использовать алгоритмы RSA_1024 или RSA_512 (что не рекомендуется), необходимо установить уровень совместимости базы данных 120 или ниже.  
  
 PASSWORD = '*password*'  
 Указывает пароль для шифрования закрытого ключа. Если это предложение отсутствует, закрытый ключ будет зашифрован с использованием главного ключа базы данных. *password* имеет максимальную длину 128 символов. *password* должен соответствовать требованиям политики паролей Windows применительно к компьютеру, на котором запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="remarks"></a>Remarks  
 *Асимметричный ключ* является защищаемой сущностью на уровне базы данных. В его форме по умолчанию эта сущность содержит как открытый, так и закрытый ключ. CREATE ASYMMETRIC KEY при выполнении без предложения FROM формирует новую пару ключей. CREATE ASYMMETRIC KEY при выполнении с предложением FROM импортирует пару ключей из файла или открытый ключ из сборки.  
  
 По умолчанию закрытый ключ защищается с помощью главного ключа базы данных. Для защиты закрытого ключа необходим пароль, если не был создан главный ключ базы данных. Если главный ключ базы данных существует, пароль необязателен.  
  
 Закрытый ключ может быть длинной 512, 1024 или 2048 бит.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CREATE ASYMMETRIC KEY на базу данных. Если указывается предложение AUTHORIZATION, необходимо разрешение IMPERSONATE на участника базы данных или разрешение ALTER на роль приложения. Асимметричными ключами могут владеть только имена входа Windows, имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и роли приложений. Группы и роли не могут владеть асимметричными ключами.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-an-asymmetric-key"></a>A. Создание асимметричного ключа  
 Следующий пример создает асимметричный ключ под именем `PacificSales09`, используя алгоритм `RSA_2048`, и защищает закрытый ключ паролем.  
  
```  
CREATE ASYMMETRIC KEY PacificSales09   
    WITH ALGORITHM = RSA_2048   
    ENCRYPTION BY PASSWORD = '<enterStrongPasswordHere>';   
GO  
```  
  
### <a name="b-creating-an-asymmetric-key-from-a-file-giving-authorization-to-a-user"></a>Б. Создание асимметричного ключа из файла с предоставлением авторизации пользователю  
 Следующий пример создает асимметричный ключ `PacificSales19` из пары ключей, сохраненных в файле, и затем авторизует пользователя `Christina` для использования асимметричного ключа.  
  
```  
CREATE ASYMMETRIC KEY PacificSales19 AUTHORIZATION Christina   
    FROM FILE = 'c:\PacSales\Managers\ChristinaCerts.tmp'    
    ENCRYPTION BY PASSWORD = '<enterStrongPasswordHere>';  
GO  
```  
  
### <a name="c-creating-an-asymmetric-key-from-an-ekm-provider"></a>В. Создание асимметричного ключа из поставщика расширенного управления ключами  
 В следующем примере создается асимметричный ключ `EKM_askey1` из пары ключей, сохраненной в файле. Затем выполняется шифрование этого ключа с использованием поставщика расширенного управления ключами с именем `EKMProvider1` и ключа на этом поставщике с именем `key10_user1`.  
  
```  
CREATE ASYMMETRIC KEY EKM_askey1   
    FROM PROVIDER EKM_Provider1  
    WITH   
        ALGORITHM = RSA_2048,   
        CREATION_DISPOSITION = CREATE_NEW  
        , PROVIDER_KEY_NAME  = 'key10_user1' ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Выбор алгоритма шифрования](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [ALTER ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)   
 [DROP ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Расширенное управление ключами с помощью хранилища ключей Azure (SQL Server)](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
  
