---
title: "Embedded SQL | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- sending SQL statements to DBMS [ODBC]
- SQL statements [ODBC], embedded SQL
- ODBC [ODBC], SQL
- embedded SQL [ODBC]
ms.assetid: 8eee3527-f225-4aa2-bd18-a16bd3ab0fb7
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 12d0e4edc34ceb02f9b902016eb82b489c4ca71d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="embedded-sql"></a>Embedded SQL
Внедренные первый метод для отправки инструкций SQL в СУБД SQL. Поскольку SQL не используют переменные и инструкции управления потоком, он часто используется в качестве диалекте базы данных, который может быть добавлен к программе на языке обычной языке программирования, например C или COBOL. Это центра общее представление о embedded SQL: помещение инструкций SQL в программе на языке узел языка программирования. Коротко говоря следующие методы, используемые для внедрения инструкций SQL в основного языка.  
  
-   Внедренные инструкции SQL обрабатываются специальные предкомпилированного SQL. Все инструкции SQL начинаются с introducer и заканчиваться признак конца, оба из которых флаг инструкцию SQL для предварительной компиляции. Introducer и признак конца, зависят от основного языка. Например, introducer является «EXEC SQL» в языке C и «& SQL ("в MUMPS, и признак конца поля является точка с запятой (;) в C и правая круглая скобка в MUMPS.  
  
-   Можно использовать переменные из программы приложения, называются переменными узла в внедренные инструкции SQL, везде, где допускаются константы. Они используются для входных данных, настроить инструкцию SQL для конкретной ситуации и на выходе для получения результатов запроса.  
  
-   Запросы, которые возвращают одну строку данных обрабатываются с помощью инструкции SELECT singleton. Эта инструкция указывает запрос и хост-переменных, в котором для возвращения данных.  
  
-   Запросы, которые возвращают несколько строк данных, обрабатываются с курсорами. Курсор хранит информацию о текущей строки в результирующем наборе. Инструкция DECLARE CURSOR определяет запрос, инструкция OPEN начинает обработку запроса, инструкция FETCH возвращает последовательных строк данных и инструкцию CLOSE завершает обработку запросов.  
  
-   При открытом курсоре позиционированного обновления позиционированные инструкции и delete можно использовать для обновления или удаления строк, выбранного в данный момент курсором.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Образец Embedded SQL](../../odbc/reference/embedded-sql-example.md)  
  
-   [Компиляция программы Embedded SQL](../../odbc/reference/compiling-an-embedded-sql-program.md)  
  
-   [Статический SQL](../../odbc/reference/static-sql.md)  
  
-   [Динамический SQL](../../odbc/reference/dynamic-sql.md)
