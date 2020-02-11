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
manager: craigg
ms.openlocfilehash: f014cb37c6c28a0c9a91bd811b9e94d734167e1e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62916774"
---
# <a name="rename-a-database"></a>Переименование базы данных
  В этом подразделе описывается, как переименовать пользовательскую базу данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Имя базы данных может содержать все символы, соответствующие правилам для идентификаторов.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Переименование базы данных с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После переименования базы данных](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Системные базы данных не могут быть переименованы.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER на базу данных.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-rename-a-database"></a>Переименование базы данных  
  
1.  В **обозревателе объектов**подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], а затем разверните этот экземпляр.  
  
2.  Убедитесь в том, что никто не использует эту базу данных, а затем [переведите ее в однопользовательский режим работы](set-a-database-to-single-user-mode.md).  
  
3.  Раскройте узел **Базы данных**, щелкните правой кнопкой мыши базу данных, которую необходимо переименовать, а затем выберите пункт **Переименовать**.  
  
4.  Введите новое имя базы данных и нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
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
##  <a name="FollowUp"></a>Дальнейшие действия. После переименования базы данных  
 Создавайте резервную копию базы данных **master** после переименования любой базы данных.  
  
## <a name="see-also"></a>См. также:  
 [&#41;Transact-SQL ALTER DATABASE &#40;](/sql/t-sql/statements/alter-database-transact-sql)   
 [Идентификаторы баз данных](database-identifiers.md)  
  
  
