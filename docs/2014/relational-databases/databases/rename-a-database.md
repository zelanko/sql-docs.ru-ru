---
title: Переименование базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], renaming
- renaming databases
ms.assetid: 44c69d35-abcb-4da3-9370-5e0bc9a28496
author: stevestein
ms.author: sstein
ms.openlocfilehash: dd25a78e3d3b9be2e7191ce6ed3d6bdcbb0f9606
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965821"
---
# <a name="rename-a-database"></a>Переименование базы данных
  В этом подразделе описывается, как переименовать пользовательскую базу данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Имя базы данных может содержать все символы, соответствующие правилам для идентификаторов.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Переименование базы данных с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После переименования базы данных](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Системные базы данных не могут быть переименованы.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER на базу данных.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-rename-a-database"></a>Переименование базы данных  
  
1.  В **обозревателе объектов**подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , а затем разверните этот экземпляр.  
  
2.  Убедитесь в том, что никто не использует эту базу данных, а затем [переведите ее в однопользовательский режим работы](set-a-database-to-single-user-mode.md).  
  
3.  Раскройте узел **Базы данных**, щелкните правой кнопкой мыши базу данных, которую необходимо переименовать, а затем выберите пункт **Переименовать**.  
  
4.  Введите новое имя базы данных и нажмите кнопку **ОК**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-rename-a-database"></a>Переименование базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере имя базы данных `AdventureWorks2012` изменяется на `Northwind`.  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
Modify Name = Northwind ;  
GO  
```  
  
###  <a name="TsqlExample"></a>   
##  <a name="follow-up-after-renaming-a-database"></a><a name="FollowUp"></a> Дальнейшие действия. После переименования базы данных  
 Создавайте резервную копию базы данных **master** после переименования любой базы данных.  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)   
 [Идентификаторы баз данных](database-identifiers.md)  
  
  
