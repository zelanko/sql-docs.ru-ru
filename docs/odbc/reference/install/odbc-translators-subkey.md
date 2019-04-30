---
title: Подраздел ODBC-преобразователей | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translator subkey [ODBC]
- subkeys [ODBC], translator subkey
- registry entries for components [ODBC], translator subkey
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e7109a6f1b88cf7639b2fc823ce0c5f14d05002
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63280792"
---
# <a name="odbc-translators-subkey"></a>Подраздел ODBC-преобразователей
Значения в столбце подраздел ODBC-преобразователей список установленных переводчику. В следующей таблице показан формат из следующих значений.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|*Translator desc*|REG_SZ|**установлен**|  
  
 *Translator desc* имя определяется разработчиком translator.  
  
 Например предположим, что пользователь установил преобразователь Microsoft® кодовых страниц и пользовательских ASCII к EBCDIC translator. Значения в столбце подраздел ODBC-преобразователей может выглядеть следующим образом:  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
