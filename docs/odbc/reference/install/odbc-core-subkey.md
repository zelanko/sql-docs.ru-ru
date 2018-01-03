---
title: "Основной раздел ODBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC], core subkey
- registry entries for components [ODBC], core subkey
- core subkey [ODBC]
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9331aa39d5df84cc5269fb995c594df9cd08e27f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
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
