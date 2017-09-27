---
title: "Подключиться к локальным источникам данных с проверкой подлинности Windows | Документы Microsoft"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: dbe6f832d4af55ddd15e12fba17a4da490fe19ae
ms.openlocfilehash: 25113093ccd068a9afe661e160ae3319025b7534
ms.contentlocale: ru-ru
ms.lasthandoff: 09/25/2017

---
# <a name="connect-to-on-premises-data-sources-with-windows-authentication"></a>Подключиться к локальным источникам данных с проверкой подлинности Windows
В этой статье описывается настройка каталога служб SSIS в базе данных SQL Azure для выполнения пакетов, использующих проверку подлинности Windows для подключения к локальным источникам данных.

Учетные данные домена, указываемые при выполнении действия в этой статье применяются к всех выполнявшихся пакетах на экземпляре базы данных SQL, пока не будет изменить или удалить учетные данные.

## <a name="prerequisite"></a>Предварительные требования
Перед тем как настроить учетные данные домена для проверки подлинности Windows, проверять ли не присоединенных к домену компьютер может подключаться к источникам данных в локальной среде в `runas` режиме. Например чтобы проверить ли подключаться к локальным SQL Server, выполните следующие действия:

1.  Для запуска этого теста fFind компьютера не присоединенных к домену.

2.  На компьютере, не присоединенных к домену выполните следующую команду, чтобы запустить SQL Server Management Studio (SSMS) с учетными данными домена, которые вы хотите использовать:

   ```cmd
   runas.exe /netonly /user:<domain>\<username> SSMS.exe
   ```

3.  В среде SSMS проверьте ли подключаться к локальным SQL Server, которую требуется использовать.

## <a name="provide-domain-credentials"></a>Укажите учетные данные домена
Чтобы предоставить учетные данные, позволяющие использовать проверку подлинности Windows для подключения к источникам данных в локальной среде пакеты, выполните следующие действия:

1.  SQL Server Management Studio (SSMS) или другое средство подключиться к базе данных SQL, на котором размещена база данных каталога служб SSIS (SSISDB). Дополнительные сведения см. в разделе [подключение к базе данных каталога SSISDB в Azure](ssis-azure-connect-to-catalog-database.md).

2.  Откройте окно запроса SSISDB в текущей базе данных.

3.  Выполните следующую хранимую процедуру и указать соответствующие учетные данные.

    ```sql
    catalog.set_execution_credential @user='<your user name>', @domain='<your domain name>', @password='<your password>'
    ```
4.  Запустите пакеты служб SSIS. Пакеты используют учетные данные, предоставленные для подключения к локальным источникам данных с проверкой подлинности Windows.

## <a name="view-domain-credentials"></a>Представление учетных данных домена
Чтобы просмотреть активные учетные данные, выполните следующие действия:

1.  SQL Server Management Studio (SSMS) или другое средство подключиться к базе данных SQL, на котором размещена база данных каталога служб SSIS (SSISDB).

2.  Откройте окно запроса SSISDB в текущей базе данных.

3.  Выполните следующую хранимую процедуру и проверьте выходные данные.

    ```sql
    SELECT * 
    FROM catalog.master_properties
    WHERE property_name = 'EXECUTION_DOMAIN' OR property_name = 'EXECUTION_USER'
    ```

## <a name="clear-domain-credentials"></a>Учетные данные домена, снимите флажок
Чтобы удалить учетные данные, которые вы указали, как описано в этой статье, выполните следующие действия:

1.  SQL Server Management Studio (SSMS) или другое средство подключиться к базе данных SQL, на котором размещена база данных каталога служб SSIS (SSISDB).

2.  Откройте окно запроса SSISDB в текущей базе данных.

3.  Выполните следующую хранимую процедуру:

    ```sql
    catalog.set_execution_credential @user='', @domain='', @password=''
    ```

## <a name="next-steps"></a>Следующие шаги
- Развертывание пакета. Дополнительные сведения см. в разделе [развернуть проект служб SSIS с SQL Server Management Studio (SSMS)](../ssis-quickstart-deploy-ssms.md).
- Запуск пакета. Дополнительные сведения см. в разделе [запуска пакета служб SSIS с SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md).
- Запланируйте запуск пакета. Дополнительные сведения см. в разделе [пакета служб SSIS расписание выполнения в Azure](ssis-azure-schedule-packages.md)

