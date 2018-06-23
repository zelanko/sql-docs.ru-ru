---
title: Изменение порядка столбцов в таблице | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- columns [SQL Server], change order in a table
- column order, change
ms.assetid: cd99ef56-9085-431a-a0fc-58e7add5399f
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 07dbfa235a722220d42e68d7f98485a8a85e829f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087573"
---
# <a name="change-column-order-in-a-table"></a>Изменение порядка столбцов в таблице
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