---
title: "СОЗДАЙТЕ СИММЕТРИЧНЫЙ ключ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE SYMMETRIC KEY
- SYMMETRIC KEP
- CREATE_SYMMETRIC_KEY_TSQL
- SYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE SYMMETRIC KEY statement
- temporary symmetric keys [SQL Server]
- symmetric keys [SQL Server], creating
- symmetric keys [SQL Server]
ms.assetid: b5d23572-b79d-4cf1-9eef-d648fa3b1358
caps.latest.revision: 72
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 71ca2fac0a6b9f087f9d434c5a701f5656889b9e
ms.openlocfilehash: d3b1490b1ac07d0e6a3f0fc3ed1515dd0872d545
ms.contentlocale: ru-ru
ms.lasthandoff: 09/13/2017

---
# <a name="create-symmetric-key-transact-sql"></a>CREATE SYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает симметричный ключ и указывает его свойства в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Эта функция несовместима с экспортом базы данных с использованием платформы приложения уровня данных (DACFx). Необходимо удалить все симметричные ключи перед экспортом.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CREATE SYMMETRIC KEY key_name   
    [ AUTHORIZATION owner_name ]  
    [ FROM PROVIDER provider_name ]  
    WITH 
      [
          <key_options> [ , ... n ]  
        | ENCRYPTION BY <encrypting_mechanism> [ , ... n ] 
      ]
  
<key_options> ::=  
      KEY_SOURCE = 'pass_phrase'  
    | ALGORITHM = <algorithm>  
    | IDENTITY_VALUE = 'identity_phrase'  
    | PROVIDER_KEY_NAME = 'key_name_in_provider'   
    | CREATION_DISPOSITION = {CREATE_NEW | OPEN_EXISTING }  
  
<algorithm> ::=  
    DES | TRIPLE_DES | TRIPLE_DES_3KEY | RC2 | RC4 | RC4_128  
    | DESX | AES_128 | AES_192 | AES_256   
  
<encrypting_mechanism> ::=  
      CERTIFICATE certificate_name   
    | PASSWORD = 'password'   
    | SYMMETRIC KEY symmetric_key_name   
    | ASYMMETRIC KEY asym_key_name  
