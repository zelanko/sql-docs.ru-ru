---
title: Подразделы спецификации переводчика | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translator subkey [ODBC]
- registry entries for components [ODBC], translator specification subkeys
- translator specification subkeys [ODBC]
- subkeys [ODBC], translator specification subkeys
ms.assetid: 3c0edeee-d43a-4466-a177-bf2d2435707a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ec94f3e02b720617e8f7369b12a916c2bbbe7b16
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093799"
---
# <a name="translator-specification-subkeys"></a>Подразделы спецификаций преобразователей
Каждый транслятор, указанный в подразделе "трансляторы ODBC", имеет собственный подраздел. Этот подраздел имеет то же имя, что и соответствующее значение в подразделе "трансляторы ODBC". В параметрах этого подраздела перечислены полные пути к библиотекам DLL установки переводчиков и переводчиков, а также счетчик использования. Форматы значений представлены в следующей таблице.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|API перевода|REG_SZ|*Translator-DLL-путь*|  
|Установка|REG_SZ|*Setup-DLL-путь*|  
|усажекаунт|REG_DWORD|*count*|  
  
 Дополнительные сведения о счетчиках использования см. в разделе [Использование подсчета использования](../../../odbc/reference/install/usage-counting.md) ранее.  
  
 Приложения не должны устанавливать счетчик использования. Этот счетчик будет поддерживаться в ODBC.  
  
 Например, предположим, что у транслятора кодовых страниц Microsoft есть библиотека DLL для перевода с именем Mscpxl32. dll, что функции установки переводчика находятся в одной и той же библиотеке DLL, и что переводчик был установлен три раза. Значения в подразделе преобразователь кодовых страниц Microsoft могут выглядеть следующим образом:  
  
```  
Translator : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
UsageCount : REG_DWORD : 0x3  
```
