---
title: Определение предложения TOP в запросах (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- TOP clause, queries
- percentage of rows returned [SQL Server]
- number of rows
- search conditions [SQL Server], TOP clause
- restricting rows returned
- search criteria [SQL Server], limiting rows returned
- inspecting portion of results
- limiting rows returned
- search criteria [SQL Server], TOP clause
ms.assetid: ba7d7c10-9bb3-4d9b-90b0-5fa94ecae59b
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1726f0c0ba83e689a0f09dc9e6f64d4175302b36
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37327004"
---
# <a name="specify-the-top-clause-in-queries-visual-database-tools"></a>Указание предложения TOP в запросах (визуальные инструменты для баз данных)
  При использовании предложения TOP возвращаются только первые *n* или *n процентов* строк запроса. Предложение TOP полезно, когда нужно исследовать только часть результатов, чтобы определить, выполняет ли запрос то, что предполагалось, и не затрачивать ресурсы, необходимые для возвращения всех результатов.  
  
### <a name="to-specify-the-top-clause-in-queries"></a>Указание в запросе предложения TOP  
  
1.  Откройте запрос с помощью обозревателя решений или создайте новый.  
  
2.  В меню **Вид** выберите **Окно "Свойства"**.  
  
3.  В разделе **Окно "Свойства"** найдите и разверните свойство **Параметр TOP** .  
  
4.  Щелкните дочернее свойство **(Top)** и выберите значение **Да**.  
  
5.  В дочернем свойстве **Выражение** введите выражение с численным результатом (например, "10" или "2*5").  
  
6.  Щелкните дочернее свойство **В процентах** и определите, обрабатывать ли значение свойства **Выражение** как проценты от числа возвращаемых строк ("Да") или как абсолютное число возвращаемых строк ("Нет").  
  
7.  Если в запросе присутствует предложение ORDER BY, щелкните дочернее свойство **Со связями** и выберите **Да** для отображения всех строк группы, если в результаты вошла только часть группы, или **Нет** для усечения результатов.  
  
 Обратите внимание, что при выполнении шагов описанной выше процедуры предложение TOP, отображающееся на панели SQL, меняется в соответствии с текущими значениями свойств.  
  
> [!NOTE]  
>  Можно также изменить значения дочерних свойств **Параметр TOP** , редактируя предложение TOP на панели SQL.  
  
## <a name="see-also"></a>См. также  
 [Проектирование запросов и представлений инструкции &#40;визуальных инструментах баз данных&#41;](visual-database-tools.md)   
 [Свойства запроса (визуальные инструменты для баз данных)](query-properties-visual-database-tools.md)  
  
  
