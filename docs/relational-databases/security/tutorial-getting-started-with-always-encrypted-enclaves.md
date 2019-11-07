---
title: Руководство. Начало работы с Always Encrypted с безопасными анклавами с использованием SSMS | Документация Майкрософт
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: d5912e7cca2ceeba1fe0db95743b4d29e1154a86
ms.sourcegitcommit: 312b961cfe3a540d8f304962909cd93d0a9c330b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73592344"
---
# <a name="tutorial-getting-started-with-always-encrypted-with-secure-enclaves-using-ssms"></a>Руководство. Начало работы с Always Encrypted с безопасными анклавами с использованием SSMS
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

В этом руководстве показывается, как приступить к работе с [Always Encrypted с безопасными анклавами](encryption/always-encrypted-enclaves.md). Буду рассмотрены следующие темы.
- Создание простой среды для тестирования и оценки Always Encrypted с безопасными анклавами.
- Шифрование данных на месте и выдача полнофункциональных запросов к зашифрованным столбцам с помощью SQL Server Management Studio (SSMS).

## <a name="prerequisites"></a>предварительные требования

Чтобы начать работу с Always Encrypted с безопасными анклавами, потребуется по крайней мере два компьютера (это могут быть виртуальные машины):

- компьютер SQL Server для размещения SQL Server и SSMS;
- компьютер HGS для запуска службы защиты узла, необходимой для аттестации анклава.

### <a name="sql-server-computer-requirements"></a>Требования к компьютеру с SQL Server

