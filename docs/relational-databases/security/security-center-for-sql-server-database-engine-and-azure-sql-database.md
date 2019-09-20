---
title: Центр обеспечения безопасности для базы данных Azure SQL и ядра СУБД SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 09/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 86d3f0bcc0d791a025165d8bda3188d443fce1e1
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874835"
---
# <a name="security-center-for-sql-server-database-engine-and-azure-sql-database"></a>Центр обеспечения безопасности для базы данных Azure SQL и SQL Server Database Engine
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  На этой странице представлены ссылки, помогающие найти сведения, касающиеся безопасности и защиты в компоненте [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)].  
  
 **Условные обозначения**  
  
 ![security-center-legend](../performance/media/security-center-legend.PNG "security-center-legend")  
  
##  <a name="Who"></a> Проверка подлинности: кто вы?  
  
|||  
|-|-|  
|**Кто выполняет проверку подлинности?**<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Проверка подлинности Windows<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Проверка подлинности<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") Azure Active Directory|Кто выполняет проверку подлинности? (Windows или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])<br /><br /> [Выбор режима проверки подлинности](../../relational-databases/security/choose-an-authentication-mode.md)<br /><br /> [Подключение к базе данных SQL с использованием аутентификации Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)|  
|**Где выполняется проверка подлинности?**<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") В базе данных master: имена для входа и пользователи базы данных<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") В пользовательской базе данных: включенные пользователи базы данных|Аутентификация в базе данных master (имена для входа и пользователи базы данных)<br /><br /> [создать имя входа SQL Server](../../relational-databases/security/authentication-access/create-a-login.md)<br /><br /> [Управление базами данных и именами входа в базе данных SQL Azure](https://msdn.microsoft.com/library/ee336235.aspx)<br /><br /> [Создание пользователя базы данных](../../relational-databases/security/authentication-access/create-a-database-user.md)<br /><br /> <br /><br /> Проверка подлинности в пользовательской базе данных<br /><br /> [Пользователи автономной базы данных — создание переносимой базы данных](../../relational-databases/security/contained-database-users-making-your-database-portable.md)|  
|**Использование других идентификаторов**<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Учетные данные<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security center-sqlserver") Выполнение от другого имени для входа<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Выполнение от имени другого пользователя базы данных|[Учетные данные (компонент Database Engine)](../../relational-databases/security/authentication-access/credentials-database-engine.md)<br /><br /> [Выполнение в контексте другого имени входа](../../t-sql/statements/execute-as-transact-sql.md)<br /><br /> [Выполнение от имени другого пользователя базы данных](../../t-sql/statements/execute-as-transact-sql.md)|  
  
##  <a name="What"></a> Авторизация: что можно делать?  
  
|||  
|-|-|  
|**Предоставление, отмена и запрет разрешений**<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Защищаемые классы<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security center-sqlserver") Детализированные разрешения сервера<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Детализированные разрешения базы данных|[Иерархия разрешений (компонент Database Engine)](../../relational-databases/security/permissions-hierarchy-database-engine.md)<br /><br /> [Разрешения](../../relational-databases/security/permissions-database-engine.md)<br /><br /> [Защищаемые объекты](../../relational-databases/security/securables.md)<br /><br /> [Приступая к работе с разрешениями Database Engine](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)|  
|**Роли безопасности**<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Роли уровня сервера<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Роли уровня базы данных|[Роли уровня сервера](../../relational-databases/security/authentication-access/server-level-roles.md)<br /><br /> [Роли уровня базы данных](../../relational-databases/security/authentication-access/database-level-roles.md)|  
|**Ограничение доступа к данным для выбранных элементов**<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Ограничение доступа к данным с помощью представлений и процедур<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Безопасность на уровне строк<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Динамическое маскирование данных<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Подписанные объекты|Ограничение доступа к данным с помощью [представлений](../../relational-databases/views/views.md) и [процедур](../../relational-databases/stored-procedures/stored-procedures-database-engine.md)<br /><br /> [Безопасность на уровне строк (SQL Server)](../../relational-databases/security/row-level-security.md)<br /><br /> [Безопасность на уровне строк (база данных SQL Azure)](https://msdn.microsoft.com/library/azure/dn765131.aspx)<br /><br /> [Динамическое маскирование данных (SQL Server)](../../relational-databases/security/dynamic-data-masking.md)<br /><br /> [Динамическое маскирование данных (база данных Azure SQL)](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [Подписанные объекты](../../t-sql/statements/add-signature-transact-sql.md)|  
  
##  <a name="Encrypt"></a> Шифрование: хранение секретных данных  
  
|||  
|-|-|  
|**Шифрование файлов**<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Шифрование BitLocker (уровень диска)<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Шифрование NTFS (уровень папки)<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Прозрачное шифрование данных (уровень файла)<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Шифрование резервной копии (уровень файла)|[BitLocker (уровень диска)](https://support.microsoft.com/kb/2855131)<br /><br /> [Шифрование NTFS (уровень папки)](https://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [Прозрачное шифрование данных (уровень файла)](../../relational-databases/security/encryption/transparent-data-encryption.md)<br /><br /> [Шифрование резервной копии (уровень файла)](../../relational-databases/backup-restore/backup-encryption.md)|  
|**Шифрование источников**<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Расширяемый модуль управления ключами<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Ключи, хранящиеся в Azure Key Vault<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Постоянное шифрование|[Расширяемый модуль управление ключами](../../relational-databases/security/encryption/extensible-key-management-ekm.md)<br /><br /> [Ключи, хранящиеся в хранилище ключей Azure](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)<br /><br /> [Постоянное шифрование](../../relational-databases/security/encryption/always-encrypted-database-engine.md)|  
|**Шифрование столбцов, данных и ключей**<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Шифрование по сертификату<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Шифрование симметричным ключом<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Шифрование асимметричным ключом<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Шифрование по парольной фразе|[Шифрование по сертификату](../../t-sql/functions/encryptbycert-transact-sql.md)<br /><br /> [Шифрование асимметричным ключом](../../t-sql/functions/encryptbyasymkey-transact-sql.md)<br /><br /> [Шифрование симметричным ключом](../../t-sql/functions/encryptbykey-transact-sql.md)<br /><br /> [Шифрование с парольной фразой](../../t-sql/functions/encryptbypassphrase-transact-sql.md)<br /><br /> [Шифрование столбца данных](../../relational-databases/security/encryption/encrypt-a-column-of-data.md)|  
  
##  <a name="Connect"></a> Безопасность подключения: ограничения и обеспечение безопасности  
  
|||  
|-|-|  
|**Защита с помощью брандмауэра**<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Параметры брандмауэра Windows<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") Параметры брандмауэра службы Azure<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") Параметры брандмауэра базы данных|[Настройка брандмауэра Windows для доступа к компоненту Database Engine](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)<br /><br /> [Параметры брандмауэра базы данных Azure SQL](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)<br /><br /> [Параметры брандмауэра службы Azure](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)|  
|**Шифрование данных при передаче**<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Принудительные подключения SSL<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Необязательные подключения SSL|[Secure Sockets Layer для компонента Database Engine](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)<br /><br /> [Secure Sockets Layer для базы данных SQL](https://msdn.microsoft.com/library/azure/ff394108.aspx)<br /><br /> [Поддержка TLS 1.2 для Microsoft SQL Server](https://support.microsoft.com/kb/3135244)|  
  
##  <a name="Audit"></a> Аудит: регистрация доступа  
  
|||  
|-|-|  
|**Автоматизированный аудит**<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Аудит (уровень сервера и базы данных)<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Аудит (уровень базы данных)<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") Обнаружение угроз| <br /><br /> [Подсистема аудита SQL Server (компонент Database Engine)](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)<br /><br /> [Аудит базы данных SQL](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> [Приступая к работе с Расширенной защитой от угроз для базы данных SQL](https://azure.microsoft.com/documentation/articles/sql-database-threat-detection-get-started/) <br /><br /> [Оценка уязвимостей базы данных SQL](https://docs.microsoft.com/azure/sql-database/sql-vulnerability-assessment) |  
|**Пользовательский аудит**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Триггеры|Реализация пользовательского аудита: Создание [DDL Triggers](../../relational-databases/triggers/ddl-triggers.md) и [DML Triggers](../../relational-databases/triggers/dml-triggers.md)|  
|**Соответствие**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Соответствие|SQL Server: стандарт<br />                        [Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319)<br /><br /> База данных SQL:<br />                        [Центр управления безопасностью Microsoft Azure: соответствие функций нормативным требованиям](https://azure.microsoft.com/support/trust-center/services/)|  
  
##  <a name="SQLInjection"></a> Атака путем внедрения кода SQL  
 Внедрение кода SQL — это атака, при которой производится вставка вредоносного кода в строки, передающиеся затем в [!INCLUDE[ssDE](../../includes/ssde-md.md)] для анализа и выполнения. Любая процедура, создающая инструкции SQL, должна рассматриваться на предмет уязвимости к вставке небезопасного кода, поскольку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет все получаемые синтаксически правильные запросы. Все системы базы данных подвержены риску атак путем внедрения кода SQL, и многие уязвимости представлены в приложении, которое запрашивает [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Можно предотвратить атаки путем внедрения кода SQL, используя хранимые процедуры и параметризованные команды, избегая использования динамического кода SQL и ограничив разрешения для всех пользователей.  Дополнительные сведения см. в разделе [SQL Injection](../../relational-databases/security/sql-injection.md).  
  
 Дополнительные ссылки для программистов приложений.  
  
-   [Сценарии безопасности приложений в SQL Server](/dotnet/framework/data/adonet/sql/application-security-scenarios-in-sql-server)  
  
-   [Написание безопасного динамического кода SQL в SQL Server](/dotnet/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server)  
  
-   [Руководство. Предотвращение внедрения SQL в ASP.NET](https://msdn.microsoft.com/library/ff648339.aspx)  
  
## <a name="see-also"></a>См. также:  
 [Приступая к работе с разрешениями Database Engine](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [Обеспечение безопасности SQL Server](../../relational-databases/security/securing-sql-server.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Сертификаты SQL Server и асимметричные ключи](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md)   
 [Шифрование SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [Настройка контактной зоны](../../relational-databases/security/surface-area-configuration.md)   
 [Надежные пароли](../../relational-databases/security/strong-passwords.md)   
 [Свойство базы данных TRUSTWORTHY](../../relational-databases/security/trustworthy-database-property.md)   
 [Функции и задачи компонента Database Engine](https://msdn.microsoft.com/library/d9efe145-3306-4d61-bd77-e2af43e19c34)  
 [Защита интеллектуальной собственности SQL Server](../../relational-databases/security/protecting-your-sql-server-intellectual-property.md)   
  
[!INCLUDE[get-help-security](../../includes/get-help-security.md)]
