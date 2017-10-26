---
title: "Транслятор спецификации подразделов | Документы Microsoft"
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
- translator subkey [ODBC]
- registry entries for components [ODBC], translator specification subkeys
- translator specification subkeys [ODBC]
- subkeys [ODBC], translator specification subkeys
ms.assetid: 3c0edeee-d43a-4466-a177-bf2d2435707a
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 62bfe54f5bd5117fee5d9ba063f1882be47ccbc4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="translator-specification-subkeys"></a>Транслятор спецификации подразделов
Каждого из них перечислены в подразделе трансляторы ODBC имеется подраздел свои собственные. Этот подраздел содержит имя, совпадающее с именем соответствующего значения в подразделе трансляторы ODBC. Значения в этом подразделе перечислены полные пути преобразователь и настройки транслятора библиотек DLL и счетчик использования. Форматы значений, как показано в следующей таблице.  
  
|Имя|Тип данных|data|  
|----------|---------------|----------|  
|Translator|REG_SZ|*путь к библиотеке DLL переводчик*|  
|Программа установки|REG_SZ|*путь к библиотеке DLL установки*|  
|UsageCount|REG_DWORD|*count*|  
  
 Сведения о счетчиках использования см. в разделе [об использовании инвентаризации](../../../odbc/reference/install/usage-counting.md) ранее в этом разделе.  
  
 Приложение не может установить счетчик использования. ODBC поддерживает это число.  
  
 Например предположим, преобразователь кодовых страниц Microsoft имеет перевод DLL с именем Mscpxl32.dll, который преобразователь функции установки находятся в той же библиотеки DLL, и что преобразователь был установлен три раза. Значения в подразделе преобразователь кодовых страниц Microsoft может выглядеть следующим образом:  
  
```  
Translator : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
UsageCount : REG_DWORD : 0x3  
```

