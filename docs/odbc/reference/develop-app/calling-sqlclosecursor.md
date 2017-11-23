---
title: "Вызов SQLCloseCursor | Документы Microsoft"
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
- application upgrades [ODBC], SQLCloseCursor
- backward compatibility [ODBC], SqlCloseCursor
- SQLCloseCursor function [ODBC], calling
- upgrading applications [ODBC], SQLCloseCursor
- compatibility [ODBC], SQLCloseCursor
ms.assetid: ef448c39-a9ad-4f07-8ef3-65bd4cef672a
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e70b98086732cbbcf1ab8f2f8a4bbbbf9795c84f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="calling-sqlclosecursor"></a>Вызов SQLCloseCursor
Поскольку **SQLCloseCursor** практически совпадает **SQLFreeStmt** с SQL_CLOSE, диспетчер драйверов не соответствует этой функции. Функции замены сопоставлены, чтобы существующие ODBC 2*.x* приложения можно легко переместить в ODBC 3. *x* с помощью новых функций. Это решение упрощает для таких приложений начать использовать новые ODBC 3. *x* функциональность внутри условного кода в модульном варианте. **SQLCloseCursor** не представляет никаких новых функциональных возможностей. Приложения не смогут получить все преимущества, переместив **SQLCloseCursor** из **SQLFreeStmt** с SQL_CLOSE.
