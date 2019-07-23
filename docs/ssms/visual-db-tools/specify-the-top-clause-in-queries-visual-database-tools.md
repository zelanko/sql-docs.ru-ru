---
title: Определение предложения TOP в запросах (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 3ad88b041167c8940a2243b5ce2dc32c1a58c7f2
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68263535"
---
# <a name="specify-the-top-clause-in-queries-visual-database-tools"></a>Указание предложения TOP в запросах (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
При использовании предложения TOP возвращаются только первые *n* или *n процентов* строк запроса. Предложение TOP полезно, когда нужно исследовать только часть результатов, чтобы определить, выполняет ли запрос то, что предполагалось, и не затрачивать ресурсы, необходимые для возвращения всех результатов.  
  
### <a name="to-specify-the-top-clause-in-queries"></a>Указание в запросе предложения TOP  
  
1.  Откройте запрос с помощью обозревателя решений или создайте новый.  
  
2.  В меню **Вид** выберите **Окно "Свойства"** .  
  
3.  В разделе **Окно "Свойства"** найдите и разверните свойство **Параметр TOP** .  
  
4.  Щелкните дочернее свойство **(Top)** и выберите значение **Да**.  
  
5.  В дочернем свойстве **Выражение** введите выражение с численным результатом (например, "10" или "2*5").  
  
6.  Щелкните дочернее свойство **В процентах** и определите, обрабатывать ли значение свойства **Выражение** как проценты от числа возвращаемых строк ("Да") или как абсолютное число возвращаемых строк ("Нет").  
  
7.  Если в запросе присутствует предложение ORDER BY, щелкните дочернее свойство **Со связями** и выберите **Да** для отображения всех строк группы, если в результаты вошла только часть группы, или **Нет** для усечения результатов.  
  
Обратите внимание, что при выполнении шагов описанной выше процедуры предложение TOP, отображающееся на панели SQL, меняется в соответствии с текущими значениями свойств.  
  
> [!NOTE]  
> Можно также изменить значения дочерних свойств **Параметр TOP** , редактируя предложение TOP на панели SQL.  
  
## <a name="see-also"></a>См. также:  
[Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Свойства запроса (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/query-properties-visual-database-tools.md)  
  
