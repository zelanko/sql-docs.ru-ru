---
title: "Возвращает значение SQL_NO_DATA | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 259ec0c9904501069036bdcadcbdad9d0a528d70
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="returning-sqlnodata"></a>Возвращает значение SQL_NO_DATA
Когда ODBC 2. *x* workingwith приложения ODBC 3*.x* драйвер вызывает **SQLExecDirect**, **SQLExecute**, или **SQLParamData**, и в которой выполняется поиск инструкция update или delete была выполнена, но не влияют на все строки в источнике данных ODBC 3*.x* драйвер должен возвращать значение SQL_SUCCESS. Когда ODBC 3*.x* приложения, работа с ODBC 3*.x* драйвер вызывает **SQLExecDirect**, **SQLExecute**, или  **SQLParamData** с тем же ODBC 3*.x* драйвер вернет значение SQL_NO_DATA.  
  
 Искомая инструкцией обновления или удаления в пакет инструкций не влияет на все строки в источнике данных **SQLMoreResults** возвращает SQL_SUCCESS. Он не может возвращать значение SQL_NO_DATA, так как это будет означать, что нет дополнительных результатов, не, что является результатом, из которой производится поиск update и delete, которые влиять ни одной строки.
