---
title: "Просмотр журнала приложений Windows (Windows) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "просмотр журналов"
  - "журналы приложений [SQL Server]"
  - "журналы [SQL Server], приложение"
  - "наблюдение за журналом приложений Windows NT [SQL Server]"
  - "журналы приложений Windows NT [SQL Server]"
  - "отображение журналов"
  - "мониторинг [SQL Server], события"
  - "журналы [SQL Server], просмотр"
ms.assetid: 168a6c6e-12df-46a9-9904-55d63ca8fe14
caps.latest.revision: 25
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Просмотр журнала приложений Windows (Windows)
  Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен на использование журнала приложений Windows, каждый сеанс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записывает новые события в этот журнал. В отличие от журнала ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , новый журнал приложений не создается заново каждый раз при запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### Просмотр журнала приложений Windows  
  
1.  В меню **Пуск** укажите пункт **Все программы**, затем **Администрирование**и выберите пункт **Просмотр событий**.  
  
2.  В окне «Просмотр событий» щелкните элемент **Приложение**.  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] события идентифицируются записью **MSSQLSERVER** (именованный экземпляр идентифицируется как **MSSQL$***\<имя_экземпляра>*) в столбце **Источник**. События агента SQL Server идентифицируются записью SQLSERVERAGENT (для именованных экземпляров сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], события агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентифицируются с помощью **SQLAgent$**\<*имя_экземпляра*>). События службы Microsoft Search идентифицируются записью **Microsoft Search**.  
  
4.  Чтобы просмотреть журнал другого компьютера, щелкните правой кнопкой мыши в окне **Просмотр событий**, выберите пункт **Подключение к другому компьютеру** и заполните диалоговое окно **Выбор компьютера**.  
  
5.  Дополнительно для отображения только событий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в меню **Просмотр** выберите пункт **Фильтрация**и в списке **Источник событий** выберите **MSSQLSERVER**. Чтобы просмотреть только события агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в списке **Источник события** вместо этого выберите **SQLSERVERAGENT** .  
  
6.  Чтобы просмотреть дополнительные сведения о событии, дважды щелкните событие.  
  
## См. также:  
 [Просмотр журнала ошибок SQL Server (среда SQL Server Management Studio)](../../relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio.md)  
  
  