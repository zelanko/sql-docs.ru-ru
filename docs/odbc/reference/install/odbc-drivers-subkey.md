---
title: Подраздел драйверы ODBC | Документы Microsoft
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
- subkeys [ODBC], drivers subkey
- registry entries for components [ODBC], drivers subkey
- drivers subkey [ODBC]
ms.assetid: 8edbf68f-d05d-4d77-92f6-e9500008f520
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 17e0a418957aa4413d0fd7d02ebdc0243596d013
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-drivers-subkey"></a>Подраздел драйверы ODBC
Значения в подразделе драйверы ODBC списка установленных драйверов. В следующей таблице показан формат этих значений.  
  
|Название|Тип данных|Данные |  
|----------|---------------|----------|  
|*Описание драйвера*|REG_SZ|**Установлен**|  
  
 *Описание драйвера* имя определяется разработчиком драйвера. Обычно это имя СУБД, связанные с драйвером.  
  
 Например предположим, что были установлены драйверы для файлов форматированный текст и SQL Server. Значения в подразделе драйверы ODBC могут быть:  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
