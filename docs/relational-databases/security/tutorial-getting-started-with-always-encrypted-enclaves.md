---
title: Учебник. Начало работы с Always Encrypted с безопасными анклавами с использованием SSMS | Документация Майкрософт
ms.custom: ''
ms.date: 10/04/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: jaszymas
ms.author: jaszymas
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: a4d833d132a0b4928d021beaa4cd9fcdd695d6c6
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046584"
---
# <a name="tutorial-getting-started-with-always-encrypted-with-secure-enclaves-using-ssms"></a>Учебник. Начало работы с Always Encrypted с безопасными анклавами с использованием SSMS
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этом руководстве показывается, как приступить к работе с [Always Encrypted с безопасными анклавами](encryption/always-encrypted-enclaves.md). Буду рассмотрены следующие темы.
- Создание простой среды для тестирования и оценки Always Encrypted с безопасными анклавами.
- Шифрование данных на месте и выдача полнофункциональных запросов к зашифрованным столбцам с помощью SQL Server Management Studio (SSMS).

## <a name="prerequisites"></a>предварительные требования

Чтобы начать работу с Always Encrypted с безопасными анклавами, потребуется по крайней мере два компьютера (это могут быть виртуальные машины):

- компьютер SQL Server для размещения SQL Server и SSMS;
- компьютер HGS для запуска службы защиты узла, необходимой для аттестации анклава.

### <a name="sql-server-computer-requirements"></a>Требования к компьютеру SQL Server

- [!INCLUDE [sssqlv15-md](../../includes/sssqlv15-md.md)] или более поздней версии
- Windows 10 Корпоративная версии 1809 или Windows Server 2019 DataCenter
- [SQL Server Management Studio (SSMS) версии не ниже 18.0](../../ssms/download-sql-server-management-studio-ssms.md)

Кроме того, можно установить SSMS на другом компьютере.

>[!WARNING] 
>В рабочей среде никогда не используйте SSMS или другие средства для управления ключами Always Encrypted или выполнения запросов зашифрованных данных на компьютере SQL Server, так как это может частично или полностью лишить смысла использование Always Encrypted.

### <a name="hgs-computer-requirements"></a>Требования к компьютеру HGS

- Windows Server 2019, выпуск Standard или Datacenter
- 2 процессора
- 8 ГБ ОЗУ
- Хранилище 100 ГБ

>[!NOTE]
>Компьютер HGS не должен быть присоединен к домену перед началом работы.

## <a name="step-1-configure-the-hgs-computer"></a>Шаг 1. Настройка компьютера HGS

На этом шаге выполняется настройка компьютера HGS для запуска службы защиты узла, поддерживающей аттестацию ключа узла.

1. Войдите на компьютер HGS с правами локального администратора, откройте консоль Windows PowerShell с повышенными привилегиями и добавьте роль службы защиты узла, выполнив следующую команду:

   ```powershell
   Install-WindowsFeature -Name HostGuardianServiceRole -IncludeManagementTools -Restart
   ```

2. После перезагрузки компьютера HGS снова войдите с учетной записью администратора, откройте консоль Windows PowerShell с повышенными привилегиями и выполните следующие команды для установки службы защиты узла и настройки ее домена. Заданный здесь пароль будет относиться только к режиму восстановления служб каталогов для Active Directory; он не изменит пароль для входа учетной записи администратора. Для параметра -HgsDomainName можно выбрать любое доменное имя.

   ```powershell
   $adminPassword = ConvertTo-SecureString -AsPlainText '<password>' -Force
   Install-HgsServer -HgsDomainName 'bastion.local' -SafeModeAdministratorPassword $adminPassword -Restart
   ```

3. После очередной перезагрузки компьютера войдите с учетной записью администратора (который теперь также является администратором домена), откройте консоль Windows PowerShell с повышенными привилегиями и настройте аттестацию ключа узла для вашего экземпляра HGS. 

   ```powershell
   Initialize-HgsAttestation -HgsServiceName 'hgs' -TrustHostKey  
   ```

4. Найдите IP-адрес компьютера HGS, выполнив следующую команду. Сохраните этот IP-адрес для выполнения дальнейших действий.

   ```powershell
   Get-NetIPAddress  
   ```

