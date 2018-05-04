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
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], core subkey
- registry entries for components [ODBC], core subkey
- core subkey [ODBC]
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf8e143a8d5d329fe3eb68185a3ebdf8f7f6cd6b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
