---
title: Выполнение пакета служб SSIS с помощью Transact-SQL (SSMS) | Документы Майкрософт
ms.date: 05/21/2018
ms.topic: quickstart
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: afb1f780509968536b12c60bc50c4d7e3f537c49
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65717396"
---
# <a name="run-an-ssis-package-from-ssms-with-transact-sql"></a>Выполнение пакета служб SSIS из SSMS с помощью Transact-SQL

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


В этом кратком руководстве показано, как использовать SQL Server Management Studio (SSMS) для подключения к базе данных каталога служб SSIS, а затем выполнить пакет SSIS в каталоге служб SSIS с помощью инструкций Transact-SQL.

SQL Server Management Studio — это интегрированная среда для управления любой инфраструктурой SQL, от SQL Server до базы данных SQL. Дополнительные сведения о SSMS см. в разделе [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>предварительные требования

Прежде чем начать, убедитесь в наличии последней версии SQL Server Management Studio (SSMS). Чтобы скачать среду SSMS, посетите страницу [Скачивание SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

Сервер базы данных SQL Azure прослушивает порт 1433. Если вы пытаетесь подключиться к серверу базы данных SQL Azure изнутри корпоративного брандмауэра, для успешного подключения в этом брандмауэре должен быть открыт данный порт.

## <a name="supported-platforms"></a>Поддерживаемые платформы

Сведения, приведенные в этом кратком руководстве, можно использовать для выполнения пакета SSIS на следующих платформах:

-   SQL Server в Windows.

-   База данных SQL Azure. Дополнительные сведения о развертывании и запуске пакетов в Azure см. в разделе [Перенос рабочих нагрузок SQL Server Integration Services в облако](lift-shift/ssis-azure-lift-shift-ssis-packages-overview.md).

Сведения, приведенные в этом кратком руководстве, не могут быть использованы для выполнения пакета SSIS в Linux. Дополнительные сведения о запуске пакетов на Linux см. в разделе [Извлечение, преобразование и загрузка данных в Linux с помощью служб SSIS](../linux/sql-server-linux-migrate-ssis.md).

## <a name="for-azure-sql-database-get-the-connection-info"></a>Получение сведений о подключении для базы данных SQL Azure

Для запуска пакета в базе данных SQL Azure вам нужны сведения, необходимые для подключения к базе данных каталога служб SSIS (SSISDB). В описанных ниже процедурах вам потребуется полное имя сервера и имя для входа.

1. Войдите на [портал Azure](https://portal.azure.com/).
2. Выберите **Базы данных SQL** в меню слева, а затем на странице **Базы данных SQL** — базу данных SSISDB. 
3. На странице **Обзор** для базы данных просмотрите полное имя сервера. Чтобы увидеть параметр **Щелкните, чтобы скопировать**, наведите указатель мыши на имя сервера. 
4. Если вы забыли учетные данные входа на сервер базы данных SQL Azure, перейдите на страницу этого сервера, чтобы узнать имя его администратора. При необходимости вы можете сбросить пароль.

## <a name="connect-to-the-ssisdb-database"></a>Подключение к базе данных SSISDB

С помощью SQL Server Management Studio установите соединение с каталогом служб SSIS на сервере базы данных SQL Azure. 

1. Откройте среду SQL Server Management Studio.

2. В диалоговом окне **Соединение с сервером** введите следующие данные:

   | Настройка       | Предлагаемое значение | Дополнительные сведения | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Тип сервера** | Ядро СУБД | Это значение обязательно. |
   | **Имя сервера** | Полное имя сервера | При подключении к серверу базы данных SQL Azure используйте следующий формат имени: `<server_name>.database.windows.net`. |
   | **Проверка подлинности** | Проверка подлинности SQL Server | Используйте проверку подлинности SQL Server для подключения к SQL Server или к базе данных SQL Azure. Если вы подключаетесь к серверу базы данных SQL Azure, вы не можете использовать проверку подлинности Windows. |
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
