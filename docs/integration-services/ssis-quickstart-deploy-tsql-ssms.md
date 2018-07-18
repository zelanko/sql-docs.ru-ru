---
title: Развертывание проекта служб SSIS с помощью Transact-SQL (SSMS) | Документы Майкрософт
ms.date: 05/21/2018
ms.topic: quickstart
ms.prod: sql
ms.prod_service: integration-services
ms.suite: sql
ms.custom: ''
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4453198895cbc67d412019a9ff0f4e9463a496f6
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35402566"
---
# <a name="deploy-an-ssis-project-from-ssms-with-transact-sql"></a>Развертывание проекта служб SSIS из SSMS с помощью Transact-SQL

Это краткое руководство показывает, как подключиться к базе данных каталога служб SSIS с помощью SQL Server Management Studio (SSMS), а затем развернуть в этом каталоге проект служб SSIS в с помощью инструкций Transact-SQL. 

SQL Server Management Studio — это интегрированная среда для управления любой инфраструктурой SQL, от SQL Server до базы данных SQL. Дополнительные сведения о SSMS см. в разделе [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>предварительные требования

Прежде чем начать, убедитесь в наличии последней версии SQL Server Management Studio. Чтобы скачать среду SSMS, посетите страницу [Скачивание SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="supported-platforms"></a>Поддерживаемые платформы

Сведения, приведенные в этом кратком руководстве, можно использовать для развертывания проекта SSIS на следующих платформах:

-   SQL Server в Windows.

Сведения в этом кратком руководстве неприменимы для развертывания пакета SSIS в базе данных SQL Azure. Хранимая процедура `catalog.deploy_project` ожидает, что путь к файлу `.ispac` находится в локальной файловой системе. Дополнительные сведения о развертывании и запуске пакетов в Azure см. в разделе [Перенос рабочих нагрузок SQL Server Integration Services в облако](lift-shift/ssis-azure-lift-shift-ssis-packages-overview.md).

Сведения, приведенные в этом кратком руководстве, не могут быть использованы для развертывания пакета SSIS на SQL Server в Linux. Дополнительные сведения о запуске пакетов на Linux см. в разделе [Извлечение, преобразование и загрузка данных в Linux с помощью служб SSIS](../linux/sql-server-linux-migrate-ssis.md).

## <a name="connect-to-the-ssis-catalog-database"></a>Подключение к базе данных каталога SSIS

С помощью SQL Server Management Studio установите соединение с каталогом служб SSIS. 

1. Откройте среду SQL Server Management Studio.

2. В диалоговом окне **Соединение с сервером** введите следующие данные:

   | Настройка       | Предлагаемое значение | Дополнительные сведения | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Тип сервера** | Ядро СУБД | Это значение обязательно. |
   | **Имя сервера** | Полное имя сервера |  |
   | **Проверка подлинности** | Проверка подлинности SQL Server | |
   | **Имя входа** | Учетная запись администратора сервера | Это учетная запись, которая была указана при создании сервера. |
   | **Пароль** | Пароль для учетной записи администратора сервера | Это пароль, который был указан при создании сервера. |

3. Нажмите кнопку **Соединить**. В SSMS открывается окно обозревателя объектов. 

4. В обозревателе объектов разверните узел **Каталоги служб Integration Services** и затем узел **SSISDB** для просмотра объектов в базе данных каталога служб SSIS.

## <a name="run-the-t-sql-code"></a>Выполнение кода T-SQL
Чтобы развернуть проект SSIS, выполните приведенный ниже код Transact-SQL.

1.  Откройте в SSMS новое окно запроса и вставьте приведенный ниже код.

2.  Обновите значения параметров в хранимой процедуре `catalog.deploy_project` так, чтобы они соответствовали вашей системе.

3.  Убедитесь, что **SSISDB** является текущей базой данных.

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
