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
ms.openlocfilehash: fc99b725f4c5895306d544df14bf2a9390189066
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75244526"
---
# <a name="security-center-for-sql-server-database-engine-and-azure-sql-database"></a>Центр обеспечения безопасности для базы данных Azure SQL и SQL Server Database Engine
  На этой странице представлены ссылки, помогающие найти сведения, касающиеся безопасности и защиты в компонентах [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].  
  
> [!NOTE]  
>  Возможности [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] постоянно совершенствуются. См. самую последнюю версию этой статьи для получения последних сведений о [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
|Проверка подлинности: кто вы?|Авторизация: что вам можно делать?|Шифрование: хранение секретных данных|Безопасность подключения: ограничения и обеспечение безопасности|Аудит: регистрация доступа|  
|----------------------------------|-------------------------------------|-------------------------------------|---------------------------------------------------|--------------------------------|  
|**Кто выполняет проверку подлинности?**<br /><br /> [![Проверка подлинности Windows в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-windows-authenticaion.png "Проверка подлинности Windows в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> <br /><br /> [![Проверка подлинности SQL Server в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-sql-authenticaion.png "Проверка подлинности SQL Server в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> **Где проверяются подлинность?**<br /><br /> [![Имена входа и пользователи в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-logins-users.png "Имена входа и пользователи в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/aa337562.aspx)<br /><br /> <br /><br /> [![Пользователи автономной базы данных в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-contained-users.png "Пользователи автономной базы данных в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ff929188.aspx)<br /><br /> **Использование других удостоверений**<br /><br /> [![Учетные данные в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-credentials.png "Учетные данные в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms161950.aspx)<br /><br /> [![Инструкция EXECUTE AS LOGIN в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-exec-as-login.png "Инструкция EXECUTE AS LOGIN в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> [![Инструкция EXECUTE AS USER в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-exec-as-user.png "Инструкция EXECUTE AS USER в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")|**Предоставление, отмена и запрет разрешений**<br /><br /> [![Защищаемые классы в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-securable-classes.png "Защищаемые классы в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms190401.aspx)<br /><br /> [![Разрешения сервера в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-srv-perms.png "Разрешения сервера в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> [![Разрешения базы данных в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-db-perms.png "Разрешения базы данных в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> **Безопасность по ролям**<br /><br /> [![Роли сервера в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-srv-roles.png "Роли сервера в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms188659.aspx)<br /><br /> [![Роли базы данных в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-db-roles.png "Роли базы данных в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms189121.aspx)<br /><br /> `Restricting Data Access to Selected Data Elements`<br /><br /> [![Представления и процедуры в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-view-procs.png "Представления и процедуры в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms175503.aspx)<br /><br /> [![Безопасность на уровне строк в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-row-level-sec.png "Безопасность на уровне строк в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/dn765131.aspx)<br /><br /> [![Динамическое маскирование данных в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-data-masking.png "Динамическое маскирование данных в схеме центра обеспечения безопасности")](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [![Подписанные объекты в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-signed-objects.png "Подписанные объекты в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms181700.aspx)<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")|**Шифрование файлов**<br /><br /> [![BitLocker в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-bitlocker.png "BitLocker в схеме центра обеспечения безопасности")](https://support.microsoft.com/kb/2855131)<br /><br /> [![Шифрование NTFS в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-ntfs-encryp.png "Шифрование NTFS в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [![Прозрачное шифрование данных в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-tde.png "Прозрачное шифрование данных в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/bb934049.aspx)<br /><br /> [![Шифрование резервной копии в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-backup-encryp.png "Шифрование резервной копии в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/dn449489.aspx)<br /><br /> **Шифрование источников**<br /><br /> [![Расширенное управление ключами в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-ekm.png "Расширенное управление ключами в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/bb895340.aspx)<br /><br /> [![Хранилище ключей Azure в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-key-vault.png "Хранилище ключей Azure в схеме центра обеспечения безопасности")](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)<br /><br /> **Шифрование ключа столбца, & данных**<br /><br /> [![Шифрование на карте центра безопасности по сертификату](../../database-engine/media/security-center-map-cert.png "Шифрование на карте центра безопасности по сертификату")](https://msdn.microsoft.com/library/ms188061.aspx)<br /><br /> [![Шифрование симметричным ключом в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-sym-key.png "Шифрование симметричным ключом в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms174361.aspx)<br /><br /> [![Шифрование асимметричным ключом в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-asym-key.png "Шифрование асимметричным ключом в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms186950.aspx)<br /><br /> [![Шифрование с помощью парольной фразы в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-passphrase.png "Шифрование с помощью парольной фразы в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms190357.aspx)|**Защита брандмауэра**<br /><br /> [![Брандмауэр Windows в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-windows-firewall.png "Брандмауэр Windows в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms175043.aspx)<br /><br /> [![Брандмауэр службы в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-service-firewall.png "Брандмауэр службы в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> [![Брандмауэр базы данных в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-db-firewall.png "Брандмауэр базы данных в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> **Шифрование данных при передаче**<br /><br /> [![Принудительное включение протокола SSL в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-forced-ssl.png "Принудительное включение протокола SSL в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> [![Необязательное включение протокола SSL в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-opt-ssl.png "Необязательное включение протокола SSL в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")|**Автоматический аудит**<br /><br /> [![Аудит SQL Server в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-sql-audit.png "Аудит SQL Server в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/cc280386.aspx)<br /><br /> [![Аудит Базы данных SQL в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-sqldb-audit.png "Аудит Базы данных SQL в схеме центра обеспечения безопасности")](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> **Настраиваемый аудит**<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> [![Триггеры в схеме центра обеспечения безопасности](../../database-engine/media/security-center-map-triggers.png "Триггеры в схеме центра обеспечения безопасности")](https://msdn.microsoft.com/library/ms175941.aspx)<br /><br /> **Имевшее**<br /><br /> [![секктркомплианце](../../database-engine/media/secctrcompliance.png "секктркомплианце")](https://azure.microsoft.com/support/trust-center/services/)<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Условные обозначения центра обеспечения безопасности](../../database-engine/media/security-center-map-legend.png "Условные обозначения центра обеспечения безопасности")|  
  
## <a name="links-to-specific-related-topics"></a>Ссылки на определенные связанные разделы  
 ![Маленький значок папки](../../integration-services/media/filefolder-small.gif "Маленький значок папки") **Проверка подлинности: кто вы?**  
 **Кто выполняет проверку подлинности? (Windows или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])**  
  
-   [Выбор режима проверки подлинности](choose-an-authentication-mode.md)  
  
 **Проверка подлинности в базе данных master** (имена входа и пользователи базы данных)  
  
-   [Создание имени входа SQL Server](authentication-access/create-a-login.md)  
  
-   [Управление базами данных и именами входа в базе данных SQL Azure](https://msdn.microsoft.com/library/ee336235.aspx)  
  
-   [Создание пользователя базы данных](authentication-access/create-a-database-user.md)  
  
 **Проверка подлинности в пользовательской базе данных**  
  
-   [Пользователи автономной базы данных — Создание переносимой базы данных](contained-database-users-making-your-database-portable.md)  
  
 **Использование других удостоверений**  
  
-   [Учетные данные &#40;ядро СУБД&#41;](authentication-access/credentials-database-engine.md)  
  
-   [Выполнить как другое имя для входа](/sql/t-sql/statements/execute-as-transact-sql)  
  
-   [Выполнение от имени другого пользователя базы данных](/sql/t-sql/statements/execute-as-transact-sql)  
  
 ![Маленький значок папки](../../integration-services/media/filefolder-small.gif "Маленький значок папки") **Шифрование: хранение секретных данных**  
 **Шифрование файлов**  
  
-   [BitLocker (уровень диска)](https://support.microsoft.com/kb/2855131)  
  
-   [Шифрование NTFS (уровень папки)](https://msdn.microsoft.com/library/dd163562.aspx)  
  
-   [Прозрачное шифрование данных (уровень файла)](encryption/transparent-data-encryption.md)  
  
-   [Шифрование резервной копии (уровень файла)](../backup-restore/backup-encryption.md)  
  
 **Шифрование источников**  
  
-   [Расширяемый модуль управления ключами](encryption/extensible-key-management-ekm.md)  
  
-   [Ключи, хранящиеся в Azure Key Vault](encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
 **Шифрование столбцов, данных и ключей**  
  
-   [Шифрование по сертификату](/sql/t-sql/functions/encryptbycert-transact-sql)  
  
-   [Шифрование асимметричным ключом](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
  
-   [Шифрование симметричным ключом](/sql/t-sql/functions/encryptbykey-transact-sql)  
  
-   [Шифрование с помощью парольной фразы](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
  
 ![Маленький значок папки с файлами](../../integration-services/media/filefolder-small.gif "Маленький значок папки") **авторизация: что можно сделать?**  
 **Предоставление, отмена и запрет разрешений**  
  
-   [Иерархия разрешений &#40;ядро СУБД&#41;](permissions-hierarchy-database-engine.md)  
  
-   [Чтение](permissions-database-engine.md)  
  
-   [Защищаемые объекты](securables.md)  
  
 **Безопасность по ролям**  
  
-   [Роли уровня сервера](authentication-access/server-level-roles.md)  
  
-   [Роли уровня базы данных](authentication-access/database-level-roles.md)  
  
 `Restricting Data Access to Selected Data Elements`  
  
-   Ограничение доступа к данным с помощью [представлений](../views/views.md) и [процедур](../stored-procedures/stored-procedures-database-engine.md)  
  
-   [Безопасность на уровне строк](https://msdn.microsoft.com/library/azure/dn765131.aspx)  
  
-   [динамическое маскирование данных](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)  
  
-   [Подписанные объекты](/sql/t-sql/statements/add-signature-transact-sql)  
  
 ![Маленький значок папки](../../integration-services/media/filefolder-small.gif "Маленький значок папки") **Безопасность подключения: защита и обеспечение безопасности**  
 **Защита брандмауэра**  
  
-   [Настройка брандмауэра Windows для доступа к ядро СУБД](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
  
-   [Параметры брандмауэра базы данных SQL Azure](/sql/relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database)  
  
-   [Параметры брандмауэра службы Azure](/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database)  
  
 **Шифрование данных при передаче**  
  
-   [SSL для ядро СУБД](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
-   [SSL для базы данных SQL](https://msdn.microsoft.com/library/azure/ff394108.aspx)  
  
 ![Маленький значок папки с файлами](../../integration-services/media/filefolder-small.gif "Маленький значок папки") **Аудит: запись доступа**  
 **Автоматический аудит**  
  
-   [SQL Server ядро СУБД &#40;аудита&#41;](auditing/sql-server-audit-database-engine.md)  
  
-   [Аудит базы данных SQL](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)  
  
 **Реализация пользовательского аудита**  
  
-   Создание [DDL Triggers](../triggers/ddl-triggers.md) и [DML Triggers](../triggers/dml-triggers.md)  
  
 ![Маленький значок папки с файлами](../../integration-services/media/filefolder-small.gif "Маленький значок папки") **соответствие**  
 **SQL Server**  
  
-   [Общие критерии](https://go.microsoft.com/fwlink/?LinkId=616319)  
  
 **База данных SQL**  
  
-   [Центр управления безопасностью Microsoft Azure: соответствие по функциям](https://azure.microsoft.com/support/trust-center/services/)  
  
## <a name="see-also"></a>См. также  
 [Защита SQL Server](securing-sql-server.md)   
 [Участники &#40;ядро СУБД&#41;](authentication-access/principals-database-engine.md)   
 [SQL Server сертификаты и асимметричные ключи](sql-server-certificates-and-asymmetric-keys.md)   
 [Шифрование SQL Server](encryption/sql-server-encryption.md)   
 [Настройка контактной зоны](surface-area-configuration.md)   
 [Надежные пароли](strong-passwords.md)   
 [Свойство базы данных TRUSTWORTHY](trustworthy-database-property.md)   
 [Функции и задачи ядро СУБД](../../database-engine/database-engine-features-and-tasks.md)  
  
  
