---
title: Практическое руководство. Создание модульных тестов SQL Server для функций, триггеров и хранимых процедур | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: bda57c10-a1ab-4a1a-8a71-42085a3cb793
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c4ba18b045570c365a53371d0abc54c86582cfd4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47835912"
---
# <a name="how-to-create-sql-server-unit-tests-for-functions-triggers-and-stored-procedures"></a>Практическое руководство. Создание модульных тестов SQL Server для функций, триггеров и хранимых процедур
Можно написать модульные тесты, которые вычисляют изменения для любого объекта базы данных. При этом SQL Server Data Tools включает дополнительную поддержку создания тестов для функций, триггеров и хранимых процедур баз данных из узла проекта базы данных в обозревателе объектов SQL Server. Заглушки кода Transact\-SQL могут создаваться автоматически и требуют настройки.  
  
### <a name="to-create-a-sql-server-unit-test-from-a-function-trigger-or-stored-procedure"></a>Создание модульного теста SQL Server из функции, триггера или хранимой процедуры  
  
1.  Пример создания модульного теста для хранимой процедуры см. в статье [ из раздела «Создание модульного теста ](../ssdt/walkthrough-creating-and-running-a-sql-server-unit-test.md) для хранимых процедур».  
  
    Условие теста «Невключительно» — это условие по умолчанию, которое добавляется в каждый тест. Оно указывает на то, что проверка теста не выполнена. Удалите это условие из теста после добавления других условий. Дополнительные сведения см. в статье [Практическое руководство. Добавление условий теста в модульные тесты SQL Server](../ssdt/how-to-add-test-conditions-to-sql-server-unit-tests.md).  
  
## <a name="see-also"></a>См. также:  
[Создание и определение модульных тестов SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
[Практическое руководство. Создание пустого модульного теста SQL Server](../ssdt/how-to-create-an-empty-sql-server-unit-test.md)  
  