>[!NOTE]
>Если же вы хотите ссылаться на этот компьютер HGS по DNS-имени, можно настроить сервер пересылки из корпоративных DNS-серверов на новый контроллер домена HGS.  

## <a name="step-2-configure-the-sql-server-computer-as-a-guarded-host"></a>Этап 2. Настройка компьютера SQL Server как защищенного узла
На этом шаге выполняется настройка компьютера SQL Server как защищенного узла, зарегистрированного в HGS с помощью аттестации ключа узла.
>[!NOTE]
>Рекомендуется использовать аттестацию ключа узла только в тестовых средах. Для рабочих сред следует использовать аттестацию доверенного платформенного модуля (TPM).

1. Войдите на компьютер SQL Server с правами администратора, откройте консоль Windows PowerShell с повышенными привилегиями и установите компонент Guarded Host (Защищенный узел); при этом будет также установлена технология Hyper-V (если она еще не установлена).

   ```powershell
   Enable-WindowsOptionalFeature -Online -FeatureName HostGuardian -All
   ```

2. При появлении запроса на завершение установки Hyper-V перезагрузите компьютер SQL Server.
3. Получите значение ниже переменной, показанной ниже, чтобы определить имя компьютера SQL Server.

   ```powershell
   $env:computername 
   ```

4. Снова войдите на компьютер SQL Server с правами администратора, откройте консоль Windows PowerShell с повышенными привилегиями, создайте уникальный ключ узла и экспортируйте полученный открытый ключ в файл.

   ```powershell
   Set-HgsClientHostKey 
   Get-HgsClientHostKey -Path $HOME\Desktop\hostkey.cer
   ```

5. Скопируйте файл ключа узла, созданный на предыдущем шаге, на компьютер HGS. В следующих инструкциях подразумевается, что файл называется hostkey.cer и он скопирован на рабочий стол компьютера HGS.
6. На компьютере HGS откройте консоль Windows PowerShell с повышенными привилегиями и зарегистрируйте ключ узла вашего компьютера SQL Server с помощью HGS:

   ```powershell
   Add-HgsAttestationHostKey -Name <your SQL Server computer name> -Path $HOME\Desktop\hostkey.cer
   ```

7. На компьютере SQL Server в консоли Windows PowerShell с повышенными привилегиями выполните следующую команду, чтобы сообщить компьютеру SQL Server, где должна выполняться аттестация. Убедитесь, что указали IP-адрес или DNS-имя своего компьютера HGS. 

   ```powershell
   # use http, and not https
   Set-HgsClientConfiguration -AttestationServerUrl http://<IP address or DNS name>/Attestation -KeyProtectionServerUrl http://<IP address or DNS name>/KeyProtection/  
   ```

Результат приведенной выше команды должен показывать, что аттестация пройдена (AttestationStatus = Passed).

Если возникла ошибка HostUnreachable, это означает, что компьютер SQL Server не может обмениваться данными с HGS. Проверьте связь с компьютером HGS с помощью команды ping.

Ошибка UnauthorizedHost указывает, что открытый ключ не был зарегистрирован на сервере HGS. Повторите шаги 5 и 6, чтобы устранить эту ошибку.

Если все эти действия не помогают, запустите командлет Clear-HgsClientHostKey и повторите шаги 4–7.

## <a name="step-3-enable-always-encrypted-with-secure-enclaves-in-sql-server"></a>Шаг 3. Настройка Always Encrypted с безопасными анклавами в SQL Server

На этом шаге выполняется включение функции Always Encrypted с использованием анклавов в экземпляре SQL Server.

1. Откройте SSMS, подключитесь к экземпляру SQL Server как системный администратор и откройте окно создания запроса.
2. Настройте безопасный тип анклава для анклавов VBS.

   ```sql
   EXEC sys.sp_configure 'column encryption enclave type', 1
   RECONFIGURE
   ```

3. Перезапустите экземпляр SQL Server, чтобы предыдущее изменение вступило в силу. Можно перезапустить этот экземпляр в SSMS, щелкнув его правой кнопкой мыши в обозревателе объектов и выбрав "Перезапуск". После перезагрузки экземпляра снова подключитесь к нему.

