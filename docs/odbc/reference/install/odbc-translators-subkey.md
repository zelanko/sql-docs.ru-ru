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
ms.openlocfilehash: 7d26f2d33d81e08cfe4bddff9b2260bd2f098f00
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093945"
---
# <a name="odbc-translators-subkey"></a>Подраздел ODBC-преобразователей
Значения в столбце подраздел ODBC-преобразователей список установленных переводчику. В следующей таблице показан формат из следующих значений.  
  
|Имя|Тип данных|Data|  
|----------|---------------|----------|  
|*Translator desc*|REG_SZ|**установлен**|  
  
 *Translator desc* имя определяется разработчиком translator.  
  
 Например предположим, что пользователь установил преобразователь Microsoft® кодовых страниц и пользовательских ASCII к EBCDIC translator. Значения в столбце подраздел ODBC-преобразователей может выглядеть следующим образом:  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