```  
  
## <a name="arguments"></a>Аргументы  
 *Key_name*  
 Уникальное имя, под которым симметричный ключ известен в базе данных. Имена временных ключей должны начинаться с одиночного символа номера (#). Например **#temporaryKey900007**. Нельзя создать симметричный ключ, в начале имени которого указано более одного символа #. Временный симметричный ключ невозможно создать с помощью поставщика расширенного управления ключами.  
  
 АВТОРИЗАЦИЯ *owner_name*  
 Указывает имя пользователя базы данных или роли приложения, которым будет принадлежать этот ключ.  
  
 ОТ ПОСТАВЩИКА *provider_name*  
 Указывает поставщик расширенного управления ключами и его имя. Этот ключ не экспортируется с устройства расширенного управления ключами. Поставщик должен быть сначала определен с использованием инструкции CREATE PROVIDER. Дополнительные сведения о создании внешних поставщиков ключей см. в разделе [расширенного управления ключами &#40; Расширенное управление Ключами &#41; ](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
 KEY_SOURCE **= "***pass_phrase***"**  
 Указывает парольную фразу, из которой извлекается ключ.  
  
 IDENTITY_VALUE **= "***identity_phrase***"**  
 Указывает идентифицирующую фразу, из которой будет формироваться идентификатор GUID для маркировки данных, зашифрованных с помощью временного ключа.  
  
 PROVIDER_KEY_NAME**= "***key_name_in_provider***"**  
 Указывает имя, на которое ссылается поставщик расширенного управления ключами.  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
 ВЫРАЖЕНИЕ CREATION_DISPOSITION ** = ** CREATE_NEW  
 Создает новый ключ на устройстве расширенного управления ключами.  Если ключ уже существует в устройстве, оператор завершается с ошибкой.  
  
 ВЫРАЖЕНИЕ CREATION_DISPOSITION ** = ** OPEN_EXISTING  
 Сопоставляет симметричный ключ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с существующим ключом системы расширенного управления ключами. Если выражение CREATION_DISPOSITION = OPEN_EXISTING не предусмотрено, значением по умолчанию является CREATE_NEW.  
  
 *имя_сертификата*  
 Указывает имя сертификата, который будет использоваться для шифрования симметричного ключа. Сертификат уже должен существовать в базе данных.  
  
 **"** *пароль* **"**  
 Указывает пароль, из которого извлекается ключ TRIPLE_DES для защиты симметричного ключа. *пароль* должен соответствовать требованиям политики паролей Windows компьютера, на котором выполняется экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Всегда используйте надежные пароли.  
  
 *symmetric_key_name*  
 Указывает симметричный ключ, используемый для шифрования создаваемого ключа. Указанный ключ должен уже существовать в базе данных, и этот ключ должен быть открытым.  
  
 *asym_key_name*  
 Указывает асимметричный ключ, используемый для шифрования создаваемого ключа. Асимметричный ключ должен уже существовать в базе данных.  
  
 \<алгоритм >  
Укажите алгоритм шифрования.   
> [!WARNING]  
> Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]все алгоритмы, отличные от AES_128, AES_192 и AES_256, являются нерекомендуемыми. Чтобы использовать старые алгоритмы (не рекомендуется), необходимо установить уровень совместимости базы данных для базы данных 120 или ниже.  
  
## <a name="remarks"></a>Замечания  
 После создания симметричный ключ должен быть зашифрован с помощью хотя бы одного из следующих средств: сертификат, пароль, симметричный ключ, асимметричный ключ или PROVIDER. Ключ может быть зашифрован более чем один раз для каждого типа шифрования. Другими словами, один симметричный ключ может быть зашифрован с использованием нескольких сертификатов, симметричных ключей и асимметричных ключей одновременно.  
  
> [!CAUTION]  
>  Если симметричный ключ шифруется с использованием пароля вместо открытого ключа главного ключа базы данных, то используется алгоритм шифрования TRIPLE DES. Поэтому ключи, созданные с помощью сильных алгоритмов шифрования, таких как AES, защищены с помощью более слабого алгоритма.  
  
 Необязательный пароль можно использовать для шифрования симметричного ключа перед распространением ключа нескольким пользователям.  
  
 Владельцем временных ключей является пользователь, который создает их. Временные ключи действительны только в текущем сеансе.  
  
 Аргумент IDENTITY_VALUE формирует идентификатор GUID, с помощью которого маркируются данные, зашифрованные новым симметричным ключом. Маркирование может быть использовано для сопоставления ключей шифрованным данным. Идентификатор GUID, формируемый определенную фразу не изменяется. Фраза, использованная для создания идентификатора GUID, не может быть повторно использована до тех пор, пока активен хотя бы один сеанс, использующий эту фразу. Предложение IDENTITY_VALUE является необязательным, но рекомендуется использовать его для хранения данных, зашифрованных с применением временного ключа.  
  
 Не существует алгоритма шифрования по умолчанию.  
  
> [!IMPORTANT]  
>  Защищать конфиденциальные данные с помощью потоковых шифров RC4 и RC4_128 не рекомендуется. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает дальнейшее шифрование данных с помощью таких ключей.  
  
 Сведения о симметричных ключах можно увидеть в [sys.symmetric_keys](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md) представления каталога.  
  
 Симметричные ключи не могут быть зашифрованы с помощью симметричных ключей, созданных поставщиком шифрования.  
  
 **Пояснение к алгоритмам DES:**  
  
-   DESX был именован неправильно. Симметричные ключи, созданные с параметром ALGORITHM = DESX, в действительности используют шифр TRIPLE DES с 192-битным ключом. Алгоритм DESX не предоставляется. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
-   Симметричные ключи, созданные с параметром ALGORITHM = TRIPLE_DES_3KEY, используют шифр TRIPLE DES с 192-битным ключом.  
-   Симметричные ключи, созданные с параметром ALGORITHM = TRIPLE_DES, используют шифр TRIPLE DES с 128-битным ключом.  
  
 **Устаревание алгоритма RC4:**  
  
 Приводит многократного использования того же RC4 или RC4_128 KEY_GUID для различных блоков данных, одинаковых ключей RC4, так как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не предоставляет рассеивание автоматически. Повторное использование одного и того же ключа RC4 является типичной ошибкой, становящейся причиной очень слабого шифрования. Таким образом, ключевые слова RC4 и RC4_128 являются устаревшими. [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
> [!WARNING]  
>  Алгоритм RC4 поддерживается только в целях обратной совместимости. Когда база данных имеет уровень совместимости 90 или 100, новые материалы могут шифроваться только с помощью алгоритмов RC4 или RC4_128. (Не рекомендуется.) Используйте вместо этого более новые алгоритмы, например AES. В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] материалы, зашифрованные с помощью алгоритмов RC4 или RC4_128, могут быть расшифрованы на любом уровне совместимости.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение ALTER ANY SYMMETRIC KEY на базу данных. Если указан аргумент AUTHORIZATION, то требуется разрешение IMPERSONATE для пользователя базы данных или разрешение ALTER для роли приложения. Если для шифрования использовался сертификат или асимметричный ключ, то требуется разрешение VIEW DEFINITION для сертификата или асимметричного ключа. Симметричные ключи могут принадлежать только именам входа Windows, именам входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и ролям приложений. Симметричные ключи не могут принадлежать группам и ролям.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-symmetric-key"></a>A. Создание симметричного ключа  
 В следующем примере создается симметричный ключ с именем `JanainaKey09` с помощью алгоритма `AES 256`, а затем новый ключ шифруется с применением сертификата `Shipping04`.  
  
```  
CREATE SYMMETRIC KEY JanainaKey09   
WITH ALGORITHM = AES_256  
ENCRYPTION BY CERTIFICATE Shipping04;  
GO  
```  
  
### <a name="b-creating-a-temporary-symmetric-key"></a>Б. Создание временного симметричного ключа  
 В следующем примере создается временный симметричный ключ с именем `#MarketingXXV` из парольной фразы: `The square of the hypotenuse is equal to the sum of the squares of the sides`. Ключу назначается идентификатор GUID, формируемый из строки `Pythagoras` и зашифрованный сертификатом `Marketing25`.  
  
