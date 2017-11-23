---
title: "Привязка столбцов | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: c4407694-c8e1-4b0b-a39d-b007e6c3b54d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 072ca1b754159efbd117f4530f458caf8fb40c0d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="binding-columns"></a>Привязка столбцов
Данные, полученные из источника данных возвращается в приложение в переменных, которые приложения, выделенной для этой цели. Прежде чем это можно сделать, необходимо связать приложение, или *привязки*, эти переменные со столбцами результирующего набора; по существу, этот процесс является таким же, как привязка переменных приложения с параметрами инструкции. Если приложение связывает переменную, чтобы столбец результирующего набора, он описывает этой переменной — адрес, тип данных и так далее — к драйверу. Драйвер сохраняет эти сведения в структуре, он поддерживает для этого оператора и использует сведения, чтобы возвращать значение из столбца при выборке строки.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Привязка столбцов результирующего набора](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Использование SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