- [!INCLUDE [sssqlv15-md](../../includes/sssqlv15-md.md)] или более поздняя версия.
- Windows 10 Корпоративная (версия 1809) или более поздние версии или выпуск Windows Server 2019 Datacenter. Другие выпуски Windows 10 и Windows Server не поддерживают аттестацию с помощью HGS.
- Поддержка ЦП для технологий виртуализации:
  - Intel VT-x с Extended Page Tables.
  - AMD-V с Rapid Virtualization Indexing.
  - Если [!INCLUDE [ssnoversion-md](../../includes/ssnoversion-md.md)] работает на виртуальной машине, низкоуровневая оболочка и физический ЦП должны предоставлять возможности вложенной виртуализации. 
    - В Hyper-V 2016 или более поздней версии [включите расширения вложенной виртуализации на процессоре виртуальной машины](https://docs.microsoft.com/virtualization/hyper-v-on-windows/user-guide/nested-virtualization#configure-nested-virtualization).
    - В Azure выберите размер виртуальной машины, поддерживающий вложенную виртуализацию. Это все виртуальные машины серии v3, например Dv3 и Ev3. См. раздел [Create a nesting capable Azure VM](https://docs.microsoft.com/azure/virtual-machines/windows/nested-virtualization#create-a-nesting-capable-azure-vm) (Создание виртуальной машины Azure с поддержкой вложения).
    - В VMWare vSphere 6.7 или более поздней версии включите для виртуальной машины поддержку технологии Virtualization Based Security (VBS), как описано в [документации VMware](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-C2E78F3E-9DE2-44DB-9B0A-11440800AADD.html).
    - Другие низкоуровневые оболочки и общедоступные облака могут поддерживать возможности вложенной виртуализации, позволяющие использовать Always Encrypted с анклавами VBS. Просмотрите сведения о совместимости и инструкции по настройке в документации по своему решению для виртуализации.
- [SQL Server Management Studio (SSMS) версии не ниже 18.3](../../ssms/download-sql-server-management-studio-ssms.md).

Кроме того, можно установить SSMS на другом компьютере.

> [!WARNING]
> В рабочей среде никогда не используйте SSMS или другие средства для управления ключами Always Encrypted или выполнения запросов зашифрованных данных на компьютере SQL Server, так как это может частично или полностью лишить смысла использование Always Encrypted. Подробнее см. в разделе [Вопросы безопасности для управления ключами](encryption/overview-of-key-management-for-always-encrypted.md#security-considerations-for-key-management).

### <a name="hgs-computer-requirements"></a>Требования к компьютеру с HGS

- Windows Server 2019, выпуск Standard или Datacenter
- 2 процессора
- 8 ГБ ОЗУ
- Хранилище 100 ГБ

> [!NOTE]
> Компьютер HGS не должен быть присоединен к домену перед началом работы.

## <a name="step-1-configure-the-hgs-computer"></a>Шаг 1. Настройка компьютера HGS

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

> [!NOTE]
> Если же вы хотите ссылаться на этот компьютер HGS по DNS-имени, можно настроить сервер пересылки из корпоративных DNS-серверов на новый контроллер домена HGS.  

## <a name="step-2-configure-the-sql-server-computer-as-a-guarded-host"></a>Шаг 2. Настройка компьютера SQL Server как защищенного узла
На этом шаге выполняется настройка компьютера SQL Server как защищенного узла, зарегистрированного в HGS с помощью аттестации ключа узла.

> [!WARNING]
> Рекомендуется использовать аттестацию ключа узла только в тестовых средах. Для рабочих сред следует использовать аттестацию доверенного платформенного модуля (TPM).

1. Войдите на компьютер SQL Server с правами администратора, откройте консоль Windows PowerShell с повышенными привилегиями и найдите имя компьютера, указанное в переменной computername.

   ```powershell
   $env:computername 
   ```

2. Установите компонент Guarded Host (Защищенный узел). При этом будет также установлена технология Hyper-V (если она еще не установлена).

   ```powershell
   Enable-WindowsOptionalFeature -Online -FeatureName HostGuardian -All
   ```

3. При появлении запроса на завершение установки Hyper-V перезагрузите компьютер SQL Server.

4. Если SQL Server работает в виртуальной машине или на устаревшем физическом компьютере, который не поддерживает UEFI Secure Boot или не имеет блока IOMMU, вам потребуется удалить требование VBS для функций безопасности платформы.
    1. Удалите требование в реестре Windows.

        ```powershell
       Set-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Control\DeviceGuard -Name RequirePlatformSecurityFeatures -Value 0
       ```

    1. Перезагрузите компьютер снова, чтобы технология VBS работала со сниженными требованиями.

        ```powershell
       Restart-Computer
       ```

5. Снова войдите на компьютер SQL Server с правами администратора, откройте консоль Windows PowerShell с повышенными привилегиями, создайте уникальный ключ узла и экспортируйте полученный открытый ключ в файл.

   ```powershell
   Set-HgsClientHostKey 
   Get-HgsClientHostKey -Path $HOME\Desktop\hostkey.cer
   ```

6. Скопируйте вручную файл ключа узла, созданный на предыдущем шаге, на компьютер HGS. В следующих инструкциях подразумевается, что файл называется hostkey.cer и он скопирован на рабочий стол компьютера HGS.

7. На компьютере HGS откройте консоль Windows PowerShell с повышенными привилегиями и зарегистрируйте ключ узла вашего компьютера SQL Server с помощью HGS:

   ```powershell
   Add-HgsAttestationHostKey -Name <your SQL Server computer name> -Path $HOME\Desktop\hostkey.cer
   ```

8. На компьютере SQL Server в консоли Windows PowerShell с повышенными привилегиями выполните следующую команду, чтобы сообщить компьютеру SQL Server, где должна выполняться аттестация. Обязательно укажите IP-адрес или DNS-имя своего компьютера HGS в качестве обоих значений адреса. 

   ```powershell
   # use http, and not https
   Set-HgsClientConfiguration -AttestationServerUrl http://<IP address or DNS name>/Attestation -KeyProtectionServerUrl http://<IP address or DNS name>/KeyProtection/  
   ```

Результат приведенной выше команды должен показывать, что аттестация пройдена (AttestationStatus = Passed).

Если возникла ошибка HostUnreachable, это означает, что компьютер SQL Server не может обмениваться данными с HGS. Проверьте связь с компьютером HGS с помощью команды ping.

Ошибка UnauthorizedHost указывает, что открытый ключ не был зарегистрирован на сервере HGS. Повторите шаги 5 и 6, чтобы устранить эту ошибку.

Если все эти действия не помогают, запустите командлет Remove-HgsClientHostKey и повторите шаги 4–7.

## <a name="step-3-enable-always-encrypted-with-secure-enclaves-in-sql-server"></a>Шаг 3. Настройка Always Encrypted с безопасными анклавами в SQL Server

На этом шаге выполняется включение функции Always Encrypted с использованием анклавов в экземпляре SQL Server.

1. От имени системного администратора с помощью SSMS подключитесь к экземпляру SQL Server **без** включенной функции Always Encrypted для подключения к базе данных.
    1. Запустите SSMS.
    1. В диалоговом окне **Соединение с сервером** укажите имя сервера, выберите метод аутентификации и введите учетные данные.
    1. Нажмите кнопку **Параметры >>** и выберите вкладку **Always Encrypted**.
    1. Убедитесь, что флажок **Включить Always Encrypted (шифрование столбцов)** **не** установлен.
    1. Выберите **Подключиться**.

2. Откройте новое окно запроса и выполните инструкции ниже, чтобы задать для типа безопасного анклава значение "Безопасность на базе виртуализации (VBS)".

   ```sql
   EXEC sys.sp_configure 'column encryption enclave type', 1;
   RECONFIGURE;
   ```

3. Перезапустите экземпляр SQL Server, чтобы предыдущее изменение вступило в силу. Можно перезапустить этот экземпляр в SSMS, щелкнув его правой кнопкой мыши в обозревателе объектов и выбрав "Перезапуск". После перезагрузки экземпляра снова подключитесь к нему.

4. Убедитесь, что безопасный анклав загружен, выполнив следующий запрос:

   ```sql
   SELECT [name], [value], [value_in_use] FROM sys.configurations
   WHERE [name] = 'column encryption enclave type';
   ```

    По результатам запроса должен возвращаться следующий результат:  

    | name                           | value | value_in_use |
    | ------------------------------ | ----- | -------------- |
    | column encryption enclave type (тип анклава для шифрования столбцов) | 1     | 1              |

5. Чтобы активировать полнофункциональные вычисления в зашифрованных столбцах, выполните следующий запрос:

   ```sql
   DBCC traceon(127,-1);
   ```

    > [!NOTE]
    > Полнофункциональные вычисления в [!INCLUDE [sssqlv15-md](../../includes/sssqlv15-md.md)] по умолчанию отключены. Их необходимо включить с помощью вышеуказанной инструкции после каждой перезагрузки экземпляра SQL Server.

## <a name="step-4-create-a-sample-database"></a>Шаг 4. Создание образца базы данных
На этом шаге создается база данных с демонстрационными данными, которые далее будут шифроваться.

1. С помощью экземпляра SSMS из предыдущего шага выполните приведенную ниже инструкцию в окне запроса, чтобы создать новую базу данных с именем **ContosoHR**.

    ```sql
    CREATE DATABASE [ContosoHR];
    ```

1. Создайте новую таблицу с именем **Employees**.

    ```sql
    USE [ContosoHR];
    GO

    CREATE TABLE [dbo].[Employees]
    (
        [EmployeeID] [int] IDENTITY(1,1) NOT NULL,
        [SSN] [char](11) NOT NULL,
        [FirstName] [nvarchar](50) NOT NULL,
        [LastName] [nvarchar](50) NOT NULL,
        [Salary] [money] NOT NULL
    ) ON [PRIMARY];
    ```

1. Добавьте несколько записей о сотрудниках в таблицу **Employees**.

    ```sql
    USE [ContosoHR];
    GO

    INSERT INTO [dbo].[Employees]
            ([SSN]
            ,[FirstName]
            ,[LastName]
            ,[Salary])
        VALUES
            ('795-73-9838'
            , N'Catherine'
            , N'Abel'
            , $31692);

    INSERT INTO [dbo].[Employees]
            ([SSN]
            ,[FirstName]
            ,[LastName]
            ,[Salary])
        VALUES
            ('990-00-6818'
            , N'Kim'
            , N'Abercrombie'
            , $55415);
    ```

## <a name="step-5-provision-enclave-enabled-keys"></a>Шаг 5. Подготовка ключей с поддержкой анклава

На этом шаге будут создаваться главный ключ столбца и ключ шифрования столбца, который разрешает вычисления анклава.

1. С помощью экземпляра SSMS из предыдущего шага в **обозревателе объектов** разверните базу данных и перейдите к пункту **Безопасность** > **Ключи Always Encrypted**.
1. Подготовьте новый главный ключ столбца с поддержкой анклава:
    1. Щелкните правой кнопкой мыши **Ключи Always Encrypted** и выберите **Создать главный ключ столбца...** .
    2. Выберите имя главного ключа столбца: **CMK1**.
    3. Убедитесь, что выбрано значение **Хранилище сертификатов Windows (текущий пользователь или локальный компьютер)** или **Azure Key Vault**.
    4. Выберите **Разрешить вычисления анклава**.
    5. Если вы выбрали Azure Key Vault, войдите в Azure и выберите хранилище ключей. Дополнительные сведения о создании хранилища ключей для Always Encrypted см. в статье [Управление хранилищами ключей на портале Azure](https://blogs.technet.microsoft.com/kv/2016/09/12/manage-your-key-vaults-from-new-azure-portal/).
    6. Выберите сертификат или ключ Azure Key Vault, если он существует, или нажмите кнопку **Создать сертификат**, чтобы создать новый сертификат.
    7. Нажмите кнопку **ОК**.

        ![Разрешение вычислений анклава](encryption/media/always-encrypted-enclaves/allow-enclave-computations.png)

1. Создайте новый ключ шифрования столбцов с поддержкой анклава:

    1. Щелкните правой кнопкой мыши **Ключи Always Encrypted** и выберите **Создать ключ шифрования столбца**.
    2. Введите имя для нового ключа шифрования столбцов: **CEK1**.
    3. В раскрывающемся списке **Главный ключ столбца** выберите ключ, созданный на предыдущих шагах.
    4. Нажмите кнопку **ОК**.

## <a name="step-6-encrypt-some-columns-in-place"></a>Шаг 6. Шифрование некоторых столбцов на месте

На этом шаге вы выполните шифрование данных, хранящихся в столбцах **SSN** и **Salary** в анклаве на стороне сервера, а затем протестируете запрос SELECT к данным.

1. Откройте новый экземпляр SSMS и подключитесь к экземпляру SQL Server **с** включенной функцией Always Encrypted для подключения к базе данных.
    1. Создайте новый экземпляр SSMS.
    1. В диалоговом окне **Соединение с сервером** укажите имя сервера, выберите метод аутентификации и введите учетные данные.
    1. Нажмите кнопку **Параметры >>** и выберите вкладку **Always Encrypted**.
    1. Установите флажок **Включить Always Encrypted (шифрование столбцов)** и укажите URL-адрес аттестации анклава (например, ht<span>tp://</span>hgs.bastion.local/Attestation).
    1. Выберите **Подключиться**.
    1. Если отобразится запрос на включение параметризации для запросов Always Encrypted, нажмите кнопку **Включить**.

1. Используя тот же экземпляр SSMS (с включенной функцией Always Encrypted), откройте новое окно запроса и выполните шифрование столбцов **SSN** и **Salary** с помощью приведенных ниже запросов.

    ```sql
    USE [ContosoHR];
    GO

    ALTER TABLE [dbo].[Employees]
    ALTER COLUMN [SSN] [char] (11) COLLATE Latin1_General_BIN2
    ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
    WITH
    (ONLINE = ON);

    ALTER TABLE [dbo].[Employees]
    ALTER COLUMN [Salary] [money]
    ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
    WITH
    (ONLINE = ON);

    ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
    ```

    > [!NOTE]
    > Обратите внимание на инструкцию ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE для очистки кэша планов запросов в базе данных в приведенном выше скрипте. Изменив таблицу, необходимо очистить планы всех пакетов и хранимых процедур, которые обращаются к таблице, чтобы обновить сведения о параметрах шифрования. 

1. Чтобы убедиться в том, что столбцы **SSN** и **Salary** зашифрованы, откройте новое окно запроса в экземпляре SSMS **без** включенной функции Always Encrypted для подключения к базе данных и выполните приведенную ниже инструкцию. Окно запроса должно возвратить зашифрованные значения столбцов **SSN** и **Salary**. Если вы выполните тот же запрос с помощью экземпляра SSMS с включенной функцией Always Encrypted, данные будут расшифрованы.

    ```sql
    SELECT * FROM [dbo].[Employees];
    ```

## <a name="step-7-run-rich-queries-against-encrypted-columns"></a>Шаг 7. Выполнение полнофункциональных запросов к зашифрованным столбцам

Теперь можно выполнять полнофункциональные запросы к зашифрованным столбцам. Некоторая обработка запросов будет выполняться в анклаве на стороне сервера. 

1. В экземпляре SSMS **с** включенной функцией Always Encrypted убедитесь, что включена параметризация для Always Encrypted.
    1. Выберите пункт **Инструменты** в главном меню SSMS.
    2. Выберите **Параметры**.
    3. Выберите **Выполнение запроса** > **SQL Server** > **Дополнительно**.
    4. Убедитесь, что установлен флажок **Включить параметризацию для Always Encrypted**.
    5. Нажмите кнопку **ОК**.
2. Откройте новое окно запроса, а затем вставьте и выполните приведенный ниже запрос. Запрос должен возвратить соответствующие заданным условиям поиска значения и строки в виде открытого текста.

    ```sql
    DECLARE @SSNPattern [char](11) = '%6818';
    DECLARE @MinSalary [money] = $1000;
    SELECT * FROM [dbo].[Employees]
    WHERE SSN LIKE @SSNPattern AND [Salary] >= @MinSalary;
    ```

3. Попробуйте выполнить тот же запрос еще раз в экземпляре SSMS с отключенной функцией Always Encrypted и запишите код возникшей ошибки.

## <a name="next-steps"></a>Next Steps
После завершения работы с этим учебником вы можете обратиться к одному из следующих учебников:
- [Учебник. Разработка приложения .NET Framework с помощью Always Encrypted с безопасными анклавами](tutorial-always-encrypted-enclaves-develop-net-framework-apps.md)
- [Учебник. Создание и использование индексов в столбцах с поддержкой анклава с помощью случайного шифрования](./tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md)

## <a name="see-also"></a>См. также:
- [Настройка типа анклава для параметра конфигурации сервера Always Encrypted](../../database-engine/configure-windows/configure-column-encryption-enclave-type.md)
- [Подготовка ключей с поддержкой анклава](encryption/always-encrypted-enclaves-provision-keys.md)
- [Настройка шифрования столбцов на месте с помощью Transact-SQL](encryption/always-encrypted-enclaves-configure-encryption-tsql.md)
- [Выполнение запросов к столбцам с помощью Always Encrypted с безопасными анклавами](encryption/always-encrypted-enclaves-query-columns.md)