```  
  
CREATE SYMMETRIC KEY #MarketingXXV   
WITH ALGORITHM = AES_128,  
KEY_SOURCE   
     = 'The square of the hypotenuse is equal to the sum of the squares of the sides',  
IDENTITY_VALUE = 'Pythagoras'  
ENCRYPTION BY CERTIFICATE Marketing25;  
GO  
```  
  
### <a name="c-creating-a-symmetric-key-using-an-extensible-key-management-ekm-device"></a>В. Создание симметричного ключа с помощью устройства расширенного управления ключами (EKM)  
 В следующем примере демонстрируется создание симметричного ключа с именем `MySymKey` при помощи поставщика с именем `MyEKMProvider` и имени ключа `KeyForSensitiveData`. Назначается авторизация для пользователя `User1`; при этом подразумевается, что системным администратором уже зарегистрирован поставщик с именем `MyEKMProvider` в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
CREATE SYMMETRIC KEY MySymKey  
AUTHORIZATION User1  
FROM PROVIDER EKMProvider  
WITH  
PROVIDER_KEY_NAME='KeyForSensitiveData',  
CREATION_DISPOSITION=OPEN_EXISTING;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Выбор алгоритма шифрования](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [ALTER SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [sys.symmetric_keys &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [Расширенное управление ключами &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [Расширенное управление ключами с помощью хранилища ключей Azure &#40;SQL Server&#41;](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
  

