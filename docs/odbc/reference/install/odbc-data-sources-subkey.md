---
title: Источники данных ODBC подраздел | Документы Microsoft
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
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e81fe6cc77d92a8fde7530c1f79381025a05856b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915469"
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
