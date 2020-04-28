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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e348ce697e512f30db46d14535cf19bd6d530f61
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81283354"
---
# <a name="step-5-commit-the-transaction"></a>Шаг 5. Фиксация транзакции
Следующим шагом является фиксация транзакции, как показано на следующем рисунке.  
  
 ![Способы фиксации транзакции](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 Пятый шаг заключается в вызове **SQLEndTran** для фиксации или отката транзакции. Приложение выполняет этот шаг только в том случае, если для режима фиксации транзакции задано ручное фиксация. Если режим фиксации транзакции является автоматической фиксацией, то есть по умолчанию, транзакция автоматически фиксируется при выполнении инструкции. Дополнительные сведения см. в статье о [транзакциях](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Чтобы выполнить инструкцию в новой транзакции, приложение вернется к шагу 3. Чтобы отключиться от источника данных, приложение переходит к шагу 6.
