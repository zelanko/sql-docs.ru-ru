---
title: Внешние объединения | Документация Майкрософт
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
ms.openlocfilehash: a4bf875b3afd21f6b8cb211c999401b0ecb80879
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67987813"
---
# <a name="outer-joins"></a>Внешние соединения
ODBC поддерживает синтаксис по левому, правому, и полному внешнему соединению SQL-92. Escape-последовательность для внешних соединений  
  
 **{ОЖ** _OUTER-JOIN_**}**  
  
 где *внешнее соединение*  
  
 *Таблица-ссылка* {**LEFT &#124; право &#124; полное} внешнее соединение** {*Таблица-ссылка* &#124; *внешнее соединение*} **в** _условии поиска_  
  
 *Таблица-Reference* указывает имя таблицы, а *условие поиска* задает условие объединения для *ссылок на таблицы*.  
  
 Запрос внешнего объединения должен находиться после ключевого слова **from** и перед предложением **WHERE** (если оно существует). Полные сведения о синтаксисе см. в разделе [escape-последовательность внешнего объединения](../../../odbc/reference/appendixes/outer-join-escape-sequence.md) в приложении C: грамматика SQL.  
  
 Например, следующие инструкции SQL создают тот же результирующий набор, в котором перечислены все клиенты и показаны открытые заказы. В первой инструкции используется синтаксис escape-последовательности. Вторая инструкция использует собственный синтаксис для Oracle и не поддерживает взаимодействие.  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM {oj Customers LEFT OUTER JOIN Orders ON Customers.CustID=Orders.CustID}  
   WHERE Orders.Status='OPEN'  
  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM Customers, Orders  
   WHERE (Orders.Status='OPEN') AND (Customers.CustID= Orders.CustID(+))  
```  
  
 Чтобы определить типы внешних соединений, поддерживаемых источником данных и драйвером, приложение вызывает **SQLGetInfo** с флагом SQL_OJ_CAPABILITIES. Типы внешних соединений, которые могут поддерживаться, — это левые, правые, полные или вложенные внешние объединения. внешние объединения, в которых имена столбцов в предложении **On** не имеют того же порядка, что и соответствующие имена таблиц в предложении **внешнего объединения** ; внутренние объединения в сочетании с внешними объединениями; и внешние соединения с использованием любого оператора сравнения ODBC. Если тип сведений SQL_OJ_CAPABILITIES возвращает значение 0, предложение внешнего объединения не поддерживается.
