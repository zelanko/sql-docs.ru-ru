---
title: ЗНАЧЕНИЕ SQL_NO_DATA | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- application upgrades [ODBC], SQL_NO_DATA
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
- upgrading applications [ODBC], SQL_NO_DATA
ms.assetid: 07a4144a-a548-4578-b2be-715c3cf73bf8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 749351694a41764b9b5cc8bf3421340d62626aaf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62445966"
---
# <a name="sqlnodata"></a>SQL_NO_DATA
Когда ODBC 3. *x* приложение вызывает **SQLExecDirect**, **SQLExecute**, или **SQLParamData** в ODBC 2. *x* драйвер выполнить поисковое обновление или удалить инструкцию, которая не влияет на все строки в источнике данных, драйвер должен возвращать значение SQL_SUCCESS, а не значение SQL_NO_DATA. Когда ODBC 2. *x* или ODBC 3. *x* приложение, которое работает с ODBC 3. *x* драйвер вызывает **SQLExecDirect**, **SQLExecute**, или **SQLParamData** с тем же ODBC 3. *x* драйвер вернет значение SQL_NO_DATA.