4. Убедитесь, что безопасный анклав загружен, выполнив следующий запрос:

   ```sql
   SELECT [name], [value], [value_in_use] FROM sys.configurations
   WHERE [name] = 'column encryption enclave type'
   ```

    Запрос должен вернуть строку, которая выглядит следующим образом:  

    | name                           | value | value_in_use |
    | ------------------------------ | ----- | -------------- |
    | column encryption enclave type (тип анклава для шифрования столбцов) | 1     | 1              |

5. Чтобы активировать полнофункциональные вычисления в зашифрованных столбцах, выполните следующий запрос:

   ```sql
   DBCC traceon(127,-1)
   ```

    > [!NOTE]
    > Полнофункциональные вычисления в [!INCLUDE [sssqlv15-md](../../includes/sssqlv15-md.md)] по умолчанию отключены. Их необходимо включить с помощью вышеуказанной инструкции после каждой перезагрузки экземпляра SQL Server.

## <a name="step-4-create-a-sample-database"></a>Шаг 4. Создание образца базы данных
На этом шаге создается база данных с демонстрационными данными, которые далее будут шифроваться.

1. Подключитесь к экземпляру SQL Server с помощью SSMS.
2. Создайте новую базу данных с именем ContosoHR.

    ```sql
    CREATE DATABASE [ContosoHR] COLLATE Latin1_General_BIN2
    ```

3. Убедитесь, что подключение к только что созданной базе данных установлено. Создайте новую таблицу с именем Employees.

    ```sql
    CREATE TABLE [dbo].[Employees]
    (
        [EmployeeID] [int] IDENTITY(1,1) NOT NULL,
        [SSN] [char](11) NOT NULL,
        [FirstName] [nvarchar](50) NOT NULL,
        [LastName] [nvarchar](50) NOT NULL,
        [Salary] [money] NOT NULL
    ) ON [PRIMARY]
    GO
    ```

4. Добавьте несколько записей о сотрудниках в таблицу Employees.

    ```sql
    INSERT INTO [dbo].[Employees]
            ([SSN]
            ,[FirstName]
            ,[LastName]
            ,[Salary])
        VALUES
            ('795-73-9838'
            , N'Catherine'
            , N'Abel'
            , $31692)
    GO

    INSERT INTO [dbo].[Employees]
            ([SSN]
            ,[FirstName]
            ,[LastName]
            ,[Salary])
        VALUES
            ('990-00-6818'
            , N'Kim'
            , N'Abercrombie'
            , $55415)
    GO
    ```

## <a name="step-5-provision-enclave-enabled-keys"></a>Шаг 5. Подготовка ключей с поддержкой анклава

На этом шаге будут создаваться главный ключ столбца и ключ шифрования столбца, который разрешает вычисления анклава.

