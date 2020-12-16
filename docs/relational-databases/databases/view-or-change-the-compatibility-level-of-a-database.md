---
title: Просмотр или изменение уровня совместимости базы данных | Документация Майкрософт
description: Узнайте, как на SQL Server просматривать или менять уровень совместимости базы данных с помощью SQL Server Management Studio или Transact-SQL.
ms.custom: ''
ms.date: 11/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8b513694dacf477f0fde5d90ee9be6952158aa63
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97481425"
---
# <a name="view-or-change-the-compatibility-level-of-a-database"></a>Просмотр или изменение уровня совместимости базы данных
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  В этом разделе описывается просмотр и изменение уровня совместимости базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Перед изменением уровня совместимости базы данных проанализируйте, как это повлияет на имеющиеся приложения. Дополнительные сведения см. в разделе [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Просмотр или изменение уровня совместимости базы данных с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER на базу данных.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-or-change-the-compatibility-level-of-a-database"></a>Просмотр или изменение уровня совместимости базы данных  
  
1.  После соединения с соответствующим экземпляром [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]в обозревателе объектов нажмите имя сервера.  
  
2.  Раскройте узел **Базы данных** и в зависимости от типа восстанавливаемой базы данных выберите пользовательскую базу данных или раскройте узел **Системные базы данных** и выберите системную базу данных.  
  
3.  Щелкните правой кнопкой мыши базу данных, а затем выберите пункт **Свойства**.  
  
     Откроется диалоговое окно **Свойства базы данных** .  
  
4.  На панели **Выбор страницы** щелкните **Параметры**.  
  
     Текущий уровень совместимости будет указан в списке **Уровень совместимости** .  
  
5.  Чтобы изменить уровень совместимости, выберите в списке другой параметр. Доступные параметры для разных версий [!INCLUDE[ssde_md](../../includes/ssde_md.md)] указаны на странице [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md#supported-dbcompats).  

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
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
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере изменяется уровень совместимости базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] на `120`, т. е. на значение уровня совместимости для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET COMPATIBILITY_LEVEL = 120;  
GO  
```  
  
## <a name="see-also"></a>См. также:
 [Уровень совместимости инструкции ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)
