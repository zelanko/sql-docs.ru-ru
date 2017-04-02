---
title: "Просмотр журнала ошибок SQL Server (среда SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "07/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "просмотр журналов"
  - "отображение журналов"
  - "ошибки [агент SQL Server], журналы"
  - "журналы [SQL Server], журналы ошибок SQL Server"
  - "журналы [SQL Server], просмотр"
ms.assetid: 55f468ba-146c-4ab3-95cd-d35d051afd12
caps.latest.revision: 14
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 14
---
# Просмотр журнала ошибок SQL Server (среда SQL Server Management Studio)
  В журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записываются пользовательские и определенные системные события, которые пригодятся при устранении неполадок. 
  

  ## Просмотр журналов
1.  В SSMS выберите **Обозреватель объектов**

>Чтобы **открыть** обозреватель объектов, используйте клавишу **F8** на клавиатуре. Или в главном меню щелкните "Вид"/"Обозреватель объектов" ![Object_explorer](../../relational-databases/performance/media/object-explorer.png) 


2.  В **обозревателе объектов** подключитесь к экземпляру SQL Server и разверните его.
  
3.  Найдите и разверните раздел **Управление** (при условии, что у вас есть разрешения на его просмотр).

4.  Щелкните правой кнопкой мыши **Журналы SQL Server**, выберите "Просмотр" и **Просмотр журнала SQL Server**.
 ![View_SQLServer_Log_SSMS](../../relational-databases/performance/media/view-sqlserver-log-ssms.png) 
 
5.  Отображается средство просмотра журнала (это может занять около минуты) со списком журналов для просмотра.
  
6. Несколько пользователей порекомендовали статью [Identify location of the SQL Server Error Log file](https://www.mssqltips.com/sqlservertip/2506/identify-location-of-the-sql-server-error-log-file/) (Расположение удостоверения для файла журнала SQL Server) на сайте [MSSQLTips.com](https://www.mssqltips.com/). Там доступно еще огромное количество полезной информации, советуем вам ознакомиться с этим ресурсом.
  
  