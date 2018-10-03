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
manager: craigg
ms.openlocfilehash: 5c95c4e28a5f32131307daeaa61e214af887b577
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47848142"
---
# <a name="odbc-core-subkey"></a>Подраздел Core ODBC
Значение в разделе подраздел ODBC Core предоставляет счетчик использования для основных компонентов (диспетчер драйверов, библиотека курсоров, библиотека DLL установщика и т. д.). В следующей таблице показан формат данного значения.  
  
|Имя|Тип данных|Данные |  
|----------|---------------|----------|  
|UsageCount|REG_DWORD|*count*|  
  
 Например предположим, что были установлены программами установки для трех разных приложений и двумя различными драйверами ODBC основных компонентов. Значение в разделе подраздел ODBC Core будет:  
  
```  
UsageCount : REG_DWORD : 0x5  
```
