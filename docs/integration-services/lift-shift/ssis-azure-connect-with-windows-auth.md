---
title: "Подключение к локальным источникам данных и общим папкам Azure с помощью проверки подлинности Windows | Документы Майкрософт"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9235ffd3225e76ee94067519c72e997c451d9893
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="connect-to-on-premises-data-sources-and-azure-file-shares-with-windows-authentication"></a>Подключение к локальным источникам данных и общим папкам Azure с помощью проверки подлинности Windows
В этой статье описывается, как настроить каталог служб SQL Server Integration Services в базе данных SQL Azure для запуска пакетов, которые используют проверку подлинности Windows для подключения к локальным источникам данных и общим папкам Azure.

Учетные данные домена, указываемые при выполнении инструкций в этой статье, применяются ко всем операциям выполнения пакетов в экземпляре базы данных SQL, пока эти данные не будут изменены или удалены.

## <a name="connect-to-on-premises-data-sources"></a>Подключение к локальным источникам данных

### <a name="prerequisite"></a>Предварительные требования
Прежде чем создавать учетные данные домена для проверки подлинности Windows, проверьте, может ли не присоединенный к домену компьютер подключиться к локальному источнику данных в режиме `runas`.

#### <a name="connecting-to-sql-server"></a>Подключение к SQL Server
Чтобы проверить возможность подключения к локальному серверу SQL Server, выполните указанные ниже действия.

1.  Чтобы выполнить эту проверку, найдите компьютер, не присоединенный к домену.

2.  На не присоединенном к домену компьютере выполните следующую команду, чтобы запустить среду SQL Server Management Studio (SSMS) с требуемыми учетными данными домена:

    ```cmd
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
    ```

3.  В среде SSMS проверьте возможность подключения к требуемому локальному серверу SQL Server.

#### <a name="connecting-to-a-file-share"></a>Подключение к общей папке
Чтобы проверить возможность подключения к локальной общей папке, выполните указанные ниже действия.

1.  Чтобы выполнить эту проверку, найдите компьютер, не присоединенный к домену.

2.  На компьютере, не присоединенном к домену, выполните приведенную ниже команду. Эта команда открывает окно командной строки с требуемыми учетными данными домена, а затем проверяет возможность подключения к общей папке, получая список каталогов.

    ```cmd
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
    ```

3.  Проверьте, возвращен ли список каталогов из локальной общей папки, которую необходимо использовать.

### <a name="provide-domain-credentials"></a>Указание учетных данных домена
Чтобы задать учетные данные домена, с помощью которых пакеты смогут подключаться к локальным источникам данных, используя проверку подлинности Windows, выполните указанные ниже действия.

1.  С помощью SQL Server Management Studio (SSMS) или другого средства подключитесь к базе данных SQL, в которой размещается база данных каталога SSIS (SSISDB). Дополнительные сведения см. в разделе [Подключение к базе данных каталога SSISDB в Azure](ssis-azure-connect-to-catalog-database.md).

2.  Откройте окно запроса для текущей базы данных SSISDB.

3.  Выполните следующую хранимую процедуру и укажите соответствующие учетные данные домена:

    ```sql
    catalog.set_execution_credential @user='<your user name>', @domain='<your domain name>', @password='<your password>'
    ```
4.  Запустите пакеты служб SSIS. Пакеты используют предоставленные учетные данные для подключения к локальным источникам данных с помощью проверки подлинности Windows.

### <a name="view-domain-credentials"></a>Просмотр учетных данных домена
Чтобы просмотреть активные учетные данные домена, выполните указанные ниже действия.

1.  С помощью SQL Server Management Studio (SSMS) или другого средства подключитесь к базе данных SQL, в которой размещается база данных каталога SSIS (SSISDB).

2.  Откройте окно запроса для текущей базы данных SSISDB.

3.  Выполните следующую хранимую процедуру и просмотрите выходные данные:

    ```sql
    SELECT * 
    FROM catalog.master_properties
    WHERE property_name = 'EXECUTION_DOMAIN' OR property_name = 'EXECUTION_USER'
    ```

### <a name="clear-domain-credentials"></a>Удаление учетных данных домена
Чтобы удалить учетные данные, заданные согласно инструкциям в этой статье, выполните указанные ниже действия.

1.  С помощью SQL Server Management Studio (SSMS) или другого средства подключитесь к базе данных SQL, в которой размещается база данных каталога SSIS (SSISDB).

2.  Откройте окно запроса для текущей базы данных SSISDB.

3.  Выполните следующую хранимую процедуру:

    ```sql
    catalog.set_execution_credential @user='', @domain='', @password=''
    ```

## <a name="connect-to-file-shares"></a>Подключение к общим папкам
С помощью проверки подлинности Windows можно подключаться к общим папкам в той же виртуальной сети, в которой размещена среда Azure SSIS Integration Runtime. Папки могут находиться в локальной среде, в виртуальных машинах Azure и в службе файлов Azure. Дополнительные сведения о файлах Azure см. в разделе [Файлы Azure](https://azure.microsoft.com/services/storage/files/).

Чтобы подключиться к общей папке в виртуальной машине Azure или к общей папке Azure, выполните указанные ниже действия.

1.  С помощью SQL Server Management Studio (SSMS) или другого средства подключитесь к базе данных SQL, в которой размещается база данных каталога SSIS (SSISDB).

2.  Откройте окно запроса для текущей базы данных SSISDB.

3.  Выполните хранимую процедуру `catalog.set_execution_credential`, как описано ниже.

    а.  Чтобы подключиться к общей папке в виртуальной машине Azure, выполните следующую хранимую процедуру:

    ```sql
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
    ```

    б.  Чтобы подключиться к общей папке Azure (в службе файлов Azure), выполните следующую хранимую процедуру:

    ```sql
    catalog.set_execution_credential @domain = N'Azure', @user = N'<storage-account-name>', @password = N'<storage-account-key>'
    ```

## <a name="next-steps"></a>Следующие шаги
- Разверните пакет. Дополнительные сведения см. в разделе [Развертывание проекта служб SSIS с помощью SQL Server Management Studio (SSMS)](../ssis-quickstart-deploy-ssms.md).
- Запустите пакет. Дополнительные сведения см. в разделе [Выполнение пакета служб SSIS с помощью SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md).
- Создайте расписание для пакета. Дополнительные сведения см. в разделе [Планирование выполнения пакета служб SSIS в Azure](ssis-azure-schedule-packages.md).
