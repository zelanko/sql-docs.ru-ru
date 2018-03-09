---
title: "Развертывание проекта служб SSIS с помощью Transact-SQL (SSMS) | Документы Майкрософт"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: quick-start
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fa245a3411b175e1bf9b8f95d473d2980eb0f47c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="deploy-an-ssis-project-from-ssms-with-transact-sql"></a>Развертывание проекта служб SSIS из SSMS с помощью Transact-SQL

В этом кратком руководстве показано, как использовать SQL Server Management Studio (SSMS) для подключения к базе данных каталога служб SSIS, а затем развернуть проект служб SSIS в каталоге служб SSIS с помощью инструкций Transact-SQL. 

> [!NOTE]
> Описываемый в этой статье метод недоступен при подключении к серверу базы данных SQL Azure с помощью SSMS. Хранимая процедура `catalog.deploy_project` ожидает, что путь к файлу `.ispac` находится в локальной файловой системе.

SQL Server Management Studio — это интегрированная среда для управления любой инфраструктурой SQL, от SQL Server до базы данных SQL. Дополнительные сведения о SSMS см. в разделе [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>предварительные требования

Прежде чем начать, убедитесь в наличии последней версии SQL Server Management Studio. Чтобы скачать среду SSMS, посетите страницу [Скачивание SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="connect-to-the-ssis-catalog-database"></a>Подключение к базе данных каталога SSIS

С помощью SQL Server Management Studio установите соединение с каталогом служб SSIS. 

> [!NOTE]
> Сервер базы данных SQL Azure прослушивает порт 1433. Если вы пытаетесь подключиться к серверу базы данных SQL Azure изнутри корпоративного брандмауэра, для успешного подключения в этом брандмауэре должен быть открыт данный порт.

1. Откройте среду SQL Server Management Studio.

2. В диалоговом окне **Соединение с сервером** введите следующие данные:

   | Настройка       | Предлагаемое значение | Дополнительные сведения | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Тип сервера** | Ядро СУБД | Это значение обязательно. |
   | **Имя сервера** | Полное имя сервера |  |
   | **Проверка подлинности** | Проверка подлинности SQL Server | В этом кратком руководстве используется проверка подлинности SQL. |
   | **Имя входа** | Учетная запись администратора сервера | Это учетная запись, которая была указана при создании сервера. |
   | **Пароль** | Пароль для учетной записи администратора сервера | Это пароль, который был указан при создании сервера. |

3. Нажмите кнопку **Соединить**. В SSMS открывается окно обозревателя объектов. 

4. В обозревателе объектов разверните узел **Каталоги служб Integration Services** и затем узел **SSISDB** для просмотра объектов в базе данных каталога служб SSIS.

## <a name="run-the-t-sql-code"></a>Выполнение кода T-SQL
Чтобы развернуть проект SSIS, выполните приведенный ниже код Transact-SQL.

1.  Откройте в SSMS новое окно запроса и вставьте приведенный ниже код.

2.  Обновите значения параметров в хранимой процедуре `catalog.deploy_project` так, чтобы они соответствовали вашей системе.

3.  Убедитесь, что SSISDB является текущей базой данных.

4.  Выполните скрипт.

5. В обозревателе объектов при необходимости обновите содержимое **SSISDB** и найдите развернутый проект.

```sql
DECLARE @ProjectBinary AS varbinary(max)
DECLARE @operation_id AS bigint
SET @ProjectBinary =
    (SELECT * FROM OPENROWSET(BULK '<project_file_path>.ispac', SINGLE_BLOB) AS BinaryData)

EXEC catalog.deploy_project @folder_name = '<target_folder>',
    @project_name = '<project_name',
    @Project_Stream = @ProjectBinary,
    @operation_id = @operation_id out
```

## <a name="next-steps"></a>Следующие шаги
- Рассмотрите другие варианты развертывания пакета.
    - [Развертывание пакета служб SSIS с помощью SSMS](./ssis-quickstart-deploy-ssms.md)
    - [Развертывание пакета служб SSIS с помощью Transact-SQL (Visual Studio Code)](ssis-quickstart-deploy-tsql-vscode.md)
    - [Развертывание пакета служб SSIS из командной строки](./ssis-quickstart-deploy-cmdline.md)
    - [Развертывание пакета служб SSIS с помощью PowerShell](ssis-quickstart-deploy-powershell.md)
    - [Развертывание пакета служб SSIS с помощью C#](./ssis-quickstart-deploy-dotnet.md) 
- Выполните развернутый пакет. Для выполнения пакета можно использовать различные средства и языки. Дополнительные сведения см. в следующих статьях:
    - [Выполнение пакета служб SSIS с помощью SSMS](./ssis-quickstart-run-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (Visual Studio Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Выполнение пакета служб SSIS из командной строки](./ssis-quickstart-run-cmdline.md)
    - [Выполнение пакета служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
    - [Выполнение пакета служб SSIS с помощью C#](./ssis-quickstart-run-dotnet.md) 
