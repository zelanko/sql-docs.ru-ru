---
title: Команда SET ANSI | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set ANSI command [ODBC]
ms.assetid: cf9a01b2-14bf-458c-a73c-2a58ddef32d8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5af98bd8f16d7278b932ad89f1c81c58ddb1fb54
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63127867"
---
# <a name="set-ansi-command"></a>Команда SET ANSI
Определяет способ между строки разной длины сравнения с =-оператор в командах Visual FoxPro SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET ANSI ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 (По умолчанию для драйвера по умолчанию для Visual FoxPro имеет значение OFF.) Более короткая строка с пустые значения, необходимые для панелей сделать его равным тем дольше длину. Две строки, затем последовательно по сравнению с символ для символа для их всего длины. Рассмотрим это сравнение.  
  
```  
'Tommy' = 'Tom'  
```  
  
 Результат равен False (. Е.) Если SET ANSI, потому, что при заполнении «Tom» становится «Том» и строки «Том» и «Антон» не соответствует символ для символа.  
  
 == Оператор использует этот метод для сравнения в команды Visual FoxPro SQL.  
  
 OFF  
 Указывает, что более короткая строка не быть дополняются пробелами. Сравниваются две строки символ для символа, пока не будет достигнут конец более короткая строка. Рассмотрим это сравнение.  
  
```  
'Tommy' = 'Tom'  
```  
  
 Результатом является значение True (. Если SET ANSI отключен, так как T.) процедура сравнения останавливается после «Том».  
  
## <a name="remarks"></a>Примечания  
 SET ANSI определяет ли короткий из двух строк дополняется пробелы при сравнении строк SQL. SET ANSI не оказывает влияния на ==-оператор; При использовании оператора ==, всегда более короткая строка дополняется пробелами для сравнения.  
  
## <a name="string-order"></a>Порядок в строке  
 Команд SQL, слева направо порядок двух строк при сравнении не irrelevantswitching строку с одной стороны = или == оператора в другую не влияет на результат сравнения.  
  
## <a name="see-also"></a>См. также  
 [SELECT — команда SQL](../../odbc/microsoft/select-sql-command.md)   
 [Команда SET EXACT](../../odbc/microsoft/set-exact-command.md)
