---
title: "Проверка целостности базы данных с потенциально поврежденными страницами | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a4c27d00dd9b975b8d06e2a9ca9d968e175a0078
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="check-integrity-of-database-with-suspect-pages"></a>Проверка целостности базы данных с потенциально поврежденными страницами
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Это правило проверяет, находятся ли пользовательские базы данных в подозрительном состоянии. Когда компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] считывает страницу базы данных, содержащую ошибку 824, страница помечается как потенциально поврежденная, ее идентификатор записывается в таблицу suspect_pages в msdb, а база данных, содержащая эту страницу, также помечается как подозрительная.  
  
 Ошибка 824 означает, что в ходе операции считывания была обнаружена ошибка логической согласованности данных. Часто эта ошибка свидетельствует о повреждении данных, вызванном сбоями компонента подсистемы ввода-вывода. Это серьезная ошибка, которая угрожает целостности базы данных, поэтому она должна быть немедленно исправлена.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
  
-   Проверьте в журнале ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] наличие сведений об ошибке 824 для этой базы данных.  
  
-   Выполните полную проверку согласованности базы данных ([DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)).  
  
-   Выполните действия, описанные в разделе [MSSQLSERVER_824](http://go.microsoft.com/fwlink/?LinkId=81397).  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Управление таблицей suspect_pages (SQL Server)](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
