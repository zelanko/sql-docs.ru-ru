---
title: "Шаг 5: Зафиксировать транзакцию | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application process [ODBC], committing transactions
- committing transactions [ODBC]
- transaction commit [ODBC]
ms.assetid: 311685e2-f7b5-4ddc-8020-59380cd2f035
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8494c26badd04a1c009f8f23c60559ed695ea3d2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="step-5-commit-the-transaction"></a>Шаг 5: Фиксация транзакции
Следующим шагом является зафиксировать транзакцию, как показано на следующем рисунке.  
  
 ![Способы фиксации транзакции](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 Пятым шагом является вызов **SQLEndTran** для фиксации или отката транзакции. Приложение выполняет этот шаг только в том случае, если его значение режима фиксации транзакции ручной фиксации; режим фиксации транзакции в случае автоматической фиксации, используемом по умолчанию, транзакция автоматически завершается при выполнении инструкции. Дополнительные сведения см. в разделе [транзакции](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Выполнить инструкцию в новой транзакции, приложение возвращается к шагу 3. Отключение от источника данных, приложение переходит к шагу 6.
