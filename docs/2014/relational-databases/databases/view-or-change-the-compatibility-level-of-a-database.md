---
title: Просмотр или изменение уровня совместимости базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- compatibility levels [SQL Server], viewing
- compatibility [SQL Server], databases
- compatibility levels [SQL Server], changing
ms.assetid: 579867ec-57cb-4cb8-af35-9688c1e9e15d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ccc7b96f4275b09b90b8120813b93f860ec07b9a
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58533576"
---
# <a name="view-or-change-the-compatibility-level-of-a-database"></a>Просмотр или изменение уровня совместимости базы данных
  В этом разделе описывается просмотр и изменение уровня совместимости базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Перед изменением уровня совместимости базы данных проанализируйте, как это повлияет на имеющиеся приложения. Дополнительные сведения см. в разделе [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Просмотр или изменение уровня совместимости базы данных с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER на базу данных.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-or-change-the-compatibility-level-of-a-database"></a>Просмотр или изменение уровня совместимости базы данных  
  
1.  После соединения с соответствующим экземпляром [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]в обозревателе объектов нажмите имя сервера.  
  
2.  Раскройте узел **Базы данных**и в зависимости от типа восстанавливаемой базы данных выберите пользовательскую базу данных или раскройте узел **Системные базы данных** и выберите системную базу данных.  
  
3.  Щелкните правой кнопкой мыши базу данных, а затем выберите пункт **Свойства**.  
  
     Откроется диалоговое окно **Свойства базы данных** .  
  
4.  На панели **Выбор страницы** щелкните **Параметры**.  
  
     Текущий уровень совместимости будет указан в списке **Уровень совместимости** .  
  
5.  Чтобы изменить уровень совместимости, выберите в списке другой параметр. Доступны следующие значения: **SQL Server 2008 (100)**, **SQL Server 2012 (110)** и **SQL Server 2014 (120)**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-view-the-compatibility-level-of-a-database"></a>Просмотр уровня совместимости базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере возвращается уровень совместимости базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT compatibility_level  
FROM sys.databases WHERE name = 'AdventureWorks2012';  
GO  
  
```  
  
#### <a name="to-change-the-compatibility-level-of-a-database"></a>Изменение уровня совместимости базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере изменяется уровень совместимости [!INCLUDE[ssSampleDBobject](../../includes/sssql14-md.md)].  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET COMPATIBILITY_LEVEL = 120;  
GO  
```  
  
  
