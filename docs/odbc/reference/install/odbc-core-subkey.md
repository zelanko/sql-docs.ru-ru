---
title: Подключка ODBC Core (ru) Документы Майкрософт
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
ms.openlocfilehash: 9e6bfcf3c1efa87076e6d3e27a438cde6f794157
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304062"
---
# <a name="odbc-core-subkey"></a>Подраздел Core ODBC
Значение подключаемого ключа ODBC Core дает количество использования основных компонентов (Driver Manager, библиотека курсоров, установщик DLL и так далее). Формат этого значения отображается в следующей таблице.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|UsageCount|REG_DWORD|*count*|  
  
 Например, предположим, что компоненты ODBC Core были установлены программами настройки для трех различных приложений и двух разных драйверов. Значение подключаемого ключа ODBC Core будет:  
  
```  
UsageCount : REG_DWORD : 0x5  
```
