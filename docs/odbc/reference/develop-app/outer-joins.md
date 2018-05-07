---
title: Внешние соединения | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequences [ODBC]
- escape sequences [ODBC], outer join
ms.assetid: be1a0203-5da9-4871-9566-4bd3fbc0895c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 15ab82f5623bad7d3c82729dfd9077ac967301e5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="outer-joins"></a>Внешние соединения
ODBC поддерживает SQL-92 слева, правое и полное внешнее соединение синтаксис. Escape-последовательность для внешних соединений  
  
 **{oj** *внешнего-соединения ***}**  
  
 где *внешнего соединения* —  
  
 *ссылка на таблицу* {**влево &#124; ПРАВО &#124; полный} ВНЕШНЕГО СОЕДИНЕНИЯ** {*ссылка на таблицу* &#124; *внешнего соединения*} **ON**  *условия поиска*  
  
 *ссылка на таблицу* позволяет задать имя таблицы и *условие поиска* указывает условие соединения между *ссылки на таблицу*.  
  
 Запрос внешнего соединения должны располагаться после **FROM** ключевое слово и перед **ГДЕ** предложения (если он существует). Полный синтаксис Подробнее [Outer Join Escape-последовательности](../../../odbc/reference/appendixes/outer-join-escape-sequence.md) в грамматику SQL приложение C:.  
  
 Например следующие инструкции SQL создать тот же результирующий набор со списком всех клиентов и показывает, которой принадлежит открытых заказов. В первом операторе используется синтаксис escape последовательность. Вторая инструкция использует собственный синтаксис для Oracle и не поддерживает взаимодействие.  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM {oj Customers LEFT OUTER JOIN Orders ON Customers.CustID=Orders.CustID}  
   WHERE Orders.Status='OPEN'  
  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM Customers, Orders  
   WHERE (Orders.Status='OPEN') AND (Customers.CustID= Orders.CustID(+))  
```  
  
 Для определения типа внешнего соединения, поддерживаемые источником данных и драйвера, приложение вызывает **SQLGetInfo** с SQL_OJ_CAPABILITIES флаг. Тип внешнего соединения, которые могут поддерживаться слева, справа, полной обработки или вложенные внешние соединения; внешние соединения, в котором имена столбцов в **ON** предложение не имеют имен их соответствующих таблиц в том же порядке **OUTER JOIN** предложения; внутренние соединения в сочетании с внешних соединений; и внешние соединения с помощью Любой оператор сравнения ODBC. Если тип данных SQL_OJ_CAPABILITIES возвращает 0, поддерживается без предложения внешнего соединения.
