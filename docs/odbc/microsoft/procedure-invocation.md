---
title: Вызов процедуры | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL grammar [ODBC], procedure invocation
- procedure invocation [ODBC]
ms.assetid: b9ff2c3a-2003-4832-adbe-08dd0f5ad948
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6eb0abafb72b0acd9424a31205771c91edbc5529
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32900840"
---
# <a name="procedure-invocation"></a>Вызов процедуры
Когда используется драйвер Microsoft Access, процедуры могут вызываться из драйвера, с помощью **SQLExecDirect** или **SQLPrepare** функция со следующим синтаксисом: {ВЫЗОВИТЕ *имя процедуры*  [(*параметр*[,*параметр*]...)]}. Обратите внимание, что выражения не поддерживаются в качестве параметров для вызываемой процедуре.  
  
 Если имя процедуры содержит дефис, имя должны быть заключены в обратной кавычки (').  
  
 Параметризованный запрос может быть вызван с помощью предыдущей инструкции.
