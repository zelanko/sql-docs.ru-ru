---
title: ЗНАЧЕНИЕ SQL_NO_DATA | Документы Microsoft
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
ms.topic: article
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- application upgrades [ODBC], SQL_NO_DATA
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
- upgrading applications [ODBC], SQL_NO_DATA
ms.assetid: 07a4144a-a548-4578-b2be-715c3cf73bf8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 48e50a556f5d1caa05170772d95a702d436d1722
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlnodata"></a>ЗНАЧЕНИЕ SQL_NO_DATA
Когда ODBC 3. *x* приложение вызывает **SQLExecDirect**, **SQLExecute**, или **SQLParamData** в ODBC 2. *x* драйвер на выполнение поисковое обновление или удаление инструкцию, которая не влияет на все строки в источнике данных, драйвер должен возвращать значение SQL_SUCCESS, а не значение SQL_NO_DATA. Когда ODBC 2. *x* или ODBC 3. *x* приложения, работа с ODBC 3. *x* драйвер вызывает **SQLExecDirect**, **SQLExecute**, или **SQLParamData** с тем же ODBC 3. *x* драйвер вернет значение SQL_NO_DATA.
