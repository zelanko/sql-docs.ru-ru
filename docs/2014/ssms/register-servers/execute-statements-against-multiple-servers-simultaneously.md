---
title: Выполнение инструкций на нескольких серверах одновременно (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- multiserver queries
- executing queries against multiple servers
- queries [SQL Server], multiserver
ms.assetid: 197760f3-0a06-43de-8162-69c27d3fbe56
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3cd2224785df8d5dfa171cd1cfc3390d680c07f2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152844"
---
# <a name="execute-statements-against-multiple-servers-simultaneously-sql-server-management-studio"></a>Execute Statements Against Multiple Servers Simultaneously (SQL Server Management Studio)
  В этом разделе описывается, как в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]выполнить запросы к нескольким серверам одновременно путем создания локальной группы серверов либо создать сервер централизованного управления и одну или несколько групп серверов, затем создать один или несколько зарегистрированных серверов в группах и выполнить запрос ко всей группе. Результаты, возвращенные запросом, можно объединить в одну панель результатов или вернуть в отдельные панели результатов. Набор результатов может включать дополнительные столбцы для имени сервера и имени входа, используемые для запроса к каждому серверу. Центральные серверы управления и подчиненные серверы могут быть зарегистрированы с применением проверки подлинности Windows. Серверы в локальных группах серверов можно зарегистрировать с использованием проверки подлинности Windows или проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Перед выполнением следующих процедур создайте центральный сервер управления и группы серверов. Дополнительные сведения см. в разделе [Создание центрального сервера управления и группы серверов (среда SQL Server Management Studio)](create-a-central-management-server-and-server-group.md).  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Для выполнения инструкций на нескольких серверах используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Поскольку соединения, поддерживаемые центральным сервером управления, выполняются в контексте пользователя с применением проверки подлинности Windows, действующие разрешения на зарегистрированные серверы могут быть различными. Например, пользователь может входить в предопределенную роль сервера sysadmin на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] А, но иметь ограниченные разрешения на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Б.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-execute-statements-against-multiple-configuration-targets-simultaneously"></a>Выполнение инструкций на нескольких целях конфигурации одновременно  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]в меню **Вид** выберите пункт **Зарегистрированные серверы**.  
  
2.  Разверните центральный сервер управления, щелкните правой кнопкой мыши группу серверов, укажите пункт **Соединить** и выберите **Создать запрос**.  
  
3.  Введите и выполните инструкцию языка [!INCLUDE[tsql](../../includes/tsql-md.md)] в редакторе запросов, например, подобную следующей:  
  
    ```  
    USE master  
    GO  
    SELECT * FROM sysdatabases;  
    GO  
    ```  
  
     По умолчанию панель результатов объединит результаты запросов со всех серверов группы.  
  
#### <a name="to-change-the-multiserver-results-options"></a>Изменение параметров многосерверных результатов  
  
1.  В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]в меню **Сервис** выберите **Параметры**.  
  
2.  Последовательно раскройте панели **Результаты запроса**и **SQL Server**, затем выберите пункт **Многосерверные результаты**.  
  
3.  Укажите требуемые настройки параметра на странице **Многосерверные результаты** и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Администрирование нескольких серверов с использованием центральных серверов управления](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
