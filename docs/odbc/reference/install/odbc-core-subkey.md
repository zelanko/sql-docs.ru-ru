---
title: "Основной раздел ODBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC], core subkey
- registry entries for components [ODBC], core subkey
- core subkey [ODBC]
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ad7a45f0f3272e1e2d7ae799ab1ca86bfb90b9be
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-core-subkey"></a>Подраздел основных компонентов ODBC
Значение в подразделе базовый ODBC предоставляет счетчик использования для основных компонентов (диспетчера драйверов, библиотека курсоров, установщика DLL и т. д.). В следующей таблице показан формат данного значения.  
  
|Имя|Тип данных|data|  
|----------|---------------|----------|  
|UsageCount|REG_DWORD|*count*|  
  
 Например предположим, что базовый ODBC компоненты будут установлены, программы установки для трех различных приложений и двумя различными драйверами. Значение в подразделе базовый ODBC будет иметь:  
  
```  
UsageCount : REG_DWORD : 0x5  
```

