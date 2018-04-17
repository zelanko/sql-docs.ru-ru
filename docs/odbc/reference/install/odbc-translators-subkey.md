---
title: Подраздел трансляторы ODBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- translator subkey [ODBC]
- subkeys [ODBC], translator subkey
- registry entries for components [ODBC], translator subkey
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ede16122078aa53d3eeb0799678537746e3fcf12
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
