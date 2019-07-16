---
title: Подраздел Core ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], core subkey
- registry entries for components [ODBC], core subkey
- core subkey [ODBC]
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 98c9380083eb5a0ad796f436af271564676b757d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094011"
---
# <a name="odbc-core-subkey"></a>Подраздел Core ODBC
Значение в разделе подраздел ODBC Core предоставляет счетчик использования для основных компонентов (диспетчер драйверов, библиотека курсоров, библиотека DLL установщика и т. д.). В следующей таблице показан формат данного значения.  
  
|Name|Тип данных|Data|  
|----------|---------------|----------|  
|UsageCount|REG_DWORD|*count*|  
  
 Например предположим, что были установлены программами установки для трех разных приложений и двумя различными драйверами ODBC основных компонентов. Значение в разделе подраздел ODBC Core будет:  
  
```  
UsageCount : REG_DWORD : 0x5  
```
