---
title: Краткое руководство по проверке наличия R в SQL Server
description: Краткое руководство по проверке существования R и Службы машинного обучения в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 072a6f34a7cb91505d77356d6ec3835915c310d0
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715399"
---
# <a name="quickstart-verify-r-exists-in-sql-server"></a>Краткое руководство. Проверка наличия R в SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server включает поддержку языка R для аналитики обработки и анализа данных на резидентных SQL Server данных. Сценарий R может состоять из функций R с открытым исходным кодом, сторонних библиотек R или встроенных библиотек Microsoft R, таких как [RevoScaleR](../r/revoscaler-overview.md) для прогнозной аналитики в масштабе.

Выполнение скрипта осуществляется с помощью хранимых процедур с использованием любого из следующих подходов:

+ Встроенная хранимая процедура [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) , передающая R-скрипт в качестве входного параметра.
+ Заключите скрипт R в создаваемую [пользовательскую хранимую процедуру](sqldev-in-database-r-for-sql-developers.md) .

В этом кратком руководстве вы убедитесь, что установлены и настроены службы R [SQL Server службы машинного обучения](../what-is-sql-server-machine-learning.md) или [SQL Server 2016](../r/sql-server-r-services.md) .

## <a name="prerequisites"></a>предварительные требования

Для этого упражнения требуется доступ к экземпляру SQL Server с одним из следующих уже установленных:

+ [SQL Server службы машинного обучения](../install/sql-machine-learning-services-windows-install.md)с установленным языком R
+ [Службы SQL Server 2016 R](../install/sql-r-services-windows-install.md)

Ваш экземпляр SQL Server может находиться на виртуальной машине Azure или в локальной среде. Просто имейте в виду, что функция внешних скриптов по умолчанию отключена, поэтому может потребоваться [включить внешние сценарии](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) и убедиться, что **Служба панель запуска SQL Server** запущена перед началом работы.

Вам также понадобится средство для выполнения SQL-запросов. Скрипты R можно выполнять с помощью любого средства управления базами данных или запросов, если оно может подключаться к SQL Server экземпляру и выполнять запрос T-SQL или хранимую процедуру. В этом кратком руководстве используется [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="verify-r-exists"></a>Проверка наличия R

Вы можете убедиться, что Службы машинного обучения (с R) включено для экземпляра SQL Server и установленной версии R. Выполните следующие действия.

1. Откройте SQL Server Management Studio и подключитесь к экземпляру SQL Server.

2. Выполните приведенный ниже код. 

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'R',
    @script=N'print(version)';
    GO
    ```

3. Функция R `print` Возвращает версию в окно **сообщений** . В приведенном ниже примере выходных данных можно увидеть, что в SQL Server в этом случае установлена версия R 3.3.3.

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

Если вы получаете ошибки из этого запроса, устраните проблемы установки. Настройка после установки необходима для включения использования библиотек внешних кодов. См. раздел [install SQL Server службы машинного обучения](../install/sql-machine-learning-services-windows-install.md) или [Install SQL Server 2016 R Services](../install/sql-r-services-windows-install.md). Аналогичным образом убедитесь, что служба панели запуска запущена.

В зависимости от конкретной среды может потребоваться включить рабочие учетные записи R для подключения к SQL Server, установить дополнительные сетевые библиотеки, включить удаленное выполнение кода или перезапустить экземпляр после настройки всех компонентов. Дополнительные сведения см. в статье [вопросы и ответы по установке и обновлению служб R](../r/upgrade-and-installation-faq-sql-server-r-services.md).

## <a name="list-r-packages"></a>Список пакетов R

Корпорация Майкрософт предоставляет ряд пакетов R, предварительно устанавливаемых с Службы машинного обучения в экземпляре SQL Server. Чтобы просмотреть список установленных пакетов R, включая сведения о версии, зависимостях, лицензии и пути к библиотеке, выполните следующие действия.

1. Выполните приведенный ниже скрипт на экземпляре SQL Server.

    ```SQL
    EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'
    OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
    WITH result sets((Package NVARCHAR(255), Version NVARCHAR(100), Depends NVARCHAR(4000)
        , License NVARCHAR(1000), LibPath NVARCHAR(2000)));
    ```

2. Выходные данные изменяются `installed.packages()` в языке R и возвращаются в виде результирующего набора.

    **Результаты**

    ![Установленные пакеты в R](./media/rsql-installed-packages.png)

## <a name="next-steps"></a>Следующие шаги

Теперь, когда ваш экземпляр готов к работе с R, внимательно взгляните на основное взаимодействие с R.

> [!div class="nextstepaction"]
> [QuickStart Скрипт R "Hello World" в SQL Server](quickstart-r-run-using-tsql.md)
