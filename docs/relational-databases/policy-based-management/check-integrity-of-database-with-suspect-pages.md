---
description: Проверка целостности базы данных с потенциально поврежденными страницами
title: Проверка целостности базы данных с потенциально поврежденными страницами | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 297b61dad13abbc4ab327d2e5432b73961ae443b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494035"
---
# <a name="check-integrity-of-database-with-suspect-pages"></a>Проверка целостности базы данных с потенциально поврежденными страницами
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Это правило проверяет, находится ли пользовательские базы данных в подозрительном состоянии. Когда компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] считывает страницу базы данных, содержащую ошибку 824, страница помечается как потенциально поврежденная, ее идентификатор записывается в таблицу suspect_pages в msdb, а база данных, содержащая эту страницу, также помечается как подозрительная.  
  
 Ошибка 824 означает, что в ходе операции считывания была обнаружена ошибка логической согласованности данных. Часто эта ошибка свидетельствует о повреждении данных, вызванном сбоями компонента подсистемы ввода-вывода. Это серьезная ошибка, которая угрожает целостности базы данных, поэтому она должна быть немедленно исправлена.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
  
-   Проверьте в журнале ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] наличие сведений об ошибке 824 для этой базы данных.  
  
-   Выполните полную проверку согласованности базы данных ([DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)).  
  
-   Выполните действия, описанные в разделе [MSSQLSERVER_824](https://go.microsoft.com/fwlink/?LinkId=81397).  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Управление таблицей suspect_pages (SQL Server)](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
