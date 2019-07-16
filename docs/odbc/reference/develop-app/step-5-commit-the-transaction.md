---
title: Шаг 5. Зафиксировать транзакцию | Документация Майкрософт
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114132"
---
# <a name="step-5-commit-the-transaction"></a>Шаг 5. Фиксация транзакции
Следующий шаг заключается в фиксации транзакции, как показано на следующем рисунке.  
  
 ![Показано, как зафиксировать транзакцию](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 Пятый шаг является вызов **SQLEndTran** фиксацию или откат транзакции. Приложение выполняет этот шаг только в том случае, если значение режима фиксации транзакции фиксацией вручную; Если режим фиксации транзакции — автофиксации, который по умолчанию, транзакция автоматически фиксируется, при выполнении инструкции. Дополнительные сведения см. в разделе [транзакции](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Чтобы выполнить инструкцию в новой транзакции, приложение возвращает к шагу 3. Чтобы отключиться от источника данных, приложение переходит к шагу 6.
