---
title: Источники данных ODBC подраздел | Документы Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23ca0ff3f499c23be9b46209d183a12e8ae92b25
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-data-sources-subkey"></a>Раздел источников данных ODBC
Значения в подразделе источники данных ODBC списка источников данных. Формат этих значений является, как показано в следующей таблице.  
  
|Название|Тип данных|Данные |  
|----------|---------------|----------|  
|*Имя источника данных*|REG_SZ|*Описание драйвера*|  
  
 *Имя источника данных* значение определяется программы администрирования (который обычно запрашивает пользователя для него), и *Описание драйвера* определяются разработчиком драйвера (обычно это имя СУБД связанные с драйвером).  
  
 Предположим, что были определены три источника данных: инвентаризации, который использует SQL Server; Расчет заработной платы, который использует dBASE; и службу, которая использует текстовые файлы. Значения в подразделе источники данных ODBC может выглядеть следующим образом:  
  
```  
Inventory : REG_SZ : SQL Server  
Payroll : REG_SZ : dBASE  
Personnel : REG_SZ : Text  
```
