---
title: Основной раздел ODBC | Документы Microsoft
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
- subkeys [ODBC], core subkey
- registry entries for components [ODBC], core subkey
- core subkey [ODBC]
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 915c42e52c768a1b43a00b1a537a6885269f8a85
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="odbc-core-subkey"></a>Подраздел основных компонентов ODBC
Значение в подразделе базовый ODBC предоставляет счетчик использования для основных компонентов (диспетчера драйверов, библиотека курсоров, установщика DLL и т. д.). В следующей таблице показан формат данного значения.  
  
|Название|Тип данных|Данные |  
|----------|---------------|----------|  
|UsageCount|REG_DWORD|*count*|  
  
 Например предположим, что базовый ODBC компоненты будут установлены, программы установки для трех различных приложений и двумя различными драйверами. Значение в подразделе базовый ODBC будет иметь:  
  
```  
UsageCount : REG_DWORD : 0x5  
```
