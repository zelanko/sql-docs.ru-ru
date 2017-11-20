---
title: "Развертывание проекта служб SSIS с помощью Transact-SQL (среда SSMS) | Документы Microsoft"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.suite: sql
ms.custom: 
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 656e62f36446db4ef5b232129130a0253d2aebdf
ms.openlocfilehash: e97fb20f5b0ee10aa3e5de690676b7e0bb797b4c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/22/2017

---
# <a name="deploy-an-ssis-project-from-ssms-with-transact-sql"></a>Развертывание проекта служб SSIS в среде SSMS с помощью Transact-SQL

В этом кратком руководстве показано, как использовать SQL Server Management Studio (SSMS) для подключения к базе данных каталога служб SSIS, а затем использовать инструкции Transact-SQL для развертывания проекта служб SSIS в каталоге служб SSIS. 

> [!NOTE]
> Метод, описанный в этой статье недоступен, при подключении к серверу базы данных SQL Azure с помощью SSMS. `catalog.deploy_project` Хранимая процедура ожидает, что путь к `.ispac` файл в локальной (локально) файловой системы.

SQL Server Management Studio — это интегрированная среда для управления любой инфраструктуры SQL из SQL Server к базе данных SQL. Дополнительные сведения о SSMS см. в разделе [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>Предварительные требования

Прежде чем начать, убедитесь, что установлена последняя версия среды SQL Server Management Studio. Скачать SSMS [загрузить SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="connect-to-the-ssis-catalog-database"></a>Подключения к базе данных каталога служб SSIS

Используйте SQL Server Management Studio для подключения в каталоге служб SSIS. 

> [!NOTE]
> Сервер базы данных SQL Azure прослушивает порт 1433. Если вы пытаетесь подключиться к серверу базы данных SQL Azure внутри корпоративного брандмауэра, этот порт должен быть открыт в корпоративный брандмауэр, для успешного подключения.

1. Откройте среду SQL Server Management Studio.

2. В **соединение с сервером** диалоговом окне введите следующие сведения:

   | Настройка       | Предлагаемое значение | Дополнительные сведения | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Тип сервера** | Компонент Database engine | Это значение обязательно. |
   | **Имя сервера** | Полное имя сервера |  |
   | **Проверка подлинности** | Проверка подлинности SQL Server | Это краткое руководство использует проверку подлинности SQL. |
   | **Имя входа** | Учетная запись администратора сервера | Это учетная запись, указанную при создании сервера. |
   | **Пароль** | Пароль для учетной записи администратора сервера | Это пароль, указанный при создании сервера. |

3. Нажмите кнопку **Соединить**. Открывается окно обозревателя объектов в среде SSMS. 

4. В обозревателе объектов разверните **каталоги служб Integration Services** и разверните **SSISDB** для просмотра объектов в базе данных каталога служб SSIS.

## <a name="run-the-t-sql-code"></a>Выполнение кода T-SQL
Выполните следующий код Transact-SQL для развертывания проекта служб SSIS.

1.  В среде SSMS откройте новое окно запроса и вставьте следующий код.

2.  Обновите значения параметров в `catalog.deploy_project` хранимой процедуры для вашей системы.

3.  Убедитесь, что SSISDB является текущей базы данных.

4.  Выполните скрипт.

5. В обозревателе объектов щелкните Обновить содержимое **SSISDB** при необходимости и установите флажок для проекта, который был развернут.

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
- Рассмотрите другие возможности для развертывания пакета.
    - [Развертывание пакета служб SSIS с помощью SSMS](./ssis-quickstart-deploy-ssms.md)
    - [Развертывание пакета служб SSIS с помощью Transact-SQL (VS Code)](ssis-quickstart-deploy-tsql-vscode.md)
    - [Развертывание пакета служб SSIS из командной строки](./ssis-quickstart-deploy-cmdline.md)
    - [Развертывание пакета служб SSIS с помощью PowerShell](ssis-quickstart-deploy-powershell.md)
    - [Развертывание пакета служб SSIS с помощью C#](./ssis-quickstart-deploy-dotnet.md) 
- Выполнения развернутого пакета. Чтобы запустить пакет, можно выбрать несколько средств и языков. Дополнительные сведения см. в следующих статьях:
    - [Запустить пакет служб SSIS с помощью SSMS](./ssis-quickstart-run-ssms.md)
    - [Запустить пакет служб SSIS с помощью Transact-SQL (среда SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Запустить пакет служб SSIS с помощью Transact-SQL (VS Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Выполните пакет служб SSIS из командной строки](./ssis-quickstart-run-cmdline.md)
    - [Выполнить пакет служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
    - [Запустить пакет служб SSIS с помощью C#](./ssis-quickstart-run-dotnet.md) 

