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
ms.openlocfilehash: 2a1d0c506c4a4b33d7138378032947821d4e9f3e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093994"
---
# <a name="odbc-data-sources-subkey"></a>Подраздел источников данных ODBC
Значения в столбце подраздел источников данных ODBC списка источников данных. Формат этих значений является, как показано в следующей таблице.  
  
|Name|Тип данных|Data|  
|----------|---------------|----------|  
|*Имя источника данных*|REG_SZ|*Описание драйвера*|  
  
 *Имя источника данных* значение определяется программой администрирования (который обычно предлагает пользователю для него), и *Описание драйвера* определяется разработчиком драйвер (обычно это имя СУБД связанные с драйвером).  
  
 Предположим, например, три определенных источников данных: Учет, который использует SQL Server; Платежных ведомостей, который использует dBASE; и персонала, которая использует формате текстовых файлов. Значения в столбце подраздел источников данных ODBC может выглядеть следующим образом:  
  
```  
Inventory : REG_SZ : SQL Server  
Payroll : REG_SZ : dBASE  
Personnel : REG_SZ : Text  
```
