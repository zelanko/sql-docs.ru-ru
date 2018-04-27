---
title: Выполнение пакета служб SSIS с помощью SSMS | Документы Майкрософт
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: quick-start
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 540eb0d40c571b4dde94d91814d89ceb18986337
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="run-an-ssis-package-with-sql-server-management-studio-ssms"></a>Выполнение пакета служб SSIS с помощью SQL Server Management Studio (SSMS)
В этом кратком руководстве показано, как использовать SQL Server Management Studio (SSMS) для подключения к базе данных каталога служб SSIS, а затем запустить пакет служб SSIS, хранящийся в каталоге SSIS, из обозревателя объектов в SSMS.

SQL Server Management Studio — это интегрированная среда для управления любой инфраструктурой SQL, от SQL Server до базы данных SQL. Дополнительные сведения о SSMS см. в разделе [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>предварительные требования

Прежде чем начать, убедитесь в наличии последней версии SQL Server Management Studio (SSMS). Чтобы скачать среду SSMS, посетите страницу [Скачивание SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="connect-to-the-ssisdb-database"></a>Подключение к базе данных SSISDB

С помощью SQL Server Management Studio установите соединение с каталогом служб SSIS. 

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

3. Нажмите кнопку **Соединить**. В SSMS открывается окно обозревателя объектов. 

4. В обозревателе объектов разверните узел **Каталоги служб Integration Services** и затем узел **SSISDB** для просмотра объектов в базе данных каталога служб SSIS.

## <a name="run-a-package"></a>Запуск пакета

1. Выберите пакет, который хотите запустить, в обозревателе объектов.

2. Щелкните правой кнопкой мыши и выберите команду **Выполнить**. Открывается диалоговое окно **Выполнение пакета**.

3.  Настройте выполнение пакета с помощью параметров на вкладках **Параметры**, **Диспетчеры соединений** и **Расширенные** диалогового окна "Выполнение пакета".

4.  Нажмите кнопку "ОК", чтобы выполнить пакет.

## <a name="next-steps"></a>Следующие шаги
- Рассмотрите другие варианты выполнения пакета.
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (Visual Studio Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Выполнение пакета служб SSIS из командной строки](./ssis-quickstart-run-cmdline.md)
    - [Выполнение пакета служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
    - [Выполнение пакета служб SSIS с помощью C#](./ssis-quickstart-run-dotnet.md) 
