---
title: Вызов SQLCloseCursor | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], SQLCloseCursor
- backward compatibility [ODBC], SqlCloseCursor
- SQLCloseCursor function [ODBC], calling
- upgrading applications [ODBC], SQLCloseCursor
- compatibility [ODBC], SQLCloseCursor
ms.assetid: ef448c39-a9ad-4f07-8ef3-65bd4cef672a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d574729d7fa49a65b26e067c54a0af459a36094
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="calling-sqlclosecursor"></a>Вызов SQLCloseCursor
Поскольку **SQLCloseCursor** практически совпадает **SQLFreeStmt** с SQL_CLOSE, диспетчер драйверов не соответствует этой функции. Функции замены сопоставлены, чтобы существующие ODBC 2 *.x* приложения можно легко переместить в ODBC 3. *x* с помощью новых функций. Это решение упрощает для таких приложений начать использовать новые ODBC 3. *x* функциональность внутри условного кода в модульном варианте. **SQLCloseCursor** не представляет никаких новых функциональных возможностей. Приложения не смогут получить все преимущества, переместив **SQLCloseCursor** из **SQLFreeStmt** с SQL_CLOSE.
