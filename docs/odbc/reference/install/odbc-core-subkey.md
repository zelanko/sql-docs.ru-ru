---
description: Подраздел Core ODBC
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 37948c46d6a717975902bc2109ece2aea02b0129
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499739"
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
