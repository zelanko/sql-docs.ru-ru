---
title: "Подраздел трансляторы ODBC | Документы Microsoft"
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
- subkeys [ODBC], translator subkey
- registry entries for components [ODBC], translator subkey
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dfc34daa6236fa7187c27a204ee16cc47a0de7b0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-translators-subkey"></a>Подраздел трансляторы ODBC
Значения в подразделе трансляторы ODBC список установленных трансляторы. В следующей таблице показан формат этих значений.  
  
|Имя|Тип данных|data|  
|----------|---------------|----------|  
|*транслятор desc*|REG_SZ|**Установлен**|  
  
 *Переводчик desc* имя определяется разработчиком преобразователя.  
  
 Например предположим, что пользователь установил на переводчик EBCDIC преобразователь Microsoft® кодовых страниц и пользовательских ASCII. Значения в подразделе трансляторы ODBC может выглядеть следующим образом:  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```

