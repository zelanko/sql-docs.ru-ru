---
title: Внешние соединения Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 81988d34dca38d5c041ff9f87e9674d7c97d76cc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282453"
---
# <a name="outer-joins"></a>Внешние соединения
ODBC поддерживает синтаксис влево, вправо и полное внешнее соединение S'L-92. Последовательность побега для внешних соединений  
  
 **Oj** _внешнее соединение_**}**  
  
 где *внешнее соединение*  
  
 *Таблица-ссылка* -**LEFT &#124; НЕ ИДи &#124; ПОЛНОЕ" OUTER JOIN** -*таблица-ссылка* &#124; *внешнее соединение*- **НА** _поисковое состояние_  
  
 *таблица-ссылка* определяет имя таблицы, а *состояние поиска* определяет условие соединения между *таблицами-ссылками.*  
  
 Внешний запрос соединения должен отображаться после ключевого слова **FROM** и перед положением **WHERE** (если он существует). Для получения полной информации о синтаксисе смотрите [в](../../../odbc/reference/appendixes/outer-join-escape-sequence.md) приложении C: Грамматика СЗЛ.  
  
 Например, следующие операторы S'L создают один и тот же набор результатов, в котором перечислены все клиенты и отображается, который имеет открытые заказы. В первом заявлении используется синтаксис побега-последовательности. Второе утверждение использует родной синтаксис для Oracle и не совместимо.  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM {oj Customers LEFT OUTER JOIN Orders ON Customers.CustID=Orders.CustID}  
   WHERE Orders.Status='OPEN'  
  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM Customers, Orders  
   WHERE (Orders.Status='OPEN') AND (Customers.CustID= Orders.CustID(+))  
```  
  
 Чтобы определить типы внешних соединений, которые источник данных и поддержка драйверов, приложение вызывает **S'LGetInfo** с SQL_OJ_CAPABILITIES флагом. Типы внешних соединений, которые могут быть поддержаны, являются левыми, правыми, полными или вложенными внешними соединениями; внешние соединения, в которых имена столбцов в оговорке **ON** не имеют того же порядка, что и их имена таблиц в оговорке **OUTER JOIN;** внутренние соединения в сочетании с внешними соединениями; и внешние соединения с помощью любого оператора сравнения ODBC. Если SQL_OJ_CAPABILITIES тип информации возвращает 0, ни одно внешнее положение о соединении не поддерживается.
