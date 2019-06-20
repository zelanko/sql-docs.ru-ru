---
title: Подразделы спецификаций преобразователей | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: a3c5ad31437cf2639d6b8478d173c7522fa3e9fb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63272942"
---
# <a name="translator-specification-subkeys"></a>Подразделы спецификаций преобразователей
Каждого из них перечислены в подраздел ODBC-преобразователей содержит подраздел свои собственные. Этот подраздел содержит имя, совпадающее с именем соответствующего значения в подразделе переводчиков ODBC. Значения в этом подразделе перечислены полные пути переводчик и библиотеках установки translator и счетчик использования. Как показано в следующей таблице, используются форматы значений.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|Translator|REG_SZ|*путь к библиотеке DLL перевода*|  
|Установка|REG_SZ|*путь к библиотеке DLL программы установки*|  
|UsageCount|REG_DWORD|*count*|  
  
 Сведения о счетчиках использования см. в разделе [подсчет использования](../../../odbc/reference/install/usage-counting.md) ранее в этом разделе.  
  
 Приложения, не задавайте счетчик использования. ODBC будет поддерживать этот счетчик.  
  
 Например предположим, имеется перевод DLL с именем Mscpxl32.dll, который переводчик функции программы установки находятся в той же библиотеки DLL, код страницы Microsoft Translator и что переводчик установлено три раза. Значения в подразделе Microsoft Translator страницы кода может выглядеть следующим образом:  
  
```  
Translator : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
UsageCount : REG_DWORD : 0x3  
```
