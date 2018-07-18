---
title: 'Шаг 3: Построение и выполнение инструкций SQL | Документы Microsoft'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], building and executing statements
- SQL statements [ODBC], building and executing
ms.assetid: 133b8bd4-a3c8-4f7e-93c5-c05283c8e96f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f972fb5a0edfbbf492860e3421d5985d5e4edcc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915509"
---
# <a name="step-3-build-and-execute-an-sql-statement"></a>Шаг 3: Построение и выполнение инструкций SQL
Третий шаг — построение и выполнение инструкций SQL, как показано на следующем рисунке. Методы, используемые для выполнения этого шага, могут отличаться невероятно. Приложение может предложить пользователю ввести инструкцию SQL, построение инструкции SQL на основе ввода пользователя или использование жестко запрограммированных инструкции SQL. Дополнительные сведения см. в разделе [построение инструкции SQL](../../../odbc/reference/develop-app/constructing-sql-statements.md).  
  
 ![Показывает, построения и выполнения инструкции SQL](../../../odbc/reference/develop-app/media/pr13.gif "pr13")  
  
 Если инструкция SQL содержит параметры, приложение привязывает их к переменным приложения, вызвав **SQLBindParameter** для каждого параметра. Дополнительные сведения см. в разделе [параметров инструкции](../../../odbc/reference/develop-app/statement-parameters.md).  
  
 После построения инструкции SQL и любые параметры привязаны, инструкция выполняется с **SQLExecDirect**. Если инструкция будет выполняться несколько раз, он может быть подготовлен с **SQLPrepare** и выполняются с **SQLExecute**. Дополнительные сведения см. в разделе [выполнение инструкции](../../../odbc/reference/develop-app/executing-a-statement.md).  
  
 Приложение может также отказ от выполнение инструкции SQL и вместо этого вызовите функцию, чтобы возвратить результирующий набор, содержащий сведения о каталоге, таких как доступные столбцы или таблицы. Дополнительные сведения см. в разделе [использует данные из каталога](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Следующее действие приложения зависит от типа выполняемой инструкции SQL.  
  
|Тип инструкции SQL|Перейти к|  
|---------------------------|----------------|  
|**ВЫБЕРИТЕ** или каталога, функция|[Шаг 4а. Выборка результатов](../../../odbc/reference/develop-app/step-4a-fetch-the-results.md)|  
|**ОБНОВЛЕНИЕ**, **удаление**, или **вставки**|[Шаг 4б. Выборка числа строк](../../../odbc/reference/develop-app/step-4b-fetch-the-row-count.md)|  
|Все инструкции SQL|Шаг 3: Построение и выполнение инструкций SQL (этот раздел) или [шаг 5: зафиксировать транзакцию](../../../odbc/reference/develop-app/step-5-commit-the-transaction.md)|
