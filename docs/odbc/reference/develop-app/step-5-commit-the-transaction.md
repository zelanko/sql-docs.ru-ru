---
title: Шаг 5. Фиксация транзакции | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], committing transactions
- committing transactions [ODBC]
- transaction commit [ODBC]
ms.assetid: 311685e2-f7b5-4ddc-8020-59380cd2f035
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bde493edbc6d677b27ef72a24736b504959a7b59
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114132"
---
# <a name="step-5-commit-the-transaction"></a>Шаг 5. Фиксация транзакции
Следующим шагом является фиксация транзакции, как показано на следующем рисунке.  
  
 ![Способы фиксации транзакции](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 Пятый шаг заключается в вызове **SQLEndTran** для фиксации или отката транзакции. Приложение выполняет этот шаг только в том случае, если для режима фиксации транзакции задано ручное фиксация. Если режим фиксации транзакции является автоматической фиксацией, то есть по умолчанию, транзакция автоматически фиксируется при выполнении инструкции. Дополнительные сведения см. в разделе [Transactions](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Чтобы выполнить инструкцию в новой транзакции, приложение вернется к шагу 3. Чтобы отключиться от источника данных, приложение переходит к шагу 6.
