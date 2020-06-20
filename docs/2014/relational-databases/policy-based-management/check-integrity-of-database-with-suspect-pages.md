---
title: Проверка целостности базы данных с потенциально поврежденными страницами | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3cc1f87917c78f34ec7722fa21a1a67fda40a8c6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068971"
---
# <a name="check-integrity-of-database-with-suspect-pages"></a>Проверка целостности базы данных с потенциально поврежденными страницами
  Это правило проверяет, находится ли пользовательские базы данных в подозрительном состоянии. Когда компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] считывает страницу базы данных, содержащую ошибку 824, страница помечается как потенциально поврежденная, ее идентификатор записывается в таблицу suspect_pages в msdb, а база данных, содержащая эту страницу, также помечается как подозрительная.  
  
 Ошибка 824 означает, что в ходе операции считывания была обнаружена ошибка логической согласованности данных. Часто эта ошибка свидетельствует о повреждении данных, вызванном сбоями компонента подсистемы ввода-вывода. Это серьезная ошибка, которая угрожает целостности базы данных, поэтому она должна быть немедленно исправлена.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
  
-   Проверьте в журнале ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] наличие сведений об ошибке 824 для этой базы данных.  
  
-   Выполните полную проверку согласованности базы данных ([DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)).  
  
-   Выполните действия, описанные в разделе [MSSQLSERVER_824](https://go.microsoft.com/fwlink/?LinkId=81397).  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Управление таблицей suspect_pages (SQL Server)](../backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
