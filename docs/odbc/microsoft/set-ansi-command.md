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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 97269642b4147b966fdd71003f5f81ebe7905282
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300914"
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
