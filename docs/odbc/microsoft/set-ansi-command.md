---
title: Командование SET ANSI (англ.) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300914"
---
# <a name="set-ansi-command"></a>Команда SET ANSI
Определяет, как сравниваются строки разной длины с оператором в командах Visual FoxPro S'L.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET ANSI ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 (По умолчанию для драйвера; по умолчанию для Visual FoxPro является OFF.) Колодки короче строки с пробелами, необходимых, чтобы сделать его равным длине строки. Затем две строки сравниваются с символом для персонажа на протяжении всей их длины. Рассмотрим это сравнение:  
  
```  
'Tommy' = 'Tom'  
```  
  
 Результат ложный (. F.), если SET ANSI на, потому что, когда мягкий, "Том" становится "Том" и строки "Том" и "Томми" не совпадают характер для характера.  
  
 Оператор использует этот метод для сравнения в командах Visual FoxPro S'L.  
  
 OFF  
 Упомяните, что более короткая строка не будет набиваться пробелами. Две строки сравниваются характер для символа до конца короче строки достигается. Рассмотрим это сравнение:  
  
```  
'Tommy' = 'Tom'  
```  
  
 Результат True (. Т.), когда SET ANSI выключен, потому что сравнение останавливается после "Томи".  
  
## <a name="remarks"></a>Remarks  
 SET ANSI определяет, является ли более короткая из двух строк набивкой пробелов при сравнении строк s'L. SET ANSI не влияет на оператора; при использовании оператора q, более короткая строка всегда набивается пробелами для сравнения.  
  
## <a name="string-order"></a>Порядок струнных  
 В командах СЗЛ слева направо из двух строк в сравнении не имеет значения переключение строки с одной стороны оператора на другую, не влияет на результат сравнения.  
  
## <a name="see-also"></a>См. также:  
 [SELECT - Командование СЗЛ](../../odbc/microsoft/select-sql-command.md)   
 [Команда SET EXACT](../../odbc/microsoft/set-exact-command.md)
