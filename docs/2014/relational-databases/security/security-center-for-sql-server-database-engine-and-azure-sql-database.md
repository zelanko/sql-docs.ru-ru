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
ms.openlocfilehash: 131fb3639f84c1b59796d59bcfff17159da8f063
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028658"
---
# <a name="security-center-for-sql-server-database-engine-and-azure-sql-database"></a>Центр обеспечения безопасности для базы данных Azure SQL и SQL Server Database Engine
  На этой странице представлены ссылки, помогающие найти сведения, касающиеся безопасности и защиты в компонентах [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].  
  
> [!NOTE]  
>  Возможности [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] постоянно совершенствуются. См. самую последнюю версию этой статьи для получения последних сведений о [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
|Идентификаци кто вы?|Проверки что можно делать?|Ключ хранение секретных данных|Безопасность подключения: ограничения и обеспечение безопасности|Аудит. регистрация доступа|  
|----------------------------------|-------------------------------------|-------------------------------------|---------------------------------------------------|--------------------------------|  
|**Кто выполняет проверку подлинности?**<br /><br /> [![Проверка подлинности Windows в карте центра безопасности](../../database-engine/media/security-center-map-windows-authenticaion.png "Проверка подлинности Windows в карте центра безопасности")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> <br /><br /> [![Проверка Подлинности SQL Server схемы центра безопасности](../../database-engine/media/security-center-map-sql-authenticaion.png "Проверка Подлинности SQL Server схемы центра безопасности")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> **Где выполняется проверка подлинности?**<br /><br /> [![Имена входа и пользователи схемы центра безопасности](../../database-engine/media/security-center-map-logins-users.png "Имена входа и пользователи схемы центра безопасности")](https://msdn.microsoft.com/library/aa337562.aspx)<br /><br /> <br /><br /> [![Пользователи автономной базы данных схемы центра безопасности](../../database-engine/media/security-center-map-contained-users.png "Пользователи автономной базы данных схемы центра безопасности")](https://msdn.microsoft.com/library/ff929188.aspx)<br /><br /> **Использование других идентификаторов**<br /><br /> [![Учетные данные для схемы центра безопасности](../../database-engine/media/security-center-map-credentials.png "Учетные данные для схемы центра безопасности")](https://msdn.microsoft.com/library/ms161950.aspx)<br /><br /> [![Имя входа для выполнения схемы центра безопасности](../../database-engine/media/security-center-map-exec-as-login.png "Имя входа для выполнения схемы центра безопасности")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> [![Пользователь с картой центра безопасности "выполнение от имени](../../database-engine/media/security-center-map-exec-as-user.png "Пользователь с картой центра безопасности \"выполнение от имени")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")|**Предоставление, отмена и запрет разрешений**<br /><br /> [![Защищаемые классы схемы центра безопасности](../../database-engine/media/security-center-map-securable-classes.png "Защищаемые классы схемы центра безопасности")](https://msdn.microsoft.com/library/ms190401.aspx)<br /><br /> [![Разрешения сервера схемы центра безопасности](../../database-engine/media/security-center-map-srv-perms.png "Разрешения сервера схемы центра безопасности")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> [![Разрешения базы данных схемы центра безопасности](../../database-engine/media/security-center-map-db-perms.png "Разрешения базы данных схемы центра безопасности")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> **Роли безопасности**<br /><br /> [![Роли сервера схемы центра безопасности](../../database-engine/media/security-center-map-srv-roles.png "Роли сервера схемы центра безопасности")](https://msdn.microsoft.com/library/ms188659.aspx)<br /><br /> [![Роли базы данных схемы центра безопасности](../../database-engine/media/security-center-map-db-roles.png "Роли базы данных схемы центра безопасности")](https://msdn.microsoft.com/library/ms189121.aspx)<br /><br /> `Restricting Data Access to Selected Data Elements`<br /><br /> [![Представления и процедуры для карт центра безопасности](../../database-engine/media/security-center-map-view-procs.png "Представления и процедуры для карт центра безопасности")](https://msdn.microsoft.com/library/ms175503.aspx)<br /><br /> [![Безопасность на уровне строк схемы центра безопасности](../../database-engine/media/security-center-map-row-level-sec.png "Безопасность на уровне строк схемы центра безопасности")](https://msdn.microsoft.com/library/dn765131.aspx)<br /><br /> [![Динамическое маскирование данных схемы центра безопасности](../../database-engine/media/security-center-map-data-masking.png "Динамическое маскирование данных схемы центра безопасности")](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [![Подписанные объекты в схеме центра безопасности](../../database-engine/media/security-center-map-signed-objects.png "Подписанные объекты в схеме центра безопасности")](https://msdn.microsoft.com/library/ms181700.aspx)<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")|**Шифрование файлов**<br /><br /> [![BitLocker в карте центра безопасности](../../database-engine/media/security-center-map-bitlocker.png "BitLocker в карте центра безопасности")](https://support.microsoft.com/en-us/kb/2855131)<br /><br /> [![Шифрование NTFS с картой центра безопасности](../../database-engine/media/security-center-map-ntfs-encryp.png "Шифрование NTFS с картой центра безопасности")](https://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [![TDE схемы центра безопасности](../../database-engine/media/security-center-map-tde.png "TDE схемы центра безопасности")](https://msdn.microsoft.com/library/bb934049.aspx)<br /><br /> [![Шифрование резервной копии схемы центра безопасности](../../database-engine/media/security-center-map-backup-encryp.png "Шифрование резервной копии схемы центра безопасности")](https://msdn.microsoft.com/library/dn449489.aspx)<br /><br /> **Шифрование источников**<br /><br /> [![Расширенное управление ключами схемы центра безопасности](../../database-engine/media/security-center-map-ekm.png "Расширенное управление ключами схемы центра безопасности")](https://msdn.microsoft.com/library/bb895340.aspx)<br /><br /> [![Azure Key Vault схемы центра безопасности](../../database-engine/media/security-center-map-key-vault.png "Azure Key Vault схемы центра безопасности")](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)<br /><br /> **Шифрование ключа столбца, & данных**<br /><br /> [![Шифрование на карте центра безопасности по сертификату](../../database-engine/media/security-center-map-cert.png "Шифрование на карте центра безопасности по сертификату")](https://msdn.microsoft.com/library/ms188061.aspx)<br /><br /> [![Шифрование по симметричному ключу на карте центра безопасности](../../database-engine/media/security-center-map-sym-key.png "Шифрование по симметричному ключу на карте центра безопасности")](https://msdn.microsoft.com/library/ms174361.aspx)<br /><br /> [![Шифрование с помощью асимметричного ключа на карте центра безопасности](../../database-engine/media/security-center-map-asym-key.png "Шифрование с помощью асимметричного ключа на карте центра безопасности")](https://msdn.microsoft.com/library/ms186950.aspx)<br /><br /> [![Шифрование с помощью парольной фразы для схемы центра безопасности](../../database-engine/media/security-center-map-passphrase.png "Шифрование с помощью парольной фразы для схемы центра безопасности")](https://msdn.microsoft.com/library/ms190357.aspx)|**Защита с помощью брандмауэра**<br /><br /> [![Брандмауэр Windows для схемы центра безопасности](../../database-engine/media/security-center-map-windows-firewall.png "Брандмауэр Windows для схемы центра безопасности")](https://msdn.microsoft.com/library/ms175043.aspx)<br /><br /> [![Брандмауэр службы карт центра безопасности](../../database-engine/media/security-center-map-service-firewall.png "Брандмауэр службы карт центра безопасности")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> [![Брандмауэр базы данных схемы центра безопасности](../../database-engine/media/security-center-map-db-firewall.png "Брандмауэр базы данных схемы центра безопасности")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> **Шифрование данных при передаче**<br /><br /> [![Принудительный SSL схемы центра безопасности](../../database-engine/media/security-center-map-forced-ssl.png "Принудительный SSL схемы центра безопасности")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> [![Необязательный протокол SSL в схеме центра безопасности](../../database-engine/media/security-center-map-opt-ssl.png "Необязательный протокол SSL в схеме центра безопасности")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")|**Автоматизированный аудит**<br /><br /> [![Аудит SQL Server для схемы центра безопасности](../../database-engine/media/security-center-map-sql-audit.png "Аудит SQL Server для схемы центра безопасности")](https://msdn.microsoft.com/library/cc280386.aspx)<br /><br /> [![Аудит базы данных SQL схемы центра безопасности](../../database-engine/media/security-center-map-sqldb-audit.png "Аудит базы данных SQL схемы центра безопасности")](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> **Пользовательский аудит**<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")<br /><br /> [![Триггеры схемы центра безопасности](../../database-engine/media/security-center-map-triggers.png "Триггеры схемы центра безопасности")](https://msdn.microsoft.com/library/ms175941.aspx)<br /><br /> **Соответствие**<br /><br /> [![Секктркомплианце](../../database-engine/media/secctrcompliance.png "Секктркомплианце")](https://azure.microsoft.com/support/trust-center/services/)<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")<br /><br /> ![Заполнитель](../../database-engine/media/security-center-map-blankplaceholder.png "Заполнитель")<br /><br /> ![Условные обозначения центра безопасности](../../database-engine/media/security-center-map-legend.png "Условные обозначения центра безопасности")|  
  
## <a name="links-to-specific-related-topics"></a>Ссылки на определенные связанные разделы  
 ![Маленький значок папки с файлами](../../integration-services/media/filefolder-small.gif "Маленький значок папки с файлами") **Проверка подлинности: Ты кто?**  
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
  
 ![Маленький значок папки с файлами](../../integration-services/media/filefolder-small.gif "Маленький значок папки с файлами") **Шифрование: Хранение секретных данных**  
 **Шифрование файлов**  
  
-   [BitLocker (уровень диска)](https://support.microsoft.com/kb/2855131)  
  
-   [Шифрование NTFS (уровень папки)](https://msdn.microsoft.com/library/dd163562.aspx)  
  
-   [Прозрачное шифрование данных (уровень файла)](encryption/transparent-data-encryption.md)  
  
-   [Шифрование резервной копии (уровень файла)](../backup-restore/backup-encryption.md)  
  
 **Шифрование источников**  
  
-   [Расширяемый модуль управление ключами](encryption/extensible-key-management-ekm.md)  
  
-   [Ключи, хранящиеся в хранилище ключей Azure](encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
 **Шифрование столбцов, данных и ключей**  
  
-   [Шифрование по сертификату](/sql/t-sql/functions/encryptbycert-transact-sql)  
  
-   [Шифрование асимметричным ключом](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
  
-   [Шифрование симметричным ключом](/sql/t-sql/functions/encryptbykey-transact-sql)  
  
-   [Шифрование с парольной фразой](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
  
 ![Маленький значок папки с файлами](../../integration-services/media/filefolder-small.gif "Маленький значок папки с файлами") **Авторизация: Что можно сделать?**  
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
  
-   [Маскирование динамических данных](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)  
  
-   [Подписанные объекты](/sql/t-sql/statements/add-signature-transact-sql)  
  
 ![Маленький значок папки с файлами](../../integration-services/media/filefolder-small.gif "Маленький значок папки с файлами") **Безопасность подключения: Защита и обеспечение безопасности**  
 **Защита с помощью брандмауэра**  
  
-   [Настройка брандмауэра Windows для доступа к компоненту Database Engine](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
  
-   [Параметры брандмауэра базы данных Azure SQL](/sql/relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database)  
  
-   [Параметры брандмауэра службы Azure](/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database)  
  
 **Шифрование данных при передаче**  
  
-   [Secure Sockets Layer для компонента Database Engine](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
-   [Secure Sockets Layer для базы данных SQL](https://msdn.microsoft.com/library/azure/ff394108.aspx)  
  
 ![Маленький значок папки с файлами](../../integration-services/media/filefolder-small.gif "Маленький значок папки с файлами") **Аудит: Запись доступа**  
 **Автоматизированный аудит**  
  
-   [Подсистема аудита SQL Server (компонент Database Engine)](auditing/sql-server-audit-database-engine.md)  
  
-   [Аудит базы данных SQL](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)  
  
 **Реализация пользовательского аудита**  
  
-   Создание [DDL Triggers](../triggers/ddl-triggers.md) и [DML Triggers](../triggers/dml-triggers.md)  
  
 ![Маленький значок папки с файлами](../../integration-services/media/filefolder-small.gif "Маленький значок папки с файлами") **Соответствие требованиям**  
 **SQL Server**  
  
-   [Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319)  
  
 **База данных SQL**  
  
-   [Центр управления безопасностью Microsoft Azure: соответствие функций нормативным требованиям](https://azure.microsoft.com/support/trust-center/services/)  
  
## <a name="see-also"></a>См. также  
 [Обеспечение безопасности SQL Server](securing-sql-server.md)   
 [Участники (компонент Database Engine)](authentication-access/principals-database-engine.md)   
 [Сертификаты SQL Server и асимметричные ключи](sql-server-certificates-and-asymmetric-keys.md)   
 [Шифрование SQL Server](encryption/sql-server-encryption.md)   
 [Настройка контактной зоны](surface-area-configuration.md)   
 [Надежные пароли](strong-passwords.md)   
 [Свойство базы данных TRUSTWORTHY](trustworthy-database-property.md)   
 [Функции и задачи компонента Database Engine](../../database-engine/database-engine-features-and-tasks.md)  
  
  
