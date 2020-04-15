---
title: Вызов S'LCloseCursor Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2feab58de28e39747a1d9c819f9f15426b156151
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306277"
---
# <a name="calling-sqlclosecursor"></a>Вызов SQLCloseCursor
Поскольку с SQL_CLOSE **менеджер** драйверов не отображает эту функцию, так же, как и **s'LFreeStmt.** Функции замены отображаются таким образом, что существующие приложения ODBC *2.x* могут легко перейти на ODBC *3.x* с помощью новых функций. Такой шаг упрощает использование новых функций ODBC *3.x* внутри условного кода модульным способом. **СЗЛКЛОККурсор** не представляет никакой новой функциональности. Приложение не получает никаких преимуществ, перейдя на **s'LCloseCursor** из **S'LFreeStmt** с SQL_CLOSE.
