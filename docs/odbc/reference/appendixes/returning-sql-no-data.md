---
title: "Возвращает значение SQL_NO_DATA | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5539f9d2951913163ac6011695709e3664d8acb1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="returning-sqlnodata"></a>Возвращает значение SQL_NO_DATA
Когда ODBC 2. *x* workingwith приложения ODBC 3*.x* драйвер вызывает **SQLExecDirect**, **SQLExecute**, или **SQLParamData**, и в которой выполняется поиск инструкция update или delete была выполнена, но не влияют на все строки в источнике данных ODBC 3*.x* драйвер должен возвращать значение SQL_SUCCESS. Когда ODBC 3*.x* приложения, работа с ODBC 3*.x* драйвер вызывает **SQLExecDirect**, **SQLExecute**, или ** SQLParamData** с тем же ODBC 3*.x* драйвер вернет значение SQL_NO_DATA.  
  
 Искомая инструкцией обновления или удаления в пакет инструкций не влияет на все строки в источнике данных **SQLMoreResults** возвращает SQL_SUCCESS. Он не может возвращать значение SQL_NO_DATA, так как это будет означать, что нет дополнительных результатов, не, что является результатом, из которой производится поиск update и delete, которые влиять ни одной строки.
