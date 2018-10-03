---
title: Подраздел источники данных ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9867946ce84163a504582c8a9575100c3c9aacd3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600872"
---
# <a name="odbc-data-sources-subkey"></a>Подраздел источников данных ODBC
Значения в столбце подраздел источников данных ODBC списка источников данных. Формат этих значений является, как показано в следующей таблице.  
  
|Имя|Тип данных|Данные |  
|----------|---------------|----------|  
|*Имя источника данных*|REG_SZ|*Описание драйвера*|  
  
 *Имя источника данных* значение определяется программой администрирования (который обычно предлагает пользователю для него), и *Описание драйвера* определяется разработчиком драйвер (обычно это имя СУБД связанные с драйвером).  
  
 Например, предположим, что были определены три источника данных: инвентаризации, который использует SQL Server; Платежных ведомостей, который использует dBASE; и персонала, которая использует формате текстовых файлов. Значения в столбце подраздел источников данных ODBC может выглядеть следующим образом:  
  
```  
Inventory : REG_SZ : SQL Server  
Payroll : REG_SZ : dBASE  
Personnel : REG_SZ : Text  
```
