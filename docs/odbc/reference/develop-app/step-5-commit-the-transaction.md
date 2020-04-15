---
title: 'Шаг 5: Совершите транзакцию Документы Майкрософт'
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283354"
---
# <a name="step-5-commit-the-transaction"></a>Шаг 5. Фиксация транзакции
Следующим шагом является совершение транзакции, как показано на следующей иллюстрации.  
  
 ![Способы фиксации транзакции](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 Пятый шаг заключается в том, чтобы вызвать **S'LEndTran,** чтобы совершить или откатить транзакцию. Приложение выполняет этот шаг только в том случае, если оно устанавливает режим фиксации транзакции на ручной коммит; если режим фиксации транзакции является автоматическим коммитом, то есть по умолчанию, транзакция автоматически заключается при выполнении оператора. Дополнительные сведения см. в статье о [транзакциях](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Чтобы выполнить выписку в новой транзакции, приложение возвращается к шагу 3. Чтобы отключиться от источника данных, приложение переходит к шагу 6.
