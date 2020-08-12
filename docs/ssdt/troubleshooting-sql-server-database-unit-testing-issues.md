---
title: Устранение неполадок модульных тестов базы данных SQL Server
description: Ознакомьтесь с советами по устранению неполадок, которые могут возникнуть в работе модульных тестов SQL Server, таких как сбои времени ожидания и развертывание базы данных на непредвиденные целевые объекты.
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: cf4c9cd1-7e73-4c3b-922a-68b9247e7b33
author: markingmyname
ms.author: maghan
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: cc9f8c0c87922a54df0bcd3d2ee4fa730ecfaff7
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85883415"
---
# <a name="troubleshooting-sql-server-database-unit-testing-issues"></a>Устранение неполадок модульных тестов базы данных SQL Server

При работе с тестированиями модулей SQL Server для базы данных у вас могут возникнуть проблемы, описанные в этом разделе:  
  
-   [Изменения тестирования модулей и файла App.Config не учитываются при выполнении тестирований модулей](#UnitTestingAndAppConfigChanges)  
  
-   [При выполнении тестирований модулей база данных развертывается в непредвиденном расположении](#DatabaseDeploymentInUnitTests)  
  
-   [Истечение времени ожидания при выполнении тестов единиц базы данных](#TimeoutsDuringUnitTests)  
  
## <a name="unit-testing-and-appconfig-changes-ignored-when-you-run-unit-tests"></a><a name="UnitTestingAndAppConfigChanges"></a>Изменения тестирования модулей и файла App.Config не учитываются при выполнении тестирований модулей  
Если в тестовом проекте в файл App.Config вносятся изменения, для вступления этих изменений в силу проект необходимо построить повторно. Сюда также входят изменения, которые вносятся в файл App.Config с помощью диалогового окна **Конфигурация теста SQL Server**. Если не выполнить повторное построение проекта тестов, изменения не будут приведены при запуске модульных тестов.  
  
## <a name="database-deployment-to-unexpected-target-when-you-run-unit-tests"></a><a name="DatabaseDeploymentInUnitTests"></a>При выполнении тестирований модулей база данных развертывается в непредвиденном расположении  
При развертывании базы данных из проекта базы данных, когда выполняются модульные тесты, база данных развертывается с помощью данных строки подключения, заданной в конфигурации тестирования модулей. Данные подключения, указанные в свойствах "Отладка" проекта базы данных, для этой задачи не используются, что позволяет выполнять тестирования модулей SQL Server разных экземпляров одной и той же базы данных.  
  
## <a name="timeouts-when-you-run-database-unit-tests"></a><a name="TimeoutsDuringUnitTests"></a>Истечение времени ожидания при выполнении тестов единиц базы данных  
Если выполнить тесты единиц базы данных не удается из-за истечения времени ожидания, можно увеличить период времени ожидания, внеся изменение в файл app.config тестового проекта. Время ожидания подключения, заданное в строке подключения, указывает, сколько можно ждать, когда тестирование модулей устанавливает соединение с сервером. Время ожидания команды, которое должно задаваться непосредственно в файле app.config, указывает, сколько можно ждать в то время, когда тестирование модулей выполняет скрипт Transact\-SQL. Если вы испытываете проблемы с тестированиями модулей, на выполнение которых требуется длительное время, попробуйте увеличить значение времени ожидания команды в контексте соответствующего элемента. Например, чтобы задать время ожидания команды в 120 секунд для элемента **PrivilegedContext**, внесите в файл app.config следующие изменения:  
  
```  
<SqlUnitTesting_VS2010>  
    <DatabaseDeployment DatabaseProjectFileName="..\..\..\..\..\..\Visual Studio 2010\Projects\Database10\Database10\AdventureWorks.sqlproj"  
        Configuration="Debug" />  
    <DataGeneration ClearDatabase="true" />  
    <ExecutionContext Provider="System.Data.SqlClient" ConnectionString="Data Source=(LocalDB)\Projects;Initial Catalog=AdventureWorks_Test;Integrated Security=True;Pooling=False"  
        CommandTimeout="30" />  
    <PrivilegedContext Provider="System.Data.SqlClient" ConnectionString="Data Source=(LocalDB)\Projects;Initial Catalog=AdventureWorks_Test;Integrated Security=True;Pooling=False"  
        CommandTimeout="120" />  
</SqlUnitTesting_VS2010>  
```  
  
## <a name="see-also"></a>См. также:  
[Руководство. создавать модульные тесты SQL Server для функций, триггеров и хранимых процедур](../ssdt/how-to-create-unit-tests-for-functions-triggers-stored-procedures.md)  
[Руководство. Настройка запуска модульного теста SQL Server](../ssdt/how-to-configure-sql-server-unit-test-execution.md)  
  
