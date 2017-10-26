---
title: "Шаг 5: Зафиксировать транзакцию | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application process [ODBC], committing transactions
- committing transactions [ODBC]
- transaction commit [ODBC]
ms.assetid: 311685e2-f7b5-4ddc-8020-59380cd2f035
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9ac53209063a1204b57e7183501b5901dc8ea248
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="step-5-commit-the-transaction"></a>Шаг 5: Фиксация транзакции
Следующим шагом является зафиксировать транзакцию, как показано на следующем рисунке.  
  
 ![Способы фиксации транзакции](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 Пятым шагом является вызов **SQLEndTran** для фиксации или отката транзакции. Приложение выполняет этот шаг только в том случае, если его значение режима фиксации транзакции ручной фиксации; режим фиксации транзакции в случае автоматической фиксации, используемом по умолчанию, транзакция автоматически завершается при выполнении инструкции. Дополнительные сведения см. в разделе [транзакции](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Выполнить инструкцию в новой транзакции, приложение возвращается к шагу 3. Отключение от источника данных, приложение переходит к шагу 6.

