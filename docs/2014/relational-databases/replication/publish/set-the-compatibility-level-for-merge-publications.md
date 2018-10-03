---
title: Задание уровня совместимости для публикаций слиянием | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], replication
- backward compatibility [SQL Server], replication
- publications [SQL Server replication], backward compatibility
ms.assetid: db47ac73-948b-4d77-b272-bb3565135ea5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3e3795b11f492a8a691ec8777cb87cf4b8379a76
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218022"
---
# <a name="set-the-compatibility-level-for-merge-publications"></a>Задание уровня совместимости для публикаций слиянием
  В этом разделе описывается установка уровня совместимости для публикации слиянием в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)]. В репликации слиянием с помощью уровня совместимости публикации определяется, какие функции могут использоваться публикациями в указанной базе данных.  
  
 **В этом разделе**  
  
-   **Для установки уровня совместимости для публикаций слиянием используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Установите уровень совместимости на странице **Типы подписчиков** мастера создания публикации. Дополнительные сведения о доступе к этому мастеру см. в разделе [Create a Publication](create-a-publication.md). После создания моментального снимка публикации уровень совместимости можно увеличить, но нельзя снизить. Увеличьте уровень совместимости на странице **Общие** диалогового окна **Свойства публикации — \<публикация>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](view-and-modify-publication-properties.md). При повышении уровня совместимости публикации все существующие подписки на серверах, использующих версии с меньшими уровнями совместимости, более не смогут синхронизироваться.  
  
> [!NOTE]  
>  Так как уровень совместимости влияет на другие свойства публикации, для которых свойства статьи являются допустимыми, не изменяйте одновременно уровень совместимости и другие свойства в одном сеансе работы с диалоговым окном. После изменения свойства необходимо повторно сформировать моментальный снимок публикации.  
  
#### <a name="to-set-the-publication-compatibility-level"></a>Установка уровня совместимости публикации  
  
-   На странице **Типы подписчиков** мастера создания публикации выберите типы подписчиков, которые должны поддерживаться публикацией.  
  
#### <a name="to-increase-the-publication-compatibility-level"></a>Повышение уровня совместимости публикации  
  
-   На странице **Общие** диалогового окна **Свойства публикации — \<публикация>** выберите **Уровень совместимости**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Уровень совместимости для публикации слиянием можно программно установить при создании публикации или программно изменить позже. Установить или изменить свойства публикации можно с помощью хранимых процедур репликации.  
  
#### <a name="to-set-the-publication-compatibility-level-for-a-merge-publication"></a>Установка уровня совместимости для публикации слиянием  
  
1.  Чтобы сделать публикацию совместимой с прежними версиями [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], выполните в издателе хранимую процедуру [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), указав значение для **@publication_compatibility_level**. Дополнительные сведения см. в разделе [Create a Publication](create-a-publication.md).  
  
#### <a name="to-change-the-publication-compatibility-level-of-a-merge-publication"></a>Изменение уровня совместимости для публикации слиянием  
  
1.  Выполните хранимую процедуру [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), указав значение **publication_compatibility_level** для параметра **@property** и соответствующий уровень совместимости публикации в параметре **@value**.  
  
#### <a name="to-determine-the-publication-compatibility-level-of-a-merge-publication"></a>Определение уровня совместимости для публикации слиянием  
  
1.  Выполните процедуру [sp_helpmergepublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), указав нужную публикацию.  
  
2.  Найдите уровень совместимости публикации в столбце **backward_comp_level** результирующего набора.  
  
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
>  Изменение уровня совместимости публикации может быть запрещено, если публикация использует функции, для которых необходим конкретный уровень совместимости. Дополнительные сведения см. в статье [Обратная совместимость репликации](../replication-backward-compatibility.md).  
  
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
  
## <a name="see-also"></a>См. также  
 [Create a Publication](create-a-publication.md)  
  
  
