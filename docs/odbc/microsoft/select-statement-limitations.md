---
title: Ограничения на выписку SELECT Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d91e93076a67287cbbd2b64b2ad0d6414a0aea6d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300924"
---
# <a name="select-statement-limitations"></a>Ограничения инструкции SELECT
Столбец агрегированной функции не может быть смешан с неагрегированным столбиком в отчете SELECT.  
  
 В выбранном списке оператора SELECT, в котором есть оговорка GROUP BY, могут быть только выражения из положения GROUP BY или установленные функции.  
  
 Использование звездочки (для выбора всех столбцов) в заявлении SELECT, содержащем оговорку GROUP BY, не поддерживается. Имена выбранных столбцов должны быть указаны.  
  
 Использование вертикальной панели в заявлении SELECT не поддерживается. Используйте параметр в выписке SELECT, если необходимо сослаться на значение данных, содержащее вертикальную панель.  
  
 При использовании псевдонима столбца в заявлении SELECT слово «как» должно предшествовать псевдониму. Например, "SELECT col1 как от b." Без "as", заявление вернет ошибку.  
  
 Если неправильное имя столбца вводится в выписку SELECT, то вместо ошибки S'LSTATE S0022 возвращается ошибка S'Lstate S0022, "Не найдена столбец".  
  
 При использовании драйвера Microsoft Excel, если пустая строка вставляется в столбец, пустая строка преобразуется в NULL; Выгнанная операторка SELECT, выполняемый пустой строкой в пункте WHERE, не будет успешной в этом столбе.
