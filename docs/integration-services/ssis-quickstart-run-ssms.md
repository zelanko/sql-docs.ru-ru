---
title: "Запустить пакет служб SSIS с помощью SSMS | Документы Microsoft"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 656e62f36446db4ef5b232129130a0253d2aebdf
ms.openlocfilehash: bbc17907311785ef98560493cb453b7b9b6d1556
ms.contentlocale: ru-ru
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-with-sql-server-management-studio-ssms"></a>Запустить пакет служб SSIS с SQL Server Management Studio (SSMS)
В этом кратком руководстве показано, как использовать SQL Server Management Studio (SSMS) для подключения к базе данных каталога служб SSIS, а затем запустите пакет служб SSIS, сохраненные в каталоге служб SSIS из обозревателя объектов в среде SSMS.

SQL Server Management Studio — это интегрированная среда для управления любой инфраструктуры SQL из SQL Server к базе данных SQL. Дополнительные сведения о SSMS см. в разделе [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>Предварительные требования

Прежде чем начать, убедитесь, что установлена последняя версия служб SQL Server Management Studio (SSMS). Скачать SSMS [загрузить SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="connect-to-the-ssisdb-database"></a>Подключения к базе данных SSISDB

Используйте SQL Server Management Studio для подключения в каталоге служб SSIS. 

> [!NOTE]
> Сервер базы данных SQL Azure прослушивает порт 1433. Если вы пытаетесь подключиться к серверу базы данных SQL Azure внутри корпоративного брандмауэра, этот порт должен быть открыт в корпоративный брандмауэр, для успешного подключения.

1. Откройте среду SQL Server Management Studio.

2. В **соединение с сервером** диалоговом окне введите следующие сведения:

   | Настройка       | Предлагаемое значение | Дополнительные сведения | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Тип сервера** | Компонент Database engine | Это значение обязательно. |
   | **Имя сервера** | Полное имя сервера | При подключении к серверу базы данных SQL Azure, называется в следующем формате: `<server_name>.database.windows.net`. |
   | **Проверка подлинности** | Проверка подлинности SQL Server | Это краткое руководство использует проверку подлинности SQL. |
   | **Имя входа** | Учетная запись администратора сервера | Это учетная запись, указанную при создании сервера. |
   | **Пароль** | Пароль для учетной записи администратора сервера | Это пароль, указанный при создании сервера. |

3. Нажмите кнопку **Соединить**. Открывается окно обозревателя объектов в среде SSMS. 

4. В обозревателе объектов разверните **каталоги служб Integration Services** и разверните **SSISDB** для просмотра объектов в базе данных каталога служб SSIS.

## <a name="run-a-package"></a>Запуск пакета

1. В обозревателе объектов выберите пакет, которую требуется запустить.

2. Щелкните правой кнопкой мыши и выберите **Execute**. **Выполнение пакета** откроется диалоговое окно.

3.  Настройте выполнение пакета с помощью параметров на **параметры**, **диспетчеры соединений**, и **Дополнительно** вкладок в диалоговом окне выполнения пакета.

4.  Нажмите кнопку ОК, чтобы запустить пакет.

## <a name="next-steps"></a>Следующие шаги
- Рассмотрите другие возможности для выполнения пакета.
    - [Запустить пакет служб SSIS с помощью Transact-SQL (среда SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Запустить пакет служб SSIS с помощью Transact-SQL (VS Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Выполните пакет служб SSIS из командной строки](./ssis-quickstart-run-cmdline.md)
    - [Выполнить пакет служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
    - [Запустить пакет служб SSIS с помощью C#](./ssis-quickstart-run-dotnet.md) 

