---
title: Выполнение пакета служб SSIS с помощью Transact-SQL (SSMS) | Документы Майкрософт
ms.date: 09/25/2017
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.component: quick-start
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 33dd58a47f445b46c3d373090b8e3a887f9959cc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="run-an-ssis-package-from-ssms-with-transact-sql"></a>Выполнение пакета служб SSIS из SSMS с помощью Transact-SQL
В этом кратком руководстве показано, как использовать SQL Server Management Studio (SSMS) для подключения к базе данных каталога служб SSIS, а затем с помощью инструкций Transact-SQL запустить пакет служб SSIS, хранящийся в каталоге SSIS.

SQL Server Management Studio — это интегрированная среда для управления любой инфраструктурой SQL, от SQL Server до базы данных SQL. Дополнительные сведения о SSMS см. в разделе [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>предварительные требования

Прежде чем начать, убедитесь в наличии последней версии SQL Server Management Studio (SSMS). Чтобы скачать среду SSMS, посетите страницу [Скачивание SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="connect-to-the-ssisdb-database"></a>Подключение к базе данных SSISDB

С помощью SQL Server Management Studio установите соединение с каталогом служб SSIS на сервере базы данных SQL Azure. 

> [!NOTE]
> Сервер базы данных SQL Azure прослушивает порт 1433. Если вы пытаетесь подключиться к серверу базы данных SQL Azure изнутри корпоративного брандмауэра, для успешного подключения в этом брандмауэре должен быть открыт данный порт.

1. Откройте среду SQL Server Management Studio.

2. В диалоговом окне **Соединение с сервером** введите следующие данные:

   | Настройка       | Предлагаемое значение | Дополнительные сведения | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Тип сервера** | Ядро СУБД | Это значение обязательно. |
   | **Имя сервера** | Полное имя сервера | При подключении к серверу базы данных SQL Azure используйте следующий формат имени: `<server_name>.database.windows.net`. |
   | **Проверка подлинности** | Проверка подлинности SQL Server | В этом кратком руководстве используется проверка подлинности SQL. |
   | **Имя входа** | Учетная запись администратора сервера | Это учетная запись, которая была указана при создании сервера. |
   | **Пароль** | Пароль для учетной записи администратора сервера | Это пароль, который был указан при создании сервера. |

3.  Нажмите кнопку **Соединить**. В SSMS открывается окно обозревателя объектов.

4. В обозревателе объектов разверните узел **Каталоги служб Integration Services** и затем узел **SSISDB** для просмотра объектов в базе данных каталога служб SSIS.

## <a name="run-a-package"></a>Запуск пакета
Чтобы запустить пакет SSIS, выполните приведенный ниже код Transact-SQL.

1.  Откройте в SSMS новое окно запроса и вставьте приведенный ниже код. (Этот код создается параметром **Скрипт** в диалоговом окне **Выполнение пакета** в SQL Server Management Studio.)

2.  Обновите значения параметров в хранимой процедуре `catalog.create_execution` так, чтобы они соответствовали вашей системе.

3.  Убедитесь, что SSISDB является текущей базой данных.

4.  Выполните скрипт.

5. В обозревателе объектов при необходимости обновите содержимое **SSISDB** и найдите развернутый проект.

```sql
Declare @execution_id bigint
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx',
    @execution_id=@execution_id OUTPUT,
    @folder_name=N'Deployed Projects',
      @project_name=N'Integration Services Project1',
    @use32bitruntime=False,
      @reference_id=Null
Select @execution_id
DECLARE @var0 smallint = 1
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,
    @object_type=50,
      @parameter_name=N'LOGGING_LEVEL',
      @parameter_value=@var0
EXEC [SSISDB].[catalog].[start_execution] @execution_id
GO
```

## <a name="next-steps"></a>Следующие шаги
- Рассмотрите другие варианты выполнения пакета.
    - [Выполнение пакета служб SSIS с помощью SSMS](./ssis-quickstart-run-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (Visual Studio Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Выполнение пакета служб SSIS из командной строки](./ssis-quickstart-run-cmdline.md)
    - [Выполнение пакета служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
    - [Выполнение пакета служб SSIS с помощью C#](./ssis-quickstart-run-dotnet.md) 
