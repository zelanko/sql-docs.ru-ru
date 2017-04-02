---
title: "Расширенное управление ключами (Extensible Key Management) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Управление ключами"
  - "расширенное управление ключами"
  - "Расширенное управление ключами, описанное"
ms.assetid: 9bfaf500-2d1e-4c02-b041-b8761a9e695b
caps.latest.revision: 46
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 46
---
# Расширенное управление ключами (Extensible Key Management)
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] наряду с *расширенным управлением ключами* (EKM) предусматривает возможность шифрования данных с применением поставщика *Microsoft Cryptographic API* (MSCAPI) для шифрования и создания ключа. Ключи шифрования для шифрования данных и ключей создаются в контейнерах временных ключей и перед сохранением в базе данных должны быть экспортированы из поставщика. Благодаря этому подходу управление ключами, содержащее иерархию ключей шифрования и резервирование ключей, может быть обработано [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 При растущих требованиях к соответствию нормативным документам и соблюдению конфиденциальности данных компании используют шифрование в качестве решения, обеспечивающего «глубинную защиту». Использование средств по управлению шифрованием, предусмотренных только в базах данных, часто оказывается нецелесообразным. Поставщики оборудования поставляют продукты, в которых управление ключами компании осуществляется при помощи *аппаратных модулей безопасности* (HSM). В устройствах, оборудованных аппаратными модулями безопасности, ключи шифрования встроены в оборудование или в программные модули. Это решение является более безопасным, поскольку ключи шифрования хранятся отдельно от зашифрованных данных.  
  
 Некоторые поставщики предлагают аппаратные модули безопасности как для управления ключами, так и для ускорения шифрования. В устройствах с аппаратными модулями безопасности в роли посредника между приложением и аппаратным модулем выступают интерфейсы оборудования с серверной обработкой. В своих модулях производители также реализуют поставщики MSCAPI, представленные в качестве оборудования или программного обеспечения. Часто интерфейсы MSCAPI реализуют только подмножество функций, предлагаемых аппаратными модулями. Поставщики также могут предложить программное обеспечение для управления аппаратными модулями безопасности, настройки ключей и доступа к ключам.  
  
 Реализации аппаратных модулей безопасности от разных поставщиков отличаются друг от друга. Чтобы использовать их с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , необходим общий интерфейс. Несмотря на то, что в MSCAPI такой интерфейс предусмотрен, в нем реализована только часть возможностей аппаратных модулей. У этого интерфейса есть и другие ограничения, например отсутствие собственных средств для хранения симметричных ключей, отсутствие сеансоориентированной поддержки.  
  
 Расширенное управление ключами [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] позволяет сторонним поставщикам расширенного управления ключами и поставщикам аппаратных модулей безопасности регистрировать свои модули в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. После регистрации пользователи [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] могут использовать ключи шифрования, хранимые в модулях расширенного управления ключами. Таким образом, в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] доступны расширенные возможности шифрования, поддерживаемые этими модулями, такие как массовое шифрование и расшифровка, а также функции управления ключами, например устаревание или смена ключей.  
  
 При выполнении [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на виртуальной машине Azure [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может использовать ключи, хранящиеся в [хранилище ключей Azure](http://go.microsoft.com/fwlink/?LinkId=521401). Дополнительные сведения см. в разделе [Расширенное управление ключами с помощью хранилища ключей Azure (SQL Server)](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
## Конфигурация расширенного управления ключами  
 Расширенное управление ключами поддерживается не во всех выпусках [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
 По умолчанию расширенное управление ключами отключено. Чтобы включить его, воспользуйтесь командой sp_configure с параметрами, приведенными в следующем примере:  
  
```  
sp_configure 'show advanced', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'EKM provider enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
> [!NOTE]  
>  Если команда sp_configure вызывается в выпусках [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], не поддерживающих расширенное управление ключами, то возникнет ошибка.  
  
 Чтобы отключить эту функцию, задайте значение **0**. Дополнительные сведения о настройке параметров сервера см. в разделе [sp_configure (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
## Использование расширенного управления ключами  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Расширенное управление ключами включает ключи шифрования, защищающие файлы базы данных, хранимые на внешних устройствах, таких как смарт-карты, USB-устройства, модули расширенного управления ключами и аппаратные модули безопасности. Предусмотрена также защита данных от администраторов базы данных (за исключением членов группы sysadmin). Данные могут быть зашифрованы при помощи ключей шифрования, доступ к которым имеет только пользователь базы данных на внешнем модуле расширенного управления ключами или аппаратного модуля безопасности.  
  
 Расширенное управление ключами дает следующие преимущества.  
  
-   Дополнительная проверка подлинности (включая разграничение обязанностей).  
  
-   Более высокая производительность аппаратного шифрования или расшифровки.  
  
-   Внешнее создание ключей шифрования.  
  
-   Внешнее хранение ключей шифрования (физическое разделение данных и ключей.)  
  
-   Получение ключей шифрования.  
  
-   Внешнее хранение ключей шифрования (разрешает смену ключа шифрования).  
  
-   Упрощенное восстановление ключа шифрования.  
  
-   Управление распространением ключей шифрования.  
  
-   Безопасное освобождение ключей шифрования.  
  
 Расширенное управление ключами можно использовать для сочетания имени пользователя и пароля, а также других методов, определяемых драйвером расширенного управления ключами.  
  
> [!CAUTION]  
>  Службе технической поддержки [!INCLUDE[msCoName](../../../includes/msconame-md.md)] для устранения неполадок может потребоваться ключ шифрования от поставщика расширенного управления ключами. Кроме того, при работе над устранением проблем может потребоваться доступ к средствам или процессам, предоставляемым поставщиком.  
  
### Проверка подлинности на устройстве расширенного управления ключами  
 Модуль расширенного управления ключами может поддерживать несколько типов проверки подлинности. Каждый поставщик предоставляет [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]только один тип проверки подлинности, то есть если в модуле поддерживается проверка подлинности Basic или Other, то использоваться может только одна из них, но не обе.  
  
#### Определяемая устройством расширенного управления ключами обычная проверка подлинности при помощи имени пользователя и пароля  
 Для тех модулей расширенного управления ключами, в которых поддерживается обычная проверка подлинности на основе пары *имя пользователя/пароль*, в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предусмотрена прозрачная проверка подлинности с использованием учетных данных. Дополнительные сведения об учетных данных см. в статье [Учетные данные (компонент Database Engine)](../../../relational-databases/security/authentication-access/credentials-database-engine.md).  
  
 Чтобы получить доступ к модулю расширенного управления ключами на основе имени входа, можно создать для поставщика расширенного управления ключами учетные данные и сопоставить их с именем входа (для учетных записей как Windows, так и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]). Поле *Identify* учетных данных содержит имя пользователя; в поле *secret* содержится пароль для подключения к модулю расширенного управления ключами.  
  
 При отсутствии учетных данных для поставщика расширенного управления ключами, сопоставленных с именем входа, используются учетные данные, сопоставленные с учетной записью службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Имени входа может быть сопоставлено несколько учетных данных, если они используются для отдельных поставщиков расширенного управления ключами. У каждого поставщика расширенного управления ключами может быть только один набор учетных данных, сопоставленных одному имени входа. Одни и те же учетные данные могут быть сопоставлены нескольким именам входа.  
  
#### Другие виды проверки подлинности, зависящей от устройства расширенного управления ключами  
 В модулях расширенного управления ключами, проверка подлинности в которых отличается от Windows или сочетания *пользователь/пароль*, проверка подлинности должна осуществляться независимо от [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
### Шифрование и расшифровка при помощи устройства расширенного управления ключами  
 Следующие функции и возможности позволяют зашифровать и расшифровать данные при помощи симметричных и асимметричных ключей.  
  
|Функция или характеристика|Справочник|  
|-------------------------|---------------|  
|Шифрование симметричным ключом|[CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-symmetric-key-transact-sql.md)|  
|Шифрование асимметричным ключом|[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-asymmetric-key-transact-sql.md)|  
|EncryptByKey(key_guid, 'cleartext', …)|[ENCRYPTBYKEY (Transact-SQL)](../../../t-sql/functions/encryptbykey-transact-sql.md)|  
|DecryptByKey(ciphertext, …)|[DECRYPTBYKEY (Transact-SQL)](../../../t-sql/functions/decryptbykey-transact-sql.md)|  
|EncryptByAsmKey(key_guid, 'cleartext')|[ENCRYPTBYASYMKEY (Transact-SQL)](../../../t-sql/functions/encryptbyasymkey-transact-sql.md)|  
|DecryptByAsmKey(ciphertext)|[DECRYPTBYASYMKEY (Transact-SQL)](../../../t-sql/functions/decryptbyasymkey-transact-sql.md)|  
  
#### Шифрование ключей базы данных при помощи ключей расширенного управления ключами  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при помощи ключей расширенного управления ключами можно шифровать другие ключи базы данных. В устройстве расширенного управления ключами можно создать и использовать как симметричные, так и асимметричные ключи. Асимметричные ключи расширенного управления ключами позволяют зашифровать собственные (отличные от расширенного управления ключами) симметричные ключи.  
  
 В следующем примере показано создание симметричного ключа базы данных и его шифрование при помощи ключа из модуля расширенного управления ключами.  
  
```  
CREATE SYMMETRIC KEY Key1  
WITH ALGORITHM = AES_256  
ENCRYPTION BY EKM_AKey1;  
GO  
--Open database key  
OPEN SYMMETRIC KEY Key1  
DECRYPTION BY EKM_AKey1  
```  
  
 Дополнительные сведения о базе данных и ключах серверов в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] см. в статье [Ключи шифрования базы данных и SQL Server (компонент Database Engine)](../../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md).  
  
> [!NOTE]  
>  Зашифровать один ключ расширенного управления ключами при помощи другого ключа расширенного управления ключами невозможно.  
>   
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не поддерживает модули подписания и асимметричные ключи, сформированные из поставщика расширенного управления ключами.  
  
## Связанные задачи  
 [Включенный параметр конфигурации сервера поставщика расширенного управления ключами](../../../database-engine/configure-windows/ekm-provider-enabled-server-configuration-option.md)  
  
 [Enable TDE on SQL Server Using EKM (Включение прозрачного шифрования данных в SQL Server с помощью расширенного управления ключами)](../../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)  
  
 [Расширенное управление ключами с помощью хранилища ключей Azure (SQL Server)](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
## См. также:  
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [DROP CRYPTOGRAPHIC PROVIDER (Transact-SQL)](../../../t-sql/statements/drop-cryptographic-provider-transact-sql.md)   
 [ALTER CRYPTOGRAPHIC PROVIDER (Transact-SQL)](../../../t-sql/statements/alter-cryptographic-provider-transact-sql.md)   
 [sys.cryptographic_providers (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-cryptographic-providers-transact-sql.md)   
 [sys.dm_cryptographic_provider_sessions (Transact-SQL)](../../../relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-sessions-transact-sql.md)   
 [sys.dm_cryptographic_provider_properties (Transact-SQL)](../../../relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-properties-transact-sql.md)   
 [sys.dm_cryptographic_provider_algorithms (Transact-SQL)](../../../relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-algorithms-transact-sql.md)   
 [sys.dm_cryptographic_provider_keys (Transact-SQL)](../../../relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-keys-transact-sql.md)   
 [sys.credentials (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-credential-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-login-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER ASYMMETRIC KEY (Transact-SQL)](../../../t-sql/statements/alter-asymmetric-key-transact-sql.md)   
 [DROP ASYMMETRIC KEY (Transact-SQL)](../../../t-sql/statements/drop-asymmetric-key-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY (Transact-SQL)](../../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY (Transact-SQL)](../../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [OPEN SYMMETRIC KEY (Transact-SQL)](../../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [Резервное копирование и восстановление ключей шифрования служб Reporting Services](../../../reporting-services/install-windows/back-up-and-restore-reporting-services-encryption-keys.md)   
 [Удаление и повторное создание ключей шифрования (диспетчер конфигурации служб SSRS)](../../../reporting-services/install-windows/delete-and-re-create-encryption-keys-ssrs-configuration-manager.md)   
 [Добавление и удаление ключей шифрования для масштабного развертывания (диспетчер конфигурации служб SSRS)](../../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md)   
 [Создание резервной копии главного ключа службы](../../../relational-databases/security/encryption/back-up-the-service-master-key.md)   
 [Восстановление главного ключа службы](../../../relational-databases/security/encryption/restore-the-service-master-key.md)   
 [Создание главного ключа базы данных](../../../relational-databases/security/encryption/create-a-database-master-key.md)   
 [Создание резервной копии главного ключа базы данных](../../../relational-databases/security/encryption/back-up-a-database-master-key.md)   
 [Восстановление главного ключа базы данных](../../../relational-databases/security/encryption/restore-a-database-master-key.md)   
 [Создание идентичных симметричных ключей на двух серверах](../../../relational-databases/security/encryption/create-identical-symmetric-keys-on-two-servers.md)  
  
  