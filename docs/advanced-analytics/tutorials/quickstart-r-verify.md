---
title: Краткое руководство по проверке R существует в SQL Server
description: Краткое руководство по проверке существование R и служб машинного обучения в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 0f461a00c1b9ecca1569b2b4f6257966c075491c
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/07/2019
ms.locfileid: "57579694"
---
# <a name="quickstart-verify-r-exists-in-sql-server"></a>Краткое руководство. Проверка наличия R в SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server включает в себя поддержка языка R для аналитики обработки и анализа данных в резидентных данных SQL Server. R-скриптов может состоять из функций R открытым исходным кодом, сторонние библиотеки R или встроенных библиотек Microsoft R, такие как [RevoScaleR](../r/revoscaler-overview.md) для прогнозной аналитики в нужном масштабе.

Выполнение скрипта является посредством хранимых процедур, используя один из следующих методов:

+ Встроенные [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) хранимую процедуру, передавая скрипт R в качестве входного параметра.
+ Wrap R-скриптов [пользовательская хранимая процедура](sqldev-in-database-r-for-sql-developers.md) , созданный.

В этом кратком руководстве вы проверите, [службы машинного обучения SQL Server 2017](../what-is-sql-server-machine-learning.md) или [SQL Server 2016 R Services](../r/sql-server-r-services.md) установлен и настроен.

## <a name="prerequisites"></a>предварительные требования

В этом упражнении требуется доступ к экземпляру SQL Server с помощью одного из уже установлены следующие компоненты:

+ [Службы машинного обучения SQL Server 2017](../install/sql-machine-learning-services-windows-install.md), с языком R
+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)

Экземпляр SQL Server может быть в виртуальной машине Azure или локально. Только Имейте в виду, что внешние средства написания сценариев отключен по умолчанию, поэтому может потребоваться [включить внешние сценарии](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) и убедитесь, что **службы панели запуска SQL Server** запущен перед запуском.

Вам также необходимо средство для выполнения запросов SQL. Можно выполнять скрипты R, используя любой базы данных управления или запроса средство, поскольку он может подключиться к экземпляру SQL Server и выполняется запрос T-SQL или хранимой процедуры. В этом кратком руководстве [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="verify-r-exists"></a>Убедитесь, что существует R

Чтобы убедиться, что служб машинного обучения (с помощью R) включен для экземпляра SQL Server и установленной версии R. Выполните следующие действия.

1. Откройте SQL Server Management Studio и подключитесь к экземпляру SQL Server.

2. Запустите приведенный ниже код. 

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'R',
    @script=N'print(version)';
    GO
    ```

3. R `print` функция возвращает версию для **сообщений** окна. В приведенном ниже примере, вы увидите SQL Server в этом случае у R версии 3.3.3 установлен.

    **Результаты**

    ```text
    platform       x86_64-w64-mingw32          
    arch           x86_64                      
    os             mingw32                     
    system         x86_64, mingw32             
    status                                     
    major          3                           
    minor          3.3                         
    year           2017                        
    month          03                          
    day            06                          
    svn rev        72310                       
    language       R                           
    version.string R version 3.3.3 (2017-03-06)
    nickname       Another Canoe               
    ```

Если вы получаете все ошибки из этого запроса, исключить любые проблемы установки. После установки настроек не требуется, чтобы включить использование библиотек внешнего кода. См. в разделе [установить SQL Server 2017 службы машинного обучения](../install/sql-machine-learning-services-windows-install.md) или [Установка служб R SQL Server 2016](../install/sql-r-services-windows-install.md). Аналогичным образом Убедитесь, что запущена служба панели запуска.

В зависимости от конкретной среды может потребоваться включить рабочие учетные записи R для подключения к SQL Server, установить дополнительные сетевые библиотеки, включить удаленное выполнение кода или перезапустить экземпляр после настройки всех компонентов. Дополнительные сведения см. в разделе [установки служб R и обновить часто задаваемые вопросы о](../r/upgrade-and-installation-faq-sql-server-r-services.md).

## <a name="list-r-packages"></a>Вывод списка R пакетов

Корпорация Майкрософт предоставляет ряд пакетов R, предварительно установленные с помощью служб машинного обучения в вашем экземпляре SQL Server. Для просмотра списка r, какие пакеты устанавливаются, включая версию, зависимости, лицензий и сведения о пути библиотеки, выполните следующие действия.

1. Запустите приведенный ниже сценарий в экземпляре SQL Server.

    ```SQL
    EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'
    OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
    WITH result sets((Package NVARCHAR(255), Version NVARCHAR(100), Depends NVARCHAR(4000)
        , License NVARCHAR(1000), LibPath NVARCHAR(2000)));
    ```

2. Выходные данные — из `installed.packages()` в R и возвращаемого в качестве результирующего набора.

    **Результаты**

    ![Установленные пакеты в R](./media/rsql-installed-packages.png)

## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы убедитесь, что экземпляр готов для работы с R, внимательно ознакомьтесь собой базовый взаимодействие R.

> [!div class="nextstepaction"]
> [Краткое руководство. R-сценарий «Hello world» в SQL Server](quickstart-r-run-using-tsql.md)
