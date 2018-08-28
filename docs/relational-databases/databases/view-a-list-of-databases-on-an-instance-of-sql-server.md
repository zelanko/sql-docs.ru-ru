---
title: Просмотр списка баз данных в экземпляре SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- current databases
- databases currently on server [SQL Server]
- database list [SQL Server]
- viewing database list
- displaying database list
- databases [SQL Server], viewing
- servers [SQL Server], databases listed on
- listing databases
ms.assetid: 7ee7a789-db36-4be9-8a0e-0362a1e152dd
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 330d3aa585287f2c1442975043ae6a7f0104cd47
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43099089"
---
# <a name="view-a-list-of-databases-on-an-instance-of-sql-server"></a>Просмотр списка баз данных в экземпляре SQL Server
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В этой теме описывается, как просмотреть список баз данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Просмотр списка баз данных в экземпляре SQL Server выполняется при помощи следующих средств.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Если участник, вызывающий представление каталога **sys.databases** , не является владельцем базы данных, а база данных не является базой данных **master** или **tempdb**, минимально необходимыми разрешениями для просмотра соответствующей строки являются разрешения уровня сервера ALTER ANY DATABASE или VIEW ANY DATABASE, или разрешение CREATE DATABASE в базе данных **master** . Узнать базу данных, к которой подключен участник, можно в представлении каталога **sys.databases**.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-a-list-of-databases-on-an-instance-of-sql-server"></a>Просмотр списка баз данных в экземпляре SQL Server  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Для просмотра списка всех баз данных в экземпляре разверните список **Базы данных**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-view-a-list-of-databases-on-an-instance-of-sql-server"></a>Просмотр списка баз данных в экземпляре SQL Server  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. Этот пример возвращает список баз данных, размещенных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Список содержит имена баз данных, их идентификаторы и даты создания.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT name, database_id, create_date  
FROM sys.databases ;  
GO  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Представления каталогов баз данных и файлов (Transact-SQL)](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
  
