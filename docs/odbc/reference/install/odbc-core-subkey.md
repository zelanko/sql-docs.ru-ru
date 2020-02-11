---
title: Подраздел ODBC Core | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094011"
---
# <a name="odbc-core-subkey"></a>Подраздел Core ODBC
Значение в подразделе ODBC Core позволяет получить счетчик использования основных компонентов (диспетчер драйверов, Библиотека курсоров, DLL установщика и т. д.). Формат этого значения показан в следующей таблице.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|усажекаунт|REG_DWORD|*count*|  
  
 Например, предположим, что компоненты ODBC Core были установлены программами установки для трех различных приложений и двух различных драйверов. Значение в подразделе раздела ODBC Core будет следующим:  
  
```  
UsageCount : REG_DWORD : 0x5  
```
