---
title: SQL_NO_DATA Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9a399a270eb1cd2f3daf9449c53b1f577a6b9545
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299794"
---
# <a name="sql_no_data"></a>SQL_NO_DATA
Когда ODBC 3. *x* приложение вызывает **s'LExecDirect**, **S'L'LExecute**, или **S'LParamData** в ODBC 2. *x* драйвер для выполнения поискового обновления или удаления оператора, которое не влияет на строки в источнике данных, водитель должен вернуться SQL_SUCCESS, а не SQL_NO_DATA. Когда ODBC 2. *x* или ODBC 3. *x* приложение работает с ODBC 3. *x* драйвер вызывает **s'LExecDirect**, **S'L'LExecute**, или **S'LParamData** с тем же результатом, ODBC 3. *x* водитель должен вернуться SQL_NO_DATA.
