---
title: Ограничения инструкции SELECT | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, SELECT statement limitations
- SELECT statement limitations [ODBC]
ms.assetid: c6b05955-f8fd-4706-a1a7-a8dbd74870c2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26bf17596dbd3279498df2edcee7636db95ae139
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63127851"
---
# <a name="select-statement-limitations"></a>Ограничения инструкции SELECT
Столбец функции статистическое выражение нельзя комбинировать с нестатистическим столбец в инструкции SELECT.  
  
 Список выбора инструкции SELECT с предложением GROUP BY может иметь только выражения из предложения GROUP BY или набор функций.  
  
 Использование в виде звездочки (чтобы выбрать все столбцы) в инструкции SELECT, содержащая предложение GROUP BY не поддерживается. Необходимо указать имена столбцов для выбора.  
  
 Использование вертикальной чертой в инструкции SELECT не поддерживается. Использование параметра в инструкции SELECT, если вам потребуется обратиться к значению данных, содержащий вертикальной чертой.  
  
 При использовании псевдонима столбца в инструкции SELECT, слово «как» должен предшествовать псевдоним. Например «SELECT col1 как из б.» Без «как» инструкция возвращает ошибку.  
  
 Если в инструкцию SELECT, введено имя неправильный столбец, то SQLSTATE 07001, «Неверный номер из Parameters» возвращается ошибка вместо ошибки SQLSTATE S0022, «столбец не найден.»  
  
 При использовании драйвера Microsoft Excel, если пустая строка вставляется в столбец, пустая строка преобразуется в значение NULL; Искомая инструкции SELECT, который выполняется с пустой строкой в предложении WHERE не будет выполнено по этому столбцу.
