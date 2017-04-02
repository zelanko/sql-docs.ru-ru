---
title: "Задание уровня совместимости для публикаций слиянием | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "совместимость [SQL Server], репликация"
  - "обратная совместимость [SQL Server], репликация"
  - "публикации [репликация SQL Server], обратная совместимость"
ms.assetid: db47ac73-948b-4d77-b272-bb3565135ea5
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# Задание уровня совместимости для публикаций слиянием
  В этом разделе описывается установка уровня совместимости для публикации слиянием в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)]. В репликации слиянием с помощью уровня совместимости публикации определяется, какие функции могут использоваться публикациями в указанной базе данных.  
  
 **В этом разделе**  
  
-   **Для установки уровня совместимости для публикаций слиянием используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Установите уровень совместимости на странице **Типы подписчиков** мастера создания публикации. Дополнительные сведения о доступе к этому мастеру см. в разделе [Создать публикацию](../../../relational-databases/replication/publish/create-a-publication.md). После создания моментального снимка публикации уровень совместимости можно увеличить, но нельзя снизить. Увеличьте уровень совместимости на **Общие** Страница **Свойства публикации — \< публикация>** диалоговое окно. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md). При повышении уровня совместимости публикации все существующие подписки на серверах, использующих версии с меньшими уровнями совместимости, более не смогут синхронизироваться.  
  
> [!NOTE]  
>  Так как уровень совместимости влияет на другие свойства публикации, для которых свойства статьи являются допустимыми, не изменяйте одновременно уровень совместимости и другие свойства в одном сеансе работы с диалоговым окном. После изменения свойства необходимо повторно сформировать моментальный снимок публикации.  
  
#### Установка уровня совместимости публикации  
  
-   На странице **Типы подписчиков** мастера создания публикации выберите типы подписчиков, которые должны поддерживаться публикацией.  
  
#### Повышение уровня совместимости публикации  
  
-   На **Общие** Страница **Свойства публикации — \< публикация>** установите флажок для **уровень совместимости**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Уровень совместимости для публикации слиянием можно программно установить при создании публикации или программно изменить позже. Установить или изменить свойства публикации можно с помощью хранимых процедур репликации.  
  
#### Установка уровня совместимости для публикации слиянием  
  
1.  На издателе, хранимую [sp_addmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md), указав значение для **@publication_compatibility_level** для обеспечения совместимости с более ранними версиями публикации [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Изменение уровня совместимости для публикации слиянием  
  
1.  Выполнение [sp_changemergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), указав **publication_compatibility_level** для **@property** и соответствующий уровень совместимости публикации для **@value**.  
  
#### Определение уровня совместимости для публикации слиянием  
  
1.  Выполнение [sp_helpmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), указав нужную публикацию.  
  
2.  Найдите уровень совместимости публикации в **backward_comp_level** столбца в результирующем наборе.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В примере создается публикация слиянием и устанавливается уровень совместимости публикации.  
  
```  
-- To avoid storing the login and password in the script file, the values   
-- are passed into SQLCMD as scripting variables. For information about   
-- how to use scripting variables on the command line and in SQL Server  
-- Management Studio, see the "Executing Replication Scripts" section in  
-- the topic "Programming Replication Using System Stored Procedures".  
  
--Add a new merge publication.  
DECLARE @publicationDB AS sysname;  
DECLARE @publication AS sysname;  
DECLARE @login AS sysname;  
DECLARE @password AS sysname;  
SET @publicationDB = N'AdventureWorks2012';   
SET @publication = N'AdvWorksSalesOrdersMerge'   
SET @login = $(Login);  
SET @password = $(Password);  
  
-- Create a new merge publication.   
USE [AdventureWorks2012]  
EXEC sp_addmergepublication   
@publication = @publication,   
-- Set the compatibility level to SQL Server 2014.  
@publication_compatibility_level = '120RTM';   
  
-- Create the snapshot job for the publication.  
EXEC sp_addpublication_snapshot   
@publication = @publication,  
@job_login = @login,  
@job_password = @password;  
GO  
```  
  
 В примере изменяется уровень совместимости публикации для публикации слиянием.  
  
> [!NOTE]  
>  Изменение уровня совместимости публикации может быть запрещено, если публикация использует функции, для которых необходим конкретный уровень совместимости. Дополнительные сведения см. в разделе [обратная совместимость репликации](../../../relational-databases/replication/replication-backward-compatibility.md).  
  
```  
DECLARE @publication AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge' ;  
  
-- Change the publication compatibility level to   
-- SQL Server 2012.  
EXEC sp_changemergepublication   
@publication = @publication,   
@property = N'publication_compatibility_level',   
@value = N'110RTM';  
GO  
  
```  
  
 В примере возвращается текущий уровень совместимости публикации для публикации слиянием.  
  
```  
DECLARE @publication AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge' ;  
EXEC sp_helpmergepublication   
@publication = @publication;  
GO  
  
```  
  
## См. также:  
 [Создание публикации](../../../relational-databases/replication/publish/create-a-publication.md)  
  
  