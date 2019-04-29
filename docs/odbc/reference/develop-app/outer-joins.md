---
title: Внешние соединения | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequences [ODBC]
- escape sequences [ODBC], outer join
ms.assetid: be1a0203-5da9-4871-9566-4bd3fbc0895c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 827dd531eda338f4fd297a4420ed144d46a613ff
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62998933"
---
# <a name="outer-joins"></a>Внешние соединения
ODBC поддерживает SQL-92 слева, справа и полного внешнего соединения синтаксис. Escape-последовательность для внешних соединений  
  
 **{oj** _внешнего соединения_**}**  
  
 где *внешнего соединения* —  
  
 *ссылка на таблицу* {**СЛЕВА &#124; СПРАВА &#124; полный} ВНЕШНЕГО СОЕДИНЕНИЯ** {*ссылку на таблицу* &#124; *внешнего соединения*} **ON**  _условие поиска_  
  
 *ссылка на таблицу* указывает имя таблицы, и *условие поиска* указывает условие объединения *ссылки на таблицу*.  
  
 Запрос внешнего соединения должны располагаться после **FROM** ключевое слово и перед **ГДЕ** предложение (если он существует). Полный синтаксис Подробнее [внешнего соединения escape-последовательности](../../../odbc/reference/appendixes/outer-join-escape-sequence.md) в приложение в: Грамматика SQL.  
  
 Например следующие инструкции SQL создать тот же результирующий набор, который содержит список всех клиентов и показывает, который имеет открытых заказов. В первой инструкции используется синтаксис escape последовательности. Вторая инструкция имеет собственный синтаксис для Oracle и не поддерживает взаимодействие.  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM {oj Customers LEFT OUTER JOIN Orders ON Customers.CustID=Orders.CustID}  
   WHERE Orders.Status='OPEN'  
  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM Customers, Orders  
   WHERE (Orders.Status='OPEN') AND (Customers.CustID= Orders.CustID(+))  
```  
  
 Для определения типа внешнего соединения, которые поддерживают источника данных и драйвера, приложение вызывает **SQLGetInfo** с SQL_OJ_CAPABILITIES флаг. Типа внешнего соединения, которые могут поддерживаться слева, справа, полная или вложенные внешние соединения; внешние соединения, в котором имена столбцов в **ON** предложение не имеют имен их соответствующих таблиц в том же порядке **OUTER JOIN** предложение; внутренние соединения, в сочетании с внешних соединений; и внешние соединения с помощью Любой оператор сравнения ODBC. Если тип данных SQL_OJ_CAPABILITIES возвращает 0, поддерживается без предложения внешнего соединения.
