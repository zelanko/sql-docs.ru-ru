---
title: Шаг 3. Построение и выполнение инструкций SQL | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a3427057e70ee27fe1108fde71c833f0c511836b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63148972"
---
# <a name="step-3-build-and-execute-an-sql-statement"></a>Шаг 3. Построение и выполнение инструкции SQL
Третий шаг — построение и выполнение инструкций SQL, как показано на следующем рисунке. Методы, используемые для выполнения этого шага могут значительно отличаться. Приложение может предлагать пользователю введите инструкцию SQL, создайте инструкцию SQL, на основе ввода пользователя, или использовать жестко запрограммированные инструкции SQL. Дополнительные сведения см. в разделе [построение инструкций SQL](../../../odbc/reference/develop-app/constructing-sql-statements.md).  
  
 ![Показывает создание и выполнение инструкции SQL](../../../odbc/reference/develop-app/media/pr13.gif "pr13")  
  
 Если инструкция SQL содержит параметры, приложение связывает их с переменными приложения путем вызова **SQLBindParameter** для каждого параметра. Дополнительные сведения см. в разделе [параметров инструкции](../../../odbc/reference/develop-app/statement-parameters.md).  
  
 Когда инструкция SQL строится и любые параметры привязаны, инструкция выполняется с помощью **SQLExecDirect**. Если инструкция будет выполняться несколько раз, его можно подготовить с помощью **SQLPrepare** и выполняются с **SQLExecute**. Дополнительные сведения см. в разделе [выполнение инструкции](../../../odbc/reference/develop-app/executing-a-statement.md).  
  
 Приложение может также отказ от выполнение инструкции SQL и вместо этого вызова функция, возвращающая результирующий набор, содержащий сведения о каталоге, например доступные столбцы или таблицы. Дополнительные сведения см. в разделе [использует данные из каталога](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Следующее действие приложения зависит от типа выполняемой инструкции SQL.  
  
|Тип инструкции SQL|Перейти к|  
|---------------------------|----------------|  
|**ВЫБЕРИТЕ** или каталога, функция|[Шаг 4а. Получить результаты](../../../odbc/reference/develop-app/step-4a-fetch-the-results.md)|  
|**ОБНОВЛЕНИЕ**, **удалить**, или **вставки**|[Шаг 4б. Выборка числа строк](../../../odbc/reference/develop-app/step-4b-fetch-the-row-count.md)|  
|Все другие инструкции SQL|Шаг 3. Построение и выполнение инструкции SQL (этот раздел) или [Step 5: Зафиксировать транзакцию](../../../odbc/reference/develop-app/step-5-commit-the-transaction.md)|
