---
title: Руководство. Создание модульных тестов SQL Server для функций, триггеров и хранимых процедур | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: bda57c10-a1ab-4a1a-8a71-42085a3cb793
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 5d985e2b2638d8b0047f5b4d010d87c8f631af65
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65090226"
---
# <a name="how-to-create-sql-server-unit-tests-for-functions-triggers-and-stored-procedures"></a>Руководство. создать модульные тесты SQL Server для функций, триггеров и хранимых процедур
Можно написать модульные тесты, которые вычисляют изменения для любого объекта базы данных. При этом SQL Server Data Tools включает дополнительную поддержку создания тестов для функций, триггеров и хранимых процедур баз данных из узла проекта базы данных в обозревателе объектов SQL Server. Заглушки кода Transact\-SQL могут создаваться автоматически и требуют настройки.  
  
### <a name="to-create-a-sql-server-unit-test-from-a-function-trigger-or-stored-procedure"></a>Создание модульного теста SQL Server из функции, триггера или хранимой процедуры  
  
1.  См. раздел [Пошаговое руководство. Создание и запуск модульного теста SQL Server](../ssdt/walkthrough-creating-and-running-a-sql-server-unit-test.md), чтобы найти пример создания модульного теста для хранимой процедуры в разделе "Создание модульного теста SQL Server для хранимых процедур".  
  
    Условие теста «Невключительно» — это условие по умолчанию, которое добавляется в каждый тест. Оно указывает на то, что проверка теста не выполнена. Удалите это условие из теста после добавления других условий. Дополнительные сведения см. в разделе [Как добавить условия теста в модульные тесты SQL Server](../ssdt/how-to-add-test-conditions-to-sql-server-unit-tests.md).  
  
## <a name="see-also"></a>См. также:  
[Создание и определение модульных тестов SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
[Руководство. Создание пустого модульного теста SQL Server](../ssdt/how-to-create-an-empty-sql-server-unit-test.md)  
  
