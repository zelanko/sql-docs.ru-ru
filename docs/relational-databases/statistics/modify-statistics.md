---
title: "Изменение статистики | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: statistics
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-statistics
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- statistics [SQL Server], modifying
- modifying statistics
ms.assetid: b06299ca-ed52-411a-b245-45eac4628c99
caps.latest.revision: "9"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 00114f6c9d691ed00b71c9d640fa57d7676c3426
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="modify-statistics"></a>Изменение статистики
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Существующую статистику в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно изменить с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Для изменения статистики используются:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Должны выполняться следующие требования.  
  
-   пользователь должен иметь разрешение ALTER на таблицу или представление;  
  
-   пользователь должен быть владельцем таблицы или индексированного представления или членом одной из следующих ролей: предопределенная роль сервера **sysadmin** , предопределенная роль базы данных **db_owner** или предопределенная роль базы данных **db_ddladmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-statistics"></a>Изменение статистики  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть базу данных, в которой нужно изменить статистику.  
  
2.  Чтобы развернуть папку **Таблицы** , щелкните значок «плюс».  
  
3.  Щелкните значок «плюс», чтобы развернуть таблицу, в которой нужно изменить статистику.  
  
4.  Щелкните значок «плюс», чтобы развернуть папку **Статистика** .  
  
5.  Щелкните правой кнопкой мыши объект статистики, который нужно изменить, и выберите пункт **Свойства**.  
  
6.  В диалоговом окне **Свойства статистики —** *имя_статистики* на странице **Общие** нажмите кнопку **Добавить**, **Удалить**, **Переместить вверх**, **Переместить вниз**, any combination, to alter the properties of the statistics. Имейте в виду, что положение столбца в сетке **Столбцы статистики** может оказывать значительное влияние на полезность статистики.  
  
7.  Нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Изменение статистики**  
  
 Эту задачу нельзя выполнить с помощью инструкций Transact-SQL. Чтобы изменить статистику с помощью Transact-SQL, нужно удалить существующую статистику и создать ее повторно с новыми атрибутами.  
  
 Дополнительные сведения см. в статьях [DROP STATISTICS (Transact-SQL)](../../t-sql/statements/drop-statistics-transact-sql.md) и [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md).  
  
  
