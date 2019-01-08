---
title: Центр обеспечения безопасности для базы данных Azure SQL и ядра СУБД SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 09/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- Security [SQL Server]
helpviewer_keywords:
- SQL Server, security
- security [SQL Server]
- database security [SQL Server]
- databases [SQL Server], security
ms.assetid: dfb39d16-722a-4734-94bb-98e61e014ee7
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 1fffca14e9c30c5fd01cff88b7bb90608eb9d30d
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53364416"
---
# <a name="security-center-for-sql-server-database-engine-and-azure-sql-database"></a>Центр обеспечения безопасности для базы данных Azure SQL и SQL Server Database Engine
  На этой странице представлены ссылки, помогающие найти сведения, касающиеся безопасности и защиты в компонентах [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].  
  
> [!NOTE]  
>  Возможности [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] постоянно совершенствуются. См. самую последнюю версию этой статьи для получения последних сведений о [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
|Проверка подлинности: Кто вы?|Авторизация: Что можно сделать?|Шифрование. Хранение секретных данных|Безопасность подключения: Ограничения и обеспечение безопасности|Аудит. Доступ на запись|  
|----------------------------------|-------------------------------------|-------------------------------------|---------------------------------------------------|--------------------------------|  
|**Кто выполняет проверку подлинности?**<br /><br /> [![Проверка подлинности Windows в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-windows-authenticaion.png "проверка подлинности Windows в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> <br /><br /> [![Проверка подлинности SQL Server центра безопасности карты](../../database-engine/media/security-center-map-sql-authenticaion.png "центр безопасности карты проверки подлинности SQL Server")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> **Где выполняется проверка подлинности?**<br /><br /> [![Центр безопасности сопоставление имен для входа и пользователей](../../database-engine/media/security-center-map-logins-users.png "центр безопасности сопоставление имен для входа и пользователей")](https://msdn.microsoft.com/library/aa337562.aspx)<br /><br /> <br /><br /> [![Схеме центра обеспечения безопасности пользователей автономной базы данных](../../database-engine/media/security-center-map-contained-users.png "схеме центра обеспечения безопасности пользователей автономной базы данных")](https://msdn.microsoft.com/library/ff929188.aspx)<br /><br /> **Использование других идентификаторов**<br /><br /> [![Учетные данные в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-credentials.png "учетные данные в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms161950.aspx)<br /><br /> [![Execute As Login в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-exec-as-login.png "Execute As Login в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> [![Execute As пользователя в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-exec-as-user.png "схеме центра обеспечения безопасности выполнять от имени пользователя")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")|**Предоставление, отмена и запрет разрешений**<br /><br /> [![Защищаемые классы схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-securable-classes.png "защищаемые классы схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms190401.aspx)<br /><br /> [![Разрешения сервера в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-srv-perms.png "разрешения сервера в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> [![Разрешения базы данных в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-db-perms.png "разрешения базы данных в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> **Роли безопасности**<br /><br /> [![Роли сервера в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-srv-roles.png "роли сервера в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms188659.aspx)<br /><br /> [![Роли базы данных в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-db-roles.png "роли базы данных в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms189121.aspx)<br /><br /> `Restricting Data Access to Selected Data Elements`<br /><br /> [![Центр безопасности карты представлений и процедур](../../database-engine/media/security-center-map-view-procs.png "центр безопасности карты представлений и процедур")](https://msdn.microsoft.com/library/ms175503.aspx)<br /><br /> [![Безопасность на уровне строк в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-row-level-sec.png "безопасность на уровне строк в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/dn765131.aspx)<br /><br /> [![Центр безопасности карты динамическое маскирование данных](../../database-engine/media/security-center-map-data-masking.png "центр безопасности карты динамическое маскирование данных")](http://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [![Подписанные объекты в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-signed-objects.png "подписанные объекты в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms181700.aspx)<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")|**Шифрование файлов**<br /><br /> [![BitLocker в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-bitlocker.png "BitLocker в схеме центра обеспечения безопасности")](https://support.microsoft.com/en-us/kb/2855131)<br /><br /> [![Шифрование NTFS в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-ntfs-encryp.png "шифрование NTFS в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [![Схеме центра обеспечения безопасности TDE](../../database-engine/media/security-center-map-tde.png "схеме центра обеспечения безопасности прозрачного шифрования данных")](https://msdn.microsoft.com/library/bb934049.aspx)<br /><br /> [![Шифрование резервной копии карты центр безопасности](../../database-engine/media/security-center-map-backup-encryp.png "шифрование резервной копии карты центра безопасности")](https://msdn.microsoft.com/library/dn449489.aspx)<br /><br /> **Шифрование источников**<br /><br /> [![Схеме центра обеспечения безопасности расширенного управления Ключами](../../database-engine/media/security-center-map-ekm.png "схеме центра обеспечения безопасности расширенного управления Ключами")](https://msdn.microsoft.com/library/bb895340.aspx)<br /><br /> [![В схеме центра безопасности Azure Key Vault](../../database-engine/media/security-center-map-key-vault.png "схеме центра обеспечения безопасности хранилища ключей Azure")](http://azure.microsoft.com/documentation/articles/key-vault-get-started/)<br /><br /> **Шифрование столбцов, данных и ключей**<br /><br /> [![Схеме центра обеспечения безопасности шифрование по сертификату](../../database-engine/media/security-center-map-cert.png "схеме центра обеспечения безопасности шифрование по сертификату")](https://msdn.microsoft.com/library/ms188061.aspx)<br /><br /> [![Шифрование симметричным ключом схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-sym-key.png "схеме центра обеспечения безопасности шифрование симметричным ключом")](https://msdn.microsoft.com/library/ms174361.aspx)<br /><br /> [![Шифрование асимметричным ключом схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-asym-key.png "схеме центра обеспечения безопасности шифрование асимметричным ключом")](https://msdn.microsoft.com/library/ms186950.aspx)<br /><br /> [![Схеме центра обеспечения безопасности шифрование с парольной фразой](../../database-engine/media/security-center-map-passphrase.png "схеме центра обеспечения безопасности шифрование с парольной фразой")](https://msdn.microsoft.com/library/ms190357.aspx)|**Защита с помощью брандмауэра**<br /><br /> [![Брандмауэр Windows в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-windows-firewall.png "брандмауэр Windows в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms175043.aspx)<br /><br /> [![Брандмауэр службы в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-service-firewall.png "брандмауэр службы в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> [![Брандмауэр базы данных в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-db-firewall.png "брандмауэр базы данных в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> **Шифрование данных при передаче**<br /><br /> [![Принудительное включение протокола SSL схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-forced-ssl.png "схеме центра обеспечения безопасности принудительное включение протокола SSL")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> [![Необязательное Включение протокола SSL в схеме центра безопасности](../../database-engine/media/security-center-map-opt-ssl.png "необязательное Включение протокола SSL в схеме центра безопасности")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")|**Автоматизированный аудит**<br /><br /> [![Подсистема аудита SQL Server центра безопасности карты](../../database-engine/media/security-center-map-sql-audit.png "центр безопасности карты Подсистема аудита SQL Server")](https://msdn.microsoft.com/library/cc280386.aspx)<br /><br /> [![Аудит базы данных SQL в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-sqldb-audit.png "аудит базы данных SQL в схеме центра обеспечения безопасности")](http://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> **Пользовательский аудит**<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")<br /><br /> [![Триггеры в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-triggers.png "триггеры в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms175941.aspx)<br /><br /> **Соответствие**<br /><br /> [![SecCtrCompliance](../../database-engine/media/secctrcompliance.png "SecCtrCompliance")](http://azure.microsoft.com/support/trust-center/services/)<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "заполнителя")<br /><br /> ![Условные обозначения центра безопасности](../../database-engine/media/security-center-map-legend.png "условные обозначения центра безопасности")|  
  
## <a name="links-to-specific-related-topics"></a>Ссылки на определенные связанные разделы  
 ![Маленький значок папки](../../integration-services/media/filefolder-small.gif "маленький значок папки") **проверки подлинности: Ты кто?**  
 **Кто выполняет проверку подлинности? (Windows или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])**  
  
-   [Выбор режима проверки подлинности](choose-an-authentication-mode.md)  
  
 **Проверка подлинности в базе данных master** (имена входа и пользователи баз данных)  
  
-   [создать имя входа SQL Server](authentication-access/create-a-login.md)  
  
-   [Управление базами данных и именами входа в базе данных SQL Azure](https://msdn.microsoft.com/library/ee336235.aspx)  
  
-   [Создание пользователя базы данных](authentication-access/create-a-database-user.md)  
  
 **Проверка подлинности в пользовательской базе данных**  
  
-   [Пользователи автономной базы данных — создание переносимой базы данных](contained-database-users-making-your-database-portable.md)  
  
 **Использование других идентификаторов**  
  
-   [Учетные данные (компонент Database Engine)](authentication-access/credentials-database-engine.md)  
  
-   [Выполнение в контексте другого имени входа](/sql/t-sql/statements/execute-as-transact-sql)  
  
-   [Выполнение от имени другого пользователя базы данных](/sql/t-sql/statements/execute-as-transact-sql)  
  
 ![Маленький значок папки](../../integration-services/media/filefolder-small.gif "маленький значок папки") **шифрования: Хранение секретных данных**  
 **Шифрование файлов**  
  
-   [BitLocker (уровень диска)](https://support.microsoft.com/kb/2855131)  
  
-   [Шифрование NTFS (уровень папки)](https://msdn.microsoft.com/library/dd163562.aspx)  
  
-   [Прозрачное шифрование данных (уровень файла)](encryption/transparent-data-encryption.md)  
  
-   [Шифрование резервной копии (уровень файла)](../backup-restore/backup-encryption.md)  
  
 **Шифрование источников**  
  
-   [Расширяемый модуль управление ключами](encryption/extensible-key-management-ekm.md)  
  
-   [Ключи, хранящиеся в хранилище ключей Azure](encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
 **Столбец, данных и ключа шифрования**  
  
-   [Шифрование по сертификату](/sql/t-sql/functions/encryptbycert-transact-sql)  
  
-   [Шифрование асимметричным ключом](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
  
-   [Шифрование симметричным ключом](/sql/t-sql/functions/encryptbykey-transact-sql)  
  
-   [Шифрование с парольной фразой](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
  
 ![Маленький значок папки](../../integration-services/media/filefolder-small.gif "маленький значок папки") **авторизации: Что можно сделать?**  
 **Предоставление, отмена и запрет разрешений**  
  
-   [Иерархия разрешений (компонент Database Engine)](permissions-hierarchy-database-engine.md)  
  
-   [Разрешения](permissions-database-engine.md)  
  
-   [Защищаемые объекты](securables.md)  
  
 **Роли безопасности**  
  
-   [Роли уровня сервера](authentication-access/server-level-roles.md)  
  
-   [Роли уровня базы данных](authentication-access/database-level-roles.md)  
  
 `Restricting Data Access to Selected Data Elements`  
  
-   Ограничение доступа к данным с помощью [представлений](../views/views.md) и [процедур](../stored-procedures/stored-procedures-database-engine.md)  
  
-   [Безопасность на уровне строк](https://msdn.microsoft.com/library/azure/dn765131.aspx)  
  
-   [Маскирование динамических данных](http://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)  
  
-   [Подписанные объекты](/sql/t-sql/statements/add-signature-transact-sql)  
  
 ![Маленький значок папки](../../integration-services/media/filefolder-small.gif "маленький значок папки") **безопасность подключения: Ограничения и обеспечение безопасности**  
 **Защита с помощью брандмауэра**  
  
-   [Настройка брандмауэра Windows для доступа к компоненту Database Engine](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
  
-   [Параметры брандмауэра базы данных Azure SQL](/sql/relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database)  
  
-   [Параметры брандмауэра службы Azure](/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database)  
  
 **Шифрование данных при передаче**  
  
-   [Secure Sockets Layer для компонента Database Engine](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
-   [Secure Sockets Layer для базы данных SQL](https://msdn.microsoft.com/library/azure/ff394108.aspx)  
  
 ![Маленький значок папки](../../integration-services/media/filefolder-small.gif "маленький значок папки") **аудита: Доступ на запись**  
 **Автоматизированный аудит**  
  
-   [Подсистема аудита SQL Server (компонент Database Engine)](auditing/sql-server-audit-database-engine.md)  
  
-   [Аудит базы данных SQL](http://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)  
  
 **Реализация пользовательского аудита**  
  
-   Создание [DDL Triggers](../triggers/ddl-triggers.md) и [DML Triggers](../triggers/dml-triggers.md)  
  
 ![Маленький значок папки](../../integration-services/media/filefolder-small.gif "маленький значок папки") **соответствия**  
 **SQL Server**  
  
-   [Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319)  
  
 **База данных SQL**  
  
-   [Центр управления безопасностью Microsoft Azure: Соответствие функций требованиям регулирования](http://azure.microsoft.com/support/trust-center/services/)  
  
## <a name="see-also"></a>См. также  
 [Обеспечение безопасности SQL Server](securing-sql-server.md)   
 [Участники (компонент Database Engine)](authentication-access/principals-database-engine.md)   
 [Сертификаты SQL Server и асимметричные ключи](sql-server-certificates-and-asymmetric-keys.md)   
 [Шифрование SQL Server](encryption/sql-server-encryption.md)   
 [Настройка контактной зоны](surface-area-configuration.md)   
 [Надежные пароли](strong-passwords.md)   
 [Свойство базы данных TRUSTWORTHY](trustworthy-database-property.md)   
 [Функции и задачи компонента Database Engine](../../database-engine/database-engine-features-and-tasks.md)  
  
  
