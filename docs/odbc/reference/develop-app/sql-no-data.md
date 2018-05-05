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
ms.topic: conceptual
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
ms.openlocfilehash: 0166f1841d559758df70c7eef626e89b888f5904
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlnodata"></a>ЗНАЧЕНИЕ SQL_NO_DATA
Когда ODBC 3. *x* приложение вызывает **SQLExecDirect**, **SQLExecute**, или **SQLParamData** в ODBC 2. *x* драйвер на выполнение поисковое обновление или удаление инструкцию, которая не влияет на все строки в источнике данных, драйвер должен возвращать значение SQL_SUCCESS, а не значение SQL_NO_DATA. Когда ODBC 2. *x* или ODBC 3. *x* приложения, работа с ODBC 3. *x* драйвер вызывает **SQLExecDirect**, **SQLExecute**, или **SQLParamData** с тем же ODBC 3. *x* драйвер вернет значение SQL_NO_DATA.
