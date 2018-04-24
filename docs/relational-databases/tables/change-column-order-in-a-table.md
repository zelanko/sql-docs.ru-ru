---
title: Изменение порядка столбцов в таблице | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-tables
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- columns [SQL Server], change order in a table
- column order, change
ms.assetid: cd99ef56-9085-431a-a0fc-58e7add5399f
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 81eb68ed7f5e39d55df10d465d5968bcf9aef617
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="change-column-order-in-a-table"></a>Изменение порядка столбцов в таблице
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] порядок столбцов можно изменить в конструкторе таблиц с использованием [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
> [!CAUTION]  
>  Изменение порядка столбцов в таблицы влияет на коды и приложения, которые зависят от определенного порядка столбцов. Это касается запросов, представлений, хранимых процедур, определяемых пользователем функций и клиентских приложений. Внимательно рассмотрите любые изменения, которые необходимо сделать со столбцом таблицы. Рекомендуется указывать порядок, в котором возвращаются столбцы, на уровне приложения и запроса. Не следует предполагать, что SELECT * будет возвращать все столбцы в ожидаемом порядке, основанном на порядке их определения в таблице. Всегда указывайте столбцы в запросах и приложениях по именам в том порядке, в котором они должны следовать.  
  
 **В этом разделе**  
  
-   **Изменение порядка столбцов с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-change-the-column-order"></a>Изменение порядка столбцов  
  
1.  В **обозревателе объектов**щелкните правой кнопкой мыши таблицу со столбцами, которые нужно переупорядочить, и выберите пункт **Конструктор**.  
  
2.  Выберите окно, находящееся слева от названия столбца, который нужно переупорядочить.  
  
3.  Перетащите столбец в другое местоположение внутри таблицы.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Изменение порядка столбцов**  
  
 Эту задачу нельзя выполнить с помощью инструкций Transact-SQL.  
  
###  <a name="TsqlExample"></a>  
