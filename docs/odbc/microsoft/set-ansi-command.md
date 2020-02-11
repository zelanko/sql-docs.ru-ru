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
ms.openlocfilehash: d32e4dc27568b37f273ef654ebd45d26ca23e555
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67997764"
---
# <a name="set-ansi-command"></a>Команда SET ANSI
Определяет, как выполняется сравнение строк разной длины с помощью оператора = в командах SQL Visual FoxPro.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET ANSI ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 (Значение по умолчанию для драйвера; значение по умолчанию для Visual FoxPro — OFF.) Дополняет более короткую строку пробелами, чтобы сделать ее длинной длиной строки. Затем две строки сравниваются по символам для всей длины. Рассмотрите следующее сравнение:  
  
```  
'Tommy' = 'Tom'  
```  
  
 Результат равен false (. Е), если параметр SET ANSI имеет значение ON, так как при заполнении "Tom" становится "Tom", а строки "Tom" и "Антон" не соответствуют символу для символа.  
  
 Оператор = = использует этот метод для сравнения в командах SQL Visual FoxPro.  
  
 OFF  
 Указывает, что более короткая строка не дополняются пробелами. Две строки являются сравниваемыми символом для символа до тех пор, пока не будет достигнут конец укороченной строки. Рассмотрите следующее сравнение:  
  
```  
'Tommy' = 'Tom'  
```  
  
 Результат равен true (. T.), если параметр SET ANSI имеет значение OFF, так как сравнение останавливается после "Tom".  
  
## <a name="remarks"></a>Remarks  
 SET ANSI определяет, будет ли укороченная строка из двух строк дополнена пробелами при сравнении строк SQL. SET ANSI не влияет на оператор = =; При использовании оператора = = более короткая строка всегда дополняется пробелами для сравнения.  
  
## <a name="string-order"></a>Порядок строк  
 В командах SQL порядок следования двух строк в сравнении слева направо иррелевантсвитчинг строки с одной стороны от оператора = или = = на другой не влияет на результат сравнения.  
  
## <a name="see-also"></a>См. также:  
 [Команда SELECT-SQL](../../odbc/microsoft/select-sql-command.md)   
 [Команда SET EXACT](../../odbc/microsoft/set-exact-command.md)
