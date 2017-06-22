---
title: "Обслуживание соединителя SQL Server и устранение неполадок | Документация Майкрософт"
ms.custom: 
ms.date: 04/05/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Connector, appendix
ms.assetid: 7f5b73fc-e699-49ac-a22d-f4adcfae62b1
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: c0e55c0e35039490f0ce4cd8a7fb6d7e232c05aa
ms.openlocfilehash: 0218298a95d1e7df242b3ca7cbae657effead719
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-connector-maintenance-amp-troubleshooting"></a>Обслуживание соединителя SQL Server и устранение неполадок
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Эта статья содержит вспомогательные сведения о Соединителе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Дополнительные сведения о Соединителе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] см. в статьях [Расширенное управление ключами с помощью хранилища ключей Azure &#40;SQL Server&#41;](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md), [Этапы настройки расширенного управления ключами с использованием хранилища ключей Azure](../../../relational-databases/security/encryption/setup-steps-for-extensible-key-management-using-the-azure-key-vault.md) и [Использование Соединителя SQL Server с компонентами шифрования SQL](../../../relational-databases/security/encryption/use-sql-server-connector-with-sql-encryption-features.md).  
  
  
##  <a name="AppendixA"></a> A. Инструкции по обслуживанию Соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
### <a name="key-rollover"></a>Смена ключей  
  
> [!IMPORTANT]  
>  Соединитель [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] требует, чтобы имя ключа содержало только символы a–z, A–Z, 0–9 и "–" и имело длину не более 26 знаков.   
> Разные версии ключа, имеющие одинаковое имя в хранилище ключей Azure, не будут работать с Соединителем [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Чтобы сменить ключ хранилища ключей Azure, используемый [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], необходимо создать ключ с новым именем.  
  
 Асимметричные ключи сервера для шифрования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , как правило, должны меняться каждые 1–2 года. Следует отметить, что несмотря на то, что хранилище ключей предоставляет возможность управления версиями ключей, клиентам не следует использовать эту функцию для реализации управления версиями. Соединитель [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не может работать с изменениями в версии ключа хранилища ключей. Чтобы реализовать смену версии ключа, нужно создать новый ключ в хранилище ключей и повторно зашифровать ключ шифрования данных в [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].  
  
 При прозрачном шифровании данных это можно сделать следующим образом.  
  
-   **В PowerShell:** создайте в хранилище ключей асимметричный ключ (его имя должно отличаться от текущего асимметричного ключа прозрачного шифрования данных).  
  
    ```powershell  
    Add-AzureRmKeyVaultKey -VaultName 'ContosoDevKeyVault' `  
      -Name 'Key2' -Destination 'Software'  
    ```  
  
-   **С помощью [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] или sqlcmd.exe:** используйте следующие инструкции, как показано в этапе 3 раздела 3.  
  
     Импортируйте новый асимметричный ключ.  
  
    ```tsql  
    USE master  
    CREATE ASYMMETRIC KEY [MASTER_KEY2]   
    FROM PROVIDER [EKM]   
    WITH PROVIDER_KEY_NAME = 'Key2',   
    CREATION_DISPOSITION = OPEN_EXISTING   
    GO  
    ```  
  
     Создайте новое имя входа, которое должно быть связано с новым асимметричным ключом (как показано в разделе с инструкциями по прозрачному шифрованию данных).  
  
    ```tsql  
    USE master  
    CREATE LOGIN TDE_Login2   
    FROM ASYMMETRIC KEY [MASTER_KEY2]  
    GO  
    ```  
  
     Создайте учетные данные, сопоставляемые с новым именем входа.  
  
    ```tsql  
    CREATE CREDENTIAL Azure_EKM_TDE_cred2  
        WITH IDENTITY = 'ContosoDevKeyVault',   
       SECRET = 'EF5C8E094D2A4A769998D93440D8115DAADsecret123456789=’   
    FOR CRYPTOGRAPHIC PROVIDER EKM;  
  
    ALTER LOGIN TDE_Login2  
    ADD CREDENTIAL Azure_EKM_TDE_cred2;  
    GO  
    ```  
  
     Выберите базу данных, ключ шифрования которой требуется повторно зашифровать.  
  
    ```tsql  
    USE [database]  
    GO  
    ```  
  
     Повторно зашифруйте ключ шифрования базы данных.  
  
    ```tsql  
    ALTER DATABASE ENCRYPTION KEY   
    ENCRYPTION BY SERVER ASYMMETRIC KEY [MASTER_KEY2];  
    GO  
    ```  
  
### <a name="upgrade-of-includessnoversionincludesssnoversion-mdmd-connector"></a>Обновление Соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  

Версии 1.0.0.440 и старше были заменены и больше не поддерживаются в рабочих средах. Версии 1.0.1.0 и более новые поддерживаются в рабочих средах. Воспользуйтесь приведенными ниже инструкциями, чтобы выполнить обновление до самой последней версии в [Центре загрузки Майкрософт](https://www.microsoft.com/download/details.aspx?id=45344).

Если вы используете версию 1.0.1.0 или более новую, выполните приведенные ниже шаги для обновления до самой последней версии соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Эти инструкции позволяют избежать перезагрузки экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .
 
1. Установите последнюю версию соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из [Центра загрузки Майкрософт](https://www.microsoft.com/download/details.aspx?id=45344). В мастере установки сохраните новый файл библиотеки DLL в папке, отличной от той, где находится файл исходной библиотеки DLL для соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Например, можно использовать следующий новый путь: `C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault\<latest version number>\Microsoft.AzureKeyVaultService.EKM.dll`
 
2. В экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]выполните следующую команду Transact-SQL, чтобы указать экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на новую версию соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :

    ``` 
    ALTER CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov   
    FROM FILE =   
    'C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault\<latest version number>\Microsoft.AzureKeyVaultService.EKM.dll'
    GO  
    ```

Если вы используете версию 1.0.0.440 или более старую, выполните приведенные ниже шаги для обновления до самой последней версии соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .
  
1.  Остановите экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
2.  Остановите службу Соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
3.  Удалите Соединитель [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью компонента Windows "Программы и компоненты".  
  
     (Можно также переименовать папку, содержащую DLL-файл. По умолчанию эта папка называется "[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for Microsoft Azure Key Vault".  
  
4.  Установите последнюю версию Соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из Центра загрузки Майкрософт.  
  
5.  Повторно запустите экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
6.  Выполните следующую инструкцию, чтобы настроить поставщик расширенного управления ключами для использования последней версии Соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Убедитесь, что путь указывает именно на то расположение, куда вы скачали последнюю версию. (Этот шаг можно пропустить, если новая версия устанавливается там же, где и исходная версия.) 
  
    ```tsql  
    ALTER CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov   
    FROM FILE =   
    'C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault\Microsoft.AzureKeyVaultService.EKM.dll';  
    GO  
    ```  
  
7.  Проверьте, что базы данных, использующие прозрачное шифрование, доступны.  
  
8.  После проверки работы обновления можно удалить папку старого соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (если вы решили переименовать его вместо удаления в шаге 3).  
  
### <a name="rolling-the-includessnoversionincludesssnoversion-mdmd-service-principal"></a>Смена субъекта-службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует субъекты-службы, созданные в Azure Active Directory, в качестве учетных данных для доступа к хранилищу ключей.  Субъект-служба имеет идентификатор клиента и ключ проверки подлинности.  Учетные данные [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] настраиваются с использованием параметра **VaultName**, **идентификатора клиента**и **ключа проверки подлинности**.  **Ключ проверки подлинности** действителен в течение определенного периода времени (1–2 года).   До истечения этого периода времени в Azure AD должен быть создан новый ключ для субъекта-службы.  Затем учетные данные необходимо изменить в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].    [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] поддерживает кэш учетных данных в текущем сеансе, поэтому при изменении учетных данных [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] следует перезапустить.  
  
### <a name="key-backup-and-recovery"></a>Резервное копирование и восстановление ключей  
Для хранилища ключей необходимо регулярно создавать резервную копию. В случае утери асимметричного ключа в хранилище его можно восстановить из резервной копии. Восстанавливать ключ следует с тем же именем, которое он имел раньше. Именно это и делает команда Restore PowerShell (см. шаги, описанные ниже).  
Если хранилище было утрачено, необходимо заново создать хранилище и восстановить асимметричный ключ к хранилищу, используя то же имя, какое было раньше. Имя хранилища может отличаться (можно сохранить прежнее). Кроме того, необходимо задать разрешения доступа для нового хранилища, чтобы предоставить субъекту-службе SQL Server доступ, необходимый для сценариев шифрования SQL Server, а затем настроить учетные данные SQL Server так, чтобы они отражали новое имя хранилища.  
В целом необходимо выполнить следующие действия.  
  
* Создать резервную копию ключа хранилища (с помощью командлета Powershell Backup-AzureKeyVaultKey).  
* В случае сбоя хранилища создать новое хранилище в той же географической области*. Пользователь, создающий это хранилище, должен быть в том же каталоге по умолчанию, который был настроен субъектом-службой для SQL Server.  
* Восстановить ключ к новому хранилищу с помощью командлета Powershell Restore-AzureKeyVaultKey. (Ключ будет восстановлен с использованием того же имени, какое было раньше.) Если ключ с таким именем уже существует, восстановление завершается со сбоем.  
* Предоставить разрешения субъекту-службе SQL Server на использование этого нового хранилища.  
* Изменить учетные данные SQL Server, используемые ядром СУБД, чтобы отразить новое имя хранилища (при необходимости).  
  
Резервные копии ключей можно восстанавливать в разных регионах Azure при условии, что они остаются в одной географической области или одном национальном облаке: в США, Канаде, Японии, Австралии, Индии, Азиатско-Тихоокеанском регионе, Европе, Бразилии, Китае, правительстве США или Германии.  
  
  
##  <a name="AppendixB"></a> Б. Часто задаваемые вопросы  
### <a name="on-azure-key-vault"></a>В хранилище ключей Azure  
  
**Как выполняются основные операции с хранилищем ключей Azure?**  
 Асимметричный ключ в хранилище ключей используется для защиты ключей шифрования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Только открытая часть асимметричного ключа покидает хранилище, закрытая же часть никогда не экспортируется. Все криптографические операции, использующие асимметричный ключ, выполняются в службе хранилища ключей Azure и защищаются ее системой безопасности.  
  
 **Что такое URI ключа?**  
 Каждый ключ в хранилище ключей Azure имеет универсальный код ресурса (URI), который можно использовать для ссылки на ключ из приложения. Используйте формат `https://ContosoKeyVault.vault.azure.net/keys/ContosoFirstKey` для получения текущей версии и формат `https://ContosoKeyVault.vault.azure.net/keys/ContosoFirstKey/cgacf4f763ar42ffb0a1gca546aygd87` для получения конкретной версии.  
  
### <a name="on-configuring-includessnoversionincludesssnoversion-mdmd"></a>При настройке [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  

**К каким конечным точкам нужен доступ соединителю SQL Server?** 
 Соединитель взаимодействует с двумя конечными точками, которые необходимо внести в список разрешений. Для исходящей связи с этими службами нужен только один порт: 443 (HTTPS).
-  login.microsoftonline.com/*:443
-  *.vault.azure.net/*:443
  
**Какие минимальные уровни разрешений необходимы для каждого этапа конфигурации в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]?**  
 Хотя все действия по настройке можно выполнить от имени члена предопределенной роли сервера sysadmin, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] рекомендует минимизировать используемые разрешения. В приведенном ниже списке указаны минимальные уровни разрешений для каждого действия.  
  
-   Для создания поставщика служб шифрования требуется разрешение `CONTROL SERVER` или членство в предопределенной роли сервера **sysadmin** .  
  
-   Для изменения параметра конфигурации и выполнения инструкции `RECONFIGURE` должно быть предоставлено разрешение `ALTER SETTINGS` на уровне сервера. Разрешение `ALTER SETTINGS` неявным образом предоставлено предопределенным ролям сервера sysadmin и **serveradmin** .  
  
-   Для создания учетных данных требуется разрешение `ALTER ANY CREDENTIAL` .  
  
-   Для добавления учетных данных к имени входа требуется разрешение `ALTER ANY LOGIN` .  
  
-   Для создания асимметричного ключа требуется разрешение `CREATE ASYMMETRIC KEY` .  

**Как изменить Active Directory по умолчанию, чтобы хранилище ключей было создано для той же подписки и того же Active Directory, что и субъект-служба, созданный для [!INCLUDE[ssNoVersion_md](../../../includes/ssnoversion-md.md)]соединителя?**

![aad-change-default-directory-helpsteps](../../../relational-databases/security/encryption/media/aad-change-default-directory-helpsteps.png)

1. Перейдите на классический портал Azure: [https://manage.windowsazure.com](https://manage.windowsazure.com)  
2. В меню слева выполните прокрутку вниз и выберите **Параметры**.
3. Выберите подписку Azure, которую используете в данный момент, и щелкните элемент **Изменить каталог** в области команд в нижней части экрана.
4. Во всплывающем окне воспользуйтесь раскрывающимся списком **Каталог** для выбора нужного Active Directory. При этом данный каталог становится используемым по умолчанию.
5. Убедитесь, что вы являетесь глобальным администратором для вновь выбранного Active Directory. Если вы не являетесь глобальным администраторов, то можете потерять разрешения на управление в результате смены каталогов.
6. Если после закрытия всплывающего окна вы не видите ни одной из своих подписок, возможно, требуется изменить элемент **Фильтровать по каталогу** фильтра **Подписки** , который расположен в правом верхнем меню, чтобы просмотреть подписки с использованием обновленного Active Directory.

    > [!NOTE] 
    > У вас могут отсутствовать разрешения на смену каталога по умолчанию в рамках своей подписки Azure. В этом случае создайте субъект-службу AAD в своем каталоге по умолчанию, чтобы он находился в одном каталоге с хранилищем ключей, которое планируется использовать.

Дополнительные сведения об Active Directory см. в разделе [How Azure subscription are related to Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-how-subscriptions-associated-directory/)(Как подписка Azure связана с Azure Active Directory).
  
##  <a name="AppendixC"></a> В. Описания кодов ошибок для Соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
 **Коды ошибок поставщика:**  
  
Код ошибки  |Символ  |Описание    
---------|---------|---------  
0 | scp_err_Success | Операция завершилась успешно.    
1 | scp_err_Failure | Операция завершилась ошибкой.    
2 | scp_err_InsufficientBuffer | Эта ошибка сообщает подсистеме, что нужно выделить больше памяти для буфера.    
3 | scp_err_NotSupported | Операция не поддерживается. Например, указанный алгоритм или тип ключа не поддерживается поставщиком расширенного управления ключами.    
4 | scp_err_NotFound | Поставщику расширенного управления ключами не удалось найти указанный ключ и алгоритм.    
5 | scp_err_AuthFailure | Сбой проверки подлинности с поставщиком расширенного управления ключами.    
6 | scp_err_InvalidArgument | Предоставлен недопустимый аргумент.    
7 | scp_err_ProviderError | В поставщике расширенного управления ключами произошла неопределенная ошибка, перехваченная ядром SQL.    
2049 | scp_err_KeyNameDoesNotFitThumbprint | Имя ключа слишком длинное и не умещается в отпечаток ядра SQL. Длина имени ключа не должна превышать 26 символов.    
2050 | scp_err_PasswordTooShort | Секретная строка, являющаяся объединением идентификатора клиента и секрета AAD, короче 32 символов.    
2051 | scp_err_OutOfMemory | В ядре SQL возникла нехватка памяти, и не удалось выделить память для поставщика расширенного управления ключами.    
2052 | scp_err_ConvertKeyNameToThumbprint | Не удалось преобразовать имя ключа в отпечаток.    
2053 | scp_err_ConvertThumbprintToKeyName|  Не удалось преобразовать отпечаток в имя ключа.    
3000 | ErrorSuccess | Операция с хранилищем ключей Azure завершилась успешно.    
3001 | ErrorUnknown | Сбой операции с хранилищем ключей Azure из-за неизвестной ошибки.    
3002 | ErrorHttpCreateHttpClientOutOfMemory | Не удается создать HttpClient для операции с хранилищем ключей Azure из-за нехватки памяти.    
3003 | ErrorHttpOpenSession | Не удается открыть сеанс HTTP из-за ошибки сети.    
3004 | ErrorHttpConnectSession | Не удается подключиться к сеансу HTTP из-за ошибки сети.    
3005 | ErrorHttpAttemptConnect | Не удается предпринять попытку подключения из-за ошибки сети.    
3006 | ErrorHttpOpenRequest | Не удается открыть запрос из-за ошибки сети.    
3007 | ErrorHttpAddRequestHeader | Не удается добавить заголовок запроса.    
3008 | ErrorHttpSendRequest | Не удается отправить запрос из-за ошибки сети.    
3009 | ErrorHttpGetResponseCode | Не удается получить запрос из-за ошибки сети.    
3010 | ErrorHttpResponseCodeUnauthorized | Сервер вернул ответ 401 на запрос.    
3011 | ErrorHttpResponseCodeThrottled | Сервер выполнил регулирование запроса.    
3012 | ErrorHttpResponseCodeClientError | С соединителя отправлен недопустимый запрос. Обычно это означает, что имя ключа является недопустимым или содержит недопустимые символы.
3013 | ErrorHttpResponseCodeServerError | Сервер возвратил код ответа от 500 до 600.    
3014 | ErrorHttpQueryHeader | Не удается запросить заголовок ответа.    
3015 | ErrorHttpQueryHeaderOutOfMemoryCopyHeader | Не удается скопировать заголовок ответа из-за нехватки памяти.    
3016 | ErrorHttpQueryHeaderOutOfMemoryReallocBuffer | Не удается запросить заголовок ответа из-за нехватки памяти при перераспределении буфера.    
3017 | ErrorHttpQueryHeaderNotFound | Не удается найти заголовок запроса в ответе.    
3018 | ErrorHttpQueryHeaderUpdateBufferLength | Не удается обновить длину буфера при запросе заголовка ответа.    
3019 | ErrorHttpReadData | Не удается считать данные ответа из-за ошибки сети. 
3076 | ErrorHttpResourceNotFound | Сервер вернут ответ 404, так как не удалось найти имя ключа. Убедитесь, что такое имя ключа присутствует в вашем хранилище.
3077 | ErrorHttpOperationForbidden | Сервер вернут ответ 403, так как у пользователя нет необходимых разрешений на выполнение данного действия. Убедитесь, что у вас есть разрешения для указанной операции. Для правильной работы соединителю требуются по меньшей мере разрешения get, list, wrapKey, unwrapKey.   
  
Если вы не видите код ошибки в этой таблице, ниже приведены некоторые другие причины для возникновения такой ошибки.   
  
-   Возможно, у вас отсутствует доступ в Интернет, из-за чего хранилище ключей Azure недоступно. Проверьте подключение к Интернету.  
  
-   Возможно, служба хранилища ключей Azure не работает. Повторите попытку позднее.  
  
-   Возможно, вы удалили асимметричный ключ из хранилища ключей Azure или [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Восстановите ключ.  
  
-   Если отображается сообщение об ошибке "Не удается загрузить библиотеку", убедитесь, что установлена подходящая с учетом используемой версии SQL Server версия распространяемого пакета Visual Studio C++. В следующей таблице указано, какую версию следует установить из центра загрузки Майкрософт.   
  
Версия SQL Server  |Ссылка для установки распространяемого пакета    
---------|--------- 
2008, 2008 R2, 2012, 2014 | [Распространяемые пакеты Visual C++ для Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40784)    
2016 | [Распространяемый пакет Visual C++ для Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48145)    
  
  
## <a name="additional-references"></a>Дополнительные ссылки  
 Подробнее о расширенном управлении ключами:  
  
-   [Расширенное управление ключами &#40;EKM&#41;](../../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
 Виды шифрования SQL с поддержкой расширенного управления ключами:  
  
-   [Enable TDE on SQL Server Using EKM (Включение прозрачного шифрования данных в SQL Server с помощью расширенного управления ключами)](../../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)  
  
-   [Шифрование резервной копии](../../../relational-databases/backup-restore/backup-encryption.md)  
  
-   [Создание зашифрованной резервной копии](../../../relational-databases/backup-restore/create-an-encrypted-backup.md)  
  
 Связанные команды [!INCLUDE[tsql](../../../includes/tsql-md.md)] :  
  
-   [sp_configure &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
-   [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../../t-sql/statements/create-cryptographic-provider-transact-sql.md)  
  
-   [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-credential-transact-sql.md)  
  
-   [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-asymmetric-key-transact-sql.md)  
  
-   [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-symmetric-key-transact-sql.md)  
  
-   [CREATE LOGIN &#40;Transact-SQL&#41;](../../../t-sql/statements/create-login-transact-sql.md)  
  
-   [ALTER LOGIN &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-login-transact-sql.md)  
  
 Документация по хранилищу ключей Azure.  
  
-   [Что такое хранилище ключей Azure?](https://azure.microsoft.com/documentation/articles/key-vault-whatis/)  
  
-   [Приступая к работе с хранилищем ключей Azure](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)  
  
-   Справочник по [командлетам PowerShell для работы с хранилищем ключей Azure](https://msdn.microsoft.com/library/dn868052.aspx)  
  
## <a name="see-also"></a>См. также:  
 [Extensible Key Management Using Azure Key Vault](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  [Use SQL Server Connector with SQL Encryption Features](../../../relational-databases/security/encryption/use-sql-server-connector-with-sql-encryption-features.md)   
 [Включенный параметр конфигурации сервера поставщика расширенного управления ключами](../../../database-engine/configure-windows/ekm-provider-enabled-server-configuration-option.md)   
 [Этапы настройки расширенного управления ключами с использованием хранилища ключей Azure](../../../relational-databases/security/encryption/setup-steps-for-extensible-key-management-using-the-azure-key-vault.md)  
  
  

