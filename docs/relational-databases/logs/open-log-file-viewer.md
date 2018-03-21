---
title: "Открытие средства просмотра журналов | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: logs
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Log File Viewer, opening
ms.assetid: a86b89cb-0432-4648-895a-05ecc5450e45
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7e0c020a4c4726f79887c966ad2c30252c29daa6
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2018
---
# <a name="open-log-file-viewer"></a>Открытие средства просмотра файла журнала
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Средство просмотра журнала используется в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для доступа к сведениям об ошибках и событиях, записываемых в следующие журналы.  
  
-   Коллекция аудита  
  
-   Сбор данных  
  
-   Database Mail  
  
-   Журнал заданий  
  
-   SQL Server  
  
-   SQL Server, агент  
  
-   События Windows (К ним можно получить доступ с помощью программы просмотра событий Windows.)  
  
 Начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], в списке «Зарегистрированные серверы» можно просматривать файлы журналов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на локальных и удаленных экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В списке «Зарегистрированные серверы» можно просматривать файлы журнала как для экземпляров в сети, так и для экземпляров вне сети. Дополнительные сведения о доступе в сети см. далее в разделе «Просмотр файлов журнала в сети с зарегистрированных серверов». Дополнительные сведения о доступе к автономным файлам журнала [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Просмотр автономных файлов журнала](../../relational-databases/logs/view-offline-log-files.md).  
  
 Открыть средство просмотра журнала можно несколькими способами (в зависимости от того, какие сведения нужно просмотреть).  
  
##  <a name="BeforeYouBegin"></a> Разрешения  
 Чтобы получить доступ к файлам журнала для экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые находятся в сети, требуется членство в предопределенной роли сервера securityadmin.  
  
 Чтобы получить доступ к файлам журнала для экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые находятся вне сети, необходим доступ на чтение к пространству WMI **Root\Microsoft\SqlServer\ComputerManagement10** , а также к папке, в которой хранятся файлы журнала. Дополнительные сведения см. в подразделе "Безопасность" раздела [Просмотр автономных файлов журнала](../../relational-databases/logs/view-offline-log-files.md).  
  
### <a name="security"></a>безопасность  
 Требуется членство в предопределенной роли сервера securityadmin.  
  
### <a name="view-log-files"></a>Просмотр файлов журнала  
  
##### <a name="to-view-logs-that-are-related-to-general-sql-server-activity"></a>Просмотр журналов, связанных с общими операциями SQL Server  
  
1.  В обозревателе объектов разверните узел **Управление**.  
  
2.  Выполните любое из следующих действий.  
  
    -   Щелкните правой кнопкой мыши **Журналы SQL Server**, выберите **Просмотр**, а затем **Журнал SQL Server** или **Журнал SQL Server и Windows**.  
  
    -   Разверните узел **Журналы SQL Server**, щелкните правой кнопкой мыши любой файл журнала и выберите **Просмотреть журнал SQL Server**. Можно также дважды щелкнуть любой файл журнала.  
  
     Доступны журналы **Компонент Database Mail**, **SQL Server**, **Агент SQL Server**и **Windows NT**.  
  
##### <a name="to-view-logs-that-are-related-to-jobs"></a>Просмотр журналов, связанных с заданиями  
  
-   В обозревателе объектов откройте **Агент SQL Server**, щелкните правой кнопкой мыши **Задания**и выберите **Просмотр журнала**.  
  
     Доступны журналы **Компонент Database Mail**, **Журнал заданий**и **Агент SQL Server**.  
  
##### <a name="to-view-logs-that-are-related-to-maintenance-plans"></a>Просмотр журналов, связанных с планами обслуживания  
  
-   В обозревателе объектов раскройте узел **Управление**, щелкните правой кнопкой мыши **Планы обслуживания**и выберите **Просмотр журнала**.  
  
     Доступны журналы **Компонент Database Mail**, **Журнал заданий**, **Планы обслуживания**, **План удаленного обслуживания**и **Агент SQL Server**.  
  
##### <a name="to-view-logs-that-are-related-to-data-collection"></a>Просмотр журналов, связанных с коллекциями данных  
  
-   В обозревателе объектов раскройте узел **Управление**, щелкните правой кнопкой мыши **Сбор данных**и выберите команду **Просмотреть журналы**.  
  
     Доступны журналы **Сбор данных**, **Журнал заданий**и **Агент SQL Server**.  
  
##### <a name="to-view-logs-that-are-related-to-database-mail"></a>Просмотр журналов, связанных с компонентом Database Mail  
  
-   В обозревателе объектов раскройте узел **Управление**, щелкните правой кнопкой мыши **Компонент Database Mail**и выберите команду **Просмотреть журнал компонента Database Mail**.  
  
     Доступны журналы **Компонент Database Mail, Журнал заданий**, **Планы обслуживания**, **Планы удаленного обслуживания**, **SQL Server**, **Агент SQL Server**и **Windows NT**.  
  
##### <a name="to-view-logs-that-are-related-to-audits-collections"></a>Просмотр журналов, связанных с коллекциями аудитов  
  
-   В обозревателе объектов разверните узел **Безопасность**, затем узел **Аудиты**, щелкните правой кнопкой мыши аудит и выберите команду **Просмотреть журналы**.  
  
     Доступны журналы **Коллекция аудитов** и **Windows NT**.  
  
##### <a name="to-view-logs-that-are-related-to-audits-collections"></a>Просмотр журналов, связанных с коллекциями аудитов  
  
-   В обозревателе объектов разверните узел **Безопасность**, затем узел **Аудиты**, щелкните правой кнопкой мыши аудит и выберите команду **Просмотреть журналы**.  
  
     Доступны журналы **Коллекция аудитов** и **Windows NT**.  
  
## <a name="see-also"></a>См. также:  
 [Средство просмотра файлов журнала](../../relational-databases/logs/log-file-viewer.md)   
 [Подсистема аудита SQL Server (компонент Database Engine)](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)   
 [Просмотр автономных файлов журнала](../../relational-databases/logs/view-offline-log-files.md)  
  
  
