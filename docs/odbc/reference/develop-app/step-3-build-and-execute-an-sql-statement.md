---
title: "Шаг 3: Построить и выполнить заявление S'L (ru) Документы Майкрософт"
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306835"
---
# <a name="step-3-build-and-execute-an-sql-statement"></a>Шаг 3. Построение и выполнение инструкции SQL
Третьим шагом является создание и выполнение оператора S'L, как показано на следующей иллюстрации. Методы, используемые для выполнения этого шага, вероятно, сильно различаются. Приложение может побудить пользователя ввести выписку по S'L, создать выписку по S-L на основе пользовательского ввода или использовать жестко закодированное заявление S'L. Для получения более [подробной информации см.](../../../odbc/reference/develop-app/constructing-sql-statements.md)  
  
 ![Построение и выполнение инструкции SQL](../../../odbc/reference/develop-app/media/pr13.gif "pr13")  
  
 Если в отчете S'L содержатся параметры, приложение связывает их с переменными приложения, вызывая **S'LBindParameter** для каждого параметра. Для получения дополнительной [информации см.](../../../odbc/reference/develop-app/statement-parameters.md)  
  
 После того, как выписка по ЗЗЛ построена и любые параметры связаны, заявление выполняется с **помощью SLExecDirect**. Если выписка будет выполнена несколько раз, она может быть подготовлена с **помощью S'LPrepare** и выполнена с **помощью S'LExecute.** Для получения дополнительной информации [см.](../../../odbc/reference/develop-app/executing-a-statement.md)  
  
 Приложение может также отказаться от выполнения оператора S'L вообще и вместо этого вызвать функцию, чтобы вернуть набор результатов, содержащий информацию каталога, такие как доступные столбцы или таблицы. Для получения дополнительной [информации см.](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
 Следующее действие приложения зависит от типа выполненной выписки S'L.  
  
|Тип оператора S'L|Приступить к|  
|---------------------------|----------------|  
|**функция SELECT** или каталога|[Шаг 4а. Выборка результатов](../../../odbc/reference/develop-app/step-4a-fetch-the-results.md)|  
|**ОБНОВЛЕНИЕ**, **DELETE**, или **INSERT**|[Шаг 4б. Выборка числа строк](../../../odbc/reference/develop-app/step-4b-fetch-the-row-count.md)|  
|Все остальные заявления S'L|Шаг 3: Создайте и выполняйте заявление S'L (эта тема) или [Шаг 5: Совершение транзакции](../../../odbc/reference/develop-app/step-5-commit-the-transaction.md)|
