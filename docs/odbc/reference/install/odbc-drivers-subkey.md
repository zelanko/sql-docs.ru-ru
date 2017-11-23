---
title: "Подраздел драйверы ODBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC], drivers subkey
- registry entries for components [ODBC], drivers subkey
- drivers subkey [ODBC]
ms.assetid: 8edbf68f-d05d-4d77-92f6-e9500008f520
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 756f1f145d7e9a8ea5698366af920cce13041dd2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="odbc-drivers-subkey"></a>Подраздел драйверы ODBC
Значения в подразделе драйверы ODBC списка установленных драйверов. В следующей таблице показан формат этих значений.  
  
|Имя|Тип данных|data|  
|----------|---------------|----------|  
|*Описание драйвера*|REG_SZ|**Установлен**|  
  
 *Описание драйвера* имя определяется разработчиком драйвера. Обычно это имя СУБД, связанные с драйвером.  
  
 Например предположим, что были установлены драйверы для файлов форматированный текст и SQL Server. Значения в подразделе драйверы ODBC могут быть:  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
