---
title: Краткое руководство для выполнения кода «Hello, World!» основные R в T-SQL (машинного обучения SQL Server) | Документация Майкрософт
description: В этом кратком руководстве для скрипта R в SQL Server ознакомиться с основами системной хранимой процедуры sp_execute_external_script с упражнения hello world.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e738289b39f6d390bc4d6196606d242fa4803865
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086887"
---
# <a name="quickstart-hello-world-r-script-in-sql-server"></a>Краткое руководство: «Hello world» R-скриптов SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server включает в себя поддержка функций языка R для анализа в базе данных в резидентных данных SQL Server. Функции R открытым исходным кодом, сторонних пакетов и встроенные пакеты Microsoft R можно использовать для прогнозной аналитики в нужном масштабе.

В этом кратком руководстве вы узнаете основные понятия, выполнив «Hello World» R скрипт inT-SQL, представив Введение **sp_execute_external_script** системной хранимой процедуры. Выполнение скрипта R — посредством хранимых процедур. Вы можете использовать [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) хранимую процедуру и передайте R сценария в качестве входного параметра, как показано в этом кратком руководстве, или перенос R-скриптов [пользовательская хранимая процедура](sqldev-in-database-r-for-sql-developers.md). 

## <a name="prerequisites"></a>предварительные требования

В этом упражнении требуется доступ к экземпляру SQL Server с помощью одного из уже установлены следующие компоненты:

+ [Службы машинного обучения SQL Server 2017](../install/sql-machine-learning-services-windows-install.md), с языком R
+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)

  Экземпляр SQL Server может быть в виртуальной машине Azure или локально. Только Имейте в виду, что внешние средства написания сценариев отключен по умолчанию, поэтому может потребоваться [включить внешние сценарии](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) и убедитесь, что **службы панели запуска SQL Server** запущен перед запуском.

+ Средство для выполнения запросов SQL. Можно использовать любое приложение, которое может подключаться к базе данных SQL Server и выполнять код T-SQL. Специалистов по SQL можно использовать Visual Studio или SQL Server Management Studio (SSMS).

Для этого учебника, чтобы показать, насколько это просто для запуска R внутри SQL Server, мы использовали новый **расширение mssql для Visual Studio Code**. Visual STUDIO Code — это бесплатная среда разработки, можно запустить на Linux, macOS или Windows. **Mssql** расширения — это упрощенный расширение для запуска запросов T-SQL. Чтобы скачать и установить Visual Studio Code, перейдите на [эту страницу](https://code.visualstudio.com/Download). Чтобы добавить **mssql** расширения, см. в статье: [с помощью расширения mssql для Visual Studio Code](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-vscode).

## <a name="connect-to-a-database-and-run-a-hello-world-test-script"></a>Подключение к базе данных и выполнение тестового скрипта Hello World

1. В Visual Studio Code создайте текстовый файл с именем BasicRSQL.sql.

2. В файле нажмите клавиши CTR+SHIFT+P (в операционной системе macOS нажмите COMMAND+P), введите **sql**, чтобы вывести список команд SQL, и выберите **Подключиться**. Visual Studio Code предложит создать профиль для использования при подключении к конкретной базе данных. Это необязательно, но также облегчает переключение между базами данных и именами входа.
    + Выберите сервер или экземпляр, где установлено R в SQL Server.
    + Используйте учетную запись, имеющую разрешения на создание базы данных, выполнение инструкций SELECT и просмотр определений таблиц.

2. Если подключение успешно установлено, в строке состояния должны отобразиться имена сервера и базы данных, а также текущие учетные данные. В случае сбоя подключения убедитесь, что имена компьютера и сервера заданы правильно.

3. Вставьте и выполните следующую инструкцию:

    ```sql
    EXEC sp_execute_external_script
      @language =N'R',
      @script=N'OutputDataSet<-InputDataSet',
      @input_data_1 =N'SELECT 1 AS hello'
      WITH RESULT SETS (([Hello World] int));
    GO
    ```

Входные данные для этой хранимой процедуры включают:

+ *@language* Определяет расширение языка для вызова, в этом случае R.
+ *@script* параметр определяет команды, передаваемые в среду выполнения R. Весь скрипт R должен быть заключен в этом аргументе в виде текста в Юникоде. Также можно добавить текст в переменную типа **nvarchar**, а затем вызвать ее.
+ *@input_data_1* данные, возвращенные запросом, переданный в среду выполнения R, которая возвращает данные в SQL Server в качестве кадра данных.
+ С РЕЗУЛЬТИРУЮЩИМИ НАБОРАМИ предложение определяет схему таблицы возвращаемых данных для SQL Server, добавив «Hello, World!» в качестве имени столбца, **int** для типа данных.

**Результаты**

![rsql_basictut_hello1](media/rsql-basictut-hello1.PNG)

Если вы получаете все ошибки из этого запроса, исключить любые проблемы установки. После установки настроек не требуется, чтобы включить использование библиотек внешнего кода. См. в разделе [установить SQL Server 2017 службы машинного обучения](../install/sql-machine-learning-services-windows-install.md) или [Установка служб R SQL Server 2016](../install/sql-r-services-windows-install.md). Аналогичным образом Убедитесь, что запущена служба панели запуска. 

В зависимости от конкретной среды может потребоваться включить рабочие учетные записи R для подключения к SQL Server, установить дополнительные сетевые библиотеки, включить удаленное выполнение кода или перезапустить экземпляр после настройки всех компонентов. Дополнительные сведения см. в разделе [установки служб R и часто задаваемые вопросы обновления](../r/upgrade-and-installation-faq-sql-server-r-services.md)

> [!TIP]
> В Visual Studio Code выделите код, который необходимо выполнить, и нажмите клавиши CTRL+SHIFT+E. Если эту комбинацию трудно запомнить, вы можете ее изменить. Сведения см. в статье [Customize Keyboard Shortcuts](https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts) (Настройка сочетаний клавиш).
> 
> ![rsql basictut_hello1code](media/rsql-basictut-hello1code.PNG)
> 

## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы убедитесь, что экземпляр готов для работы с R, внимательно ознакомьтесь структурирование входные и выходные данные.

> [!div class="nextstepaction"]
> [Краткое руководство: Обработка входных и выходных данных](rtsql-working-with-inputs-and-outputs.md)
