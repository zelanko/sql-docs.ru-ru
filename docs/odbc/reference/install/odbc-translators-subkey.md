---
title: Подраздел трансляторы ODBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- translator subkey [ODBC]
- subkeys [ODBC], translator subkey
- registry entries for components [ODBC], translator subkey
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 03c6174d69fbe7a891e35e61a208b81bdb9cc4a2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915099"
---
# <a name="odbc-translators-subkey"></a>Подраздел трансляторы ODBC
Значения в подразделе трансляторы ODBC список установленных трансляторы. В следующей таблице показан формат этих значений.  
  
|Название|Тип данных|Данные |  
|----------|---------------|----------|  
|*транслятор desc*|REG_SZ|**Установлен**|  
  
 *Переводчик desc* имя определяется разработчиком преобразователя.  
  
 Например предположим, что пользователь установил на переводчик EBCDIC преобразователь Microsoft® кодовых страниц и пользовательских ASCII. Значения в подразделе трансляторы ODBC может выглядеть следующим образом:  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
