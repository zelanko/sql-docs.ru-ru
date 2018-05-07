---
title: Инструкция SELECT ограничения | Документы Microsoft
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
- ODBC SQL grammar, SELECT statement limitations
- SELECT statement limitations [ODBC]
ms.assetid: c6b05955-f8fd-4706-a1a7-a8dbd74870c2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00490256cb4da90fc9384f696435419266a1a3d3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="select-statement-limitations"></a>Ограничения инструкции SELECT
Столбец функция статистическое выражение нельзя использовать вместе с нестатистическим столбец в инструкции SELECT.  
  
 Список выбора инструкции SELECT с предложением GROUP BY может иметь только выражения из предложения GROUP BY или функции наборов.  
  
 Использование звездочки (для выбора всех столбцов) в инструкции SELECT, содержащая предложение GROUP BY не поддерживается. Необходимо указать имена столбцов для выбора.  
  
 Использование вертикальная черта в инструкции SELECT не поддерживается. Используйте параметр в инструкции SELECT, если вам потребуется обратиться к значению данных, содержащий вертикальной чертой.  
  
 При использовании псевдонима столбца в инструкции SELECT, слово «as» должно предшествовать псевдоним. Например «SELECT col1 как из б.» Без «как» инструкция возвращает ошибку.  
  
 Некорректное название столбца вводится в инструкции SELECT, SQLSTATE 07001, «Неверный номер из параметров» будет возвращена ошибка вместо ошибки SQLSTATE S0022, «столбец не найден».  
  
 При использовании драйвера Microsoft Excel, если пустая строка вставляется в столбец, пустая строка преобразуется в значение NULL; Искомая инструкции SELECT, который выполняется с пустой строкой в предложении WHERE не будет выполнено в этом столбце.
