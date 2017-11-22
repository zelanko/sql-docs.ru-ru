---
title: "Вызов процедуры | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL grammar [ODBC], procedure invocation
- procedure invocation [ODBC]
ms.assetid: b9ff2c3a-2003-4832-adbe-08dd0f5ad948
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 793209ab716d720266e834fcbbb846dea56950ed
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="procedure-invocation"></a>Вызов процедуры
Когда используется драйвер Microsoft Access, процедуры могут вызываться из драйвера, с помощью **SQLExecDirect** или **SQLPrepare** функция со следующим синтаксисом: {ВЫЗОВИТЕ *имя процедуры*  [(*параметр*[,*параметр*]...)]}. Обратите внимание, что выражения не поддерживаются в качестве параметров для вызываемой процедуре.  
  
 Если имя процедуры содержит дефис, имя должны быть заключены в обратной кавычки (').  
  
 Параметризованный запрос может быть вызван с помощью предыдущей инструкции.
