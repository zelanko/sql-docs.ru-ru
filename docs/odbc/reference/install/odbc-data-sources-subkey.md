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
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bbe6d0e7e424f2bea8d90eb4e9c5993f50370848
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
