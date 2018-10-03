---
title: Вызов SQLCloseCursor | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], SQLCloseCursor
- backward compatibility [ODBC], SqlCloseCursor
- SQLCloseCursor function [ODBC], calling
- upgrading applications [ODBC], SQLCloseCursor
- compatibility [ODBC], SQLCloseCursor
ms.assetid: ef448c39-a9ad-4f07-8ef3-65bd4cef672a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7ee139dd652204c750c99d8bad8ab2b17c7c1ba1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47685962"
---
# <a name="calling-sqlclosecursor"></a>Вызов SQLCloseCursor
Так как **SQLCloseCursor** практически не отличается от как **SQLFreeStmt** с SQL_CLOSE, диспетчер драйверов не соответствует этой функции. Функции замены сопоставляются таким образом, чтобы существующие ODBC 2 *.x* приложений можно легко переместить в ODBC 3. *x* с помощью новых функций. Это решение упрощает для таких приложений начать работу с новой ODBC 3. *x* функции внутри условного кода в модульном варианте. **SQLCloseCursor** не представляет никаких новых функциональных возможностей. Приложения не смогут получить все преимущества, переместив **SQLCloseCursor** из **SQLFreeStmt** с SQL_CLOSE.
