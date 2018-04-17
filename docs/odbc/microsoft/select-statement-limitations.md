---
title: Инструкция SELECT ограничения | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ODBC SQL grammar, SELECT statement limitations
- SELECT statement limitations [ODBC]
ms.assetid: c6b05955-f8fd-4706-a1a7-a8dbd74870c2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5b36eae112c385cf5cc336640460c704b0bd205e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="select-statement-limitations"></a>Ограничения инструкции SELECT
Столбец функция статистическое выражение нельзя использовать вместе с нестатистическим столбец в инструкции SELECT.  
  
 Список выбора инструкции SELECT с предложением GROUP BY может иметь только выражения из предложения GROUP BY или функции наборов.  
  
 Использование звездочки (для выбора всех столбцов) в инструкции SELECT, содержащая предложение GROUP BY не поддерживается. Необходимо указать имена столбцов для выбора.  
  
 Использование вертикальная черта в инструкции SELECT не поддерживается. Используйте параметр в инструкции SELECT, если вам потребуется обратиться к значению данных, содержащий вертикальной чертой.  
  
 При использовании псевдонима столбца в инструкции SELECT, слово «as» должно предшествовать псевдоним. Например «SELECT col1 как из б.» Без «как» инструкция возвращает ошибку.  
  
 Некорректное название столбца вводится в инструкции SELECT, SQLSTATE 07001, «Неверный номер из параметров» будет возвращена ошибка вместо ошибки SQLSTATE S0022, «столбец не найден».  
  
 При использовании драйвера Microsoft Excel, если пустая строка вставляется в столбец, пустая строка преобразуется в значение NULL; Искомая инструкции SELECT, который выполняется с пустой строкой в предложении WHERE не будет выполнено в этом столбце.
