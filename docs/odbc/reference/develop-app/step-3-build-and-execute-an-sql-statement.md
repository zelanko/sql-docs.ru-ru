---
title: Шаг 3. сборка и выполнение инструкции SQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], building and executing statements
- SQL statements [ODBC], building and executing
ms.assetid: 133b8bd4-a3c8-4f7e-93c5-c05283c8e96f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e8322cf5e7b4a91bfc5f5f0204cfb25fa4bdad92
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306835"
---
# <a name="step-3-build-and-execute-an-sql-statement"></a>Шаг 3. Построение и выполнение инструкции SQL
Третий шаг — создать и выполнить инструкцию SQL, как показано на следующем рисунке. Методы, используемые для выполнения этого шага, скорее всего, будут варьировать невероятно. Приложение может предложить пользователю ввести инструкцию SQL, построить инструкцию SQL на основе вводимых пользователем данных или использовать жестко запрограммированную инструкцию SQL. Дополнительные сведения см. в разделе [Конструирование инструкций SQL](../../../odbc/reference/develop-app/constructing-sql-statements.md).  
  
 ![Построение и выполнение инструкции SQL](../../../odbc/reference/develop-app/media/pr13.gif "pr13")  
  
 Если инструкция SQL содержит параметры, приложение привязывает их к переменным приложения, вызывая **SQLBindParameter** для каждого параметра. Дополнительные сведения см. в разделе [Параметры инструкции](../../../odbc/reference/develop-app/statement-parameters.md).  
  
 После сборки инструкции SQL и привязки любых параметров инструкция выполняется с помощью **SQLExecDirect**. Если инструкция будет выполняться несколько раз, ее можно подготовить с помощью **SQLPrepare** и выполнить с помощью **SQLExecute**. Дополнительные сведения см. [в разделе исполнение инструкции](../../../odbc/reference/develop-app/executing-a-statement.md).  
  
 Приложение также может отказаться от полностью выполнять инструкцию SQL, а вместо этого вызывать функцию для возврата результирующего набора, содержащего сведения о каталоге, например доступные столбцы или таблицы. Дополнительные сведения см. в разделе [использование данных каталога](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Следующее действие приложения зависит от типа выполняемой инструкции SQL.  
  
|Тип инструкции SQL|Перейти к|  
|---------------------------|----------------|  
|**SELECT** или функция Catalog|[Шаг 4а. Выборка результатов](../../../odbc/reference/develop-app/step-4a-fetch-the-results.md)|  
|**Обновление**, **Удаление**или **Вставка**|[Шаг 4б. Выборка числа строк](../../../odbc/reference/develop-app/step-4b-fetch-the-row-count.md)|  
|Все остальные инструкции SQL|Шаг 3. сборка и выполнение инструкции SQL (в этом разделе) или [шага 5. Фиксация транзакции](../../../odbc/reference/develop-app/step-5-commit-the-transaction.md)|
