---
title: Вызов процедуры | Документы Microsoft
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
- SQL grammar [ODBC], procedure invocation
- procedure invocation [ODBC]
ms.assetid: b9ff2c3a-2003-4832-adbe-08dd0f5ad948
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d01859ee1b44f29c1109e976cc4a59302306444
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="procedure-invocation"></a>Вызов процедуры
Когда используется драйвер Microsoft Access, процедуры могут вызываться из драйвера, с помощью **SQLExecDirect** или **SQLPrepare** функция со следующим синтаксисом: {ВЫЗОВИТЕ *имя процедуры*  [(*параметр*[,*параметр*]...)]}. Обратите внимание, что выражения не поддерживаются в качестве параметров для вызываемой процедуре.  
  
 Если имя процедуры содержит дефис, имя должны быть заключены в обратной кавычки (').  
  
 Параметризованный запрос может быть вызван с помощью предыдущей инструкции.
