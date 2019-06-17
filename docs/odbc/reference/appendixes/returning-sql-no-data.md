---
title: Возврат SQL_NO_DATA | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 74c122819980abaa328db5ad46f240cae24b92d3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63280592"
---
# <a name="returning-sqlnodata"></a>Возврат SQL_NO_DATA
Когда ODBC 2. *x* workingwith приложения ODBC 3 *.x* драйвер вызывает **SQLExecDirect**, **SQLExecute**, или **SQLParamData**, и поисковое обновление или инструкции delete был выполнен, но не влияют на все строки в источнике данных, а ODBC 3 *.x* драйвер должен возвращать значение SQL_SUCCESS. Когда ODBC 3 *.x* приложение, которое работает с ODBC 3 *.x* драйвер вызывает **SQLExecDirect**, **SQLExecute**, или  **SQLParamData** с тем же ODBC 3 *.x* драйвер вернет значение SQL_NO_DATA.  
  
 Искомая инструкция update или delete в пакет инструкций не влияет на все строки в источнике данных, **SQLMoreResults** возвращает значение SQL_SUCCESS. Он не может возвращать значение SQL_NO_DATA, так как это будет означать, что нет больше результатов, не, что является результатом из поисковое обновление, удаление, затрагиваются ни одной строки.