1. Подключитесь к базе данных с помощью SSMS.
2. В **обозревателе объектов** разверните базу данных и перейдите к пункту **Безопасность** > **Ключи Always Encrypted**.
3. Подготовьте новый главный ключ столбца с поддержкой анклава:
    1. Щелкните правой кнопкой мыши **Ключи Always Encrypted** и выберите **Создать главный ключ столбца...**.
    2. Выберите имя главного ключа столбца: CMK1.
    3. Убедитесь, что выбрано значение **Хранилище сертификатов Windows (текущий пользователь или локальный компьютер)** или **Azure Key Vault**.
    4. Выберите **Разрешить вычисления анклава**.
    5. Если вы выбрали Azure Key Vault, войдите в Azure и выберите хранилище ключей. Дополнительные сведения о создании хранилища ключей для Always Encrypted см. в статье [Управление хранилищами ключей на портале Azure](https://blogs.technet.microsoft.com/kv/2016/09/12/manage-your-key-vaults-from-new-azure-portal/).
    6. Выберите свой ключ, если он уже существует, или создайте новый ключ, следуя указаниям в форме.
    7. Нажмите кнопку **ОК**.

        ![Разрешение вычислений анклава](encryption/media/always-encrypted-enclaves/allow-enclave-computations.png)

4. Создайте новый ключ шифрования столбцов с поддержкой анклава:

    1. Щелкните правой кнопкой мыши **Ключи Always Encrypted** и выберите **Создать ключ шифрования столбца**.
    2. Введите имя для нового ключа шифрования столбцов: CEK1.
    3. В раскрывающемся списке **Главный ключ столбца** выберите ключ, созданный на предыдущих шагах.
    4. Нажмите кнопку **ОК**.

## <a name="step-6-encrypt-some-columns-in-place"></a>Шаг 6. Шифрование некоторых столбцов на месте

На этом шаге будут шифроваться данные, хранящиеся в столбцах SSN и Salary в анклаве на стороне сервера, а затем будет протестирован запрос SELECT данных.

1. В SSMS настройте окно создания запроса с включенным Always Encrypted для подключения к базе данных.
    1. В SSMS откройте окно создания запроса.
    2. Щелкните правой кнопкой мыши в любом месте окна создания запроса.
    3. Выберите "Подключение" \> "Изменить подключение".
    4. Выберите **Параметры**. Перейдите на вкладку **Always Encrypted**, выберите **Включить Always Encrypted** и укажите URL-адрес аттестации анклава.
    5. Выберите **Подключиться**.
2. В SSMS настройте другое окно создания запроса с выключенным Always Encrypted для подключения к базе данных.
    1. В SSMS откройте окно создания запроса.
    2. Щелкните правой кнопкой мыши в любом месте окна создания запроса.
    3. Выберите "Подключение" \> "Изменить подключение".
    4. Выберите **Параметры**. Перейдите на вкладку **Always Encrypted** и убедитесь, что флажок **Включить Always Encrypted** не установлен.
    5. Выберите **Подключиться**.
3. Зашифруйте столбцы SSN и Salary. Вставьте в окно запроса с включенным Always Encrypted следующие инструкции и выполните их.

    ```sql
    ALTER TABLE [dbo].[Employees]
    ALTER COLUMN [SSN] [char] (11)
    ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
    WITH
    (ONLINE = ON)
    GO
    DBCC FREEPROCCACHE
    GO

    ALTER TABLE [dbo].[Employees]
    ALTER COLUMN [Salary] [money]
    ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
    WITH
    (ONLINE = ON)
    GO
    DBCC FREEPROCCACHE
    GO
    ```

4. Чтобы проверить, зашифрованы ли теперь столбцы SSN и Salary, вставьте в окно запроса с выключенным Always Encrypted следующую инструкцию и выполните ее. Окно запроса должно возвратить зашифрованные значения столбцов SSN и Salary. В окне запроса с включенным Always Encrypted выполните тот же запрос, чтобы просмотреть расшифрованные данные.

    ```sql
    SELECT * FROM [dbo].[Employees]
    ```

## <a name="step-7-run-rich-queries-against-encrypted-columns"></a>Шаг 7. Выполнение полнофункциональных запросов к зашифрованным столбцам

Теперь можно выполнять полнофункциональные запросы к зашифрованным столбцам. Некоторая обработка запросов будет выполняться в анклаве на стороне сервера. 

1. Включите параметризацию для Always Encrypted.
    1. В главном меню SSMS выберите **Запрос**.
    2. Щелкните **Параметры запроса...**.
    3. Выберите **Выполнение** > **Дополнительно**.
    4. Установите или снимите флажок "Enable Parameterization for Always Encrypted" (Включить параметризацию для Always Encrypted).
    5. Нажмите кнопку "ОК".
2. Вставьте в окно запроса с включенным Always Encrypted следующий запрос и выполните его. Запрос должен возвратить соответствующие заданным условиям поиска значения и строки в виде открытого текста.

    ```sql
    DECLARE @SSNPattern [char](11) = '%6818'
    DECLARE @MinSalary [money] = $1000
    SELECT * FROM [dbo].[Employees]
    WHERE SSN LIKE @SSNPattern AND [Salary] >= @MinSalary;
    ```

## <a name="next-steps"></a>Next Steps
Другие варианты использования см. в разделе [Настройка Always Encrypted с безопасными анклавами](encryption/configure-always-encrypted-enclaves.md). Также можно попытаться выполнить следующее.

- [Настройка аттестации доверенного платформенного модуля (TPM).](https://docs.microsoft.com/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-tpm-mode)
- [Настройка HTTPS для экземпляра HGS.](https://docs.microsoft.com/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-configure-hgs-https)
- Разработка приложений, отправляющих полнофункциональные запросы к зашифрованным столбцам.
