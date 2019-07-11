---
title: Вызов SQLSetPos для вставки данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], inserting data
- backward compatibility [ODBC], SqlSetPos
ms.assetid: 03e5c4d0-2bb3-4649-9781-89cab73f78eb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 86647601dfc0223dd6fa4f0ffcc0e5db695868b5
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793213"
---
# <a name="calling-sqlsetpos-to-insert-data"></a>Вызов SQLSetPos для вставки данных
Когда ODBC *2.x* приложение, которое работает с ODBC *3.x* драйвер вызывает **SQLSetPos** с *операции* аргумент SQL_ADD, Диспетчер драйверов не удается сопоставить этот вызов **SQLBulkOperations**. Если ODBC *3.x* драйвер должен работать с приложением, которое вызывает **SQLSetPos** с SQL_ADD, драйвер должен поддерживает эту операцию.  
  
 Одно из основных отличий в поведении при **SQLSetPos** вызове с параметром SQL_ADD возникает, когда он вызывается в состоянии S6. В ODBC *2.x*, драйвер возвратил S1010 при **SQLSetPos** был вызван с SQL_ADD в состоянии S6 (после Позиционирует курсор с **SQLFetch**). В ODBC *3.x*, **SQLBulkOperations** с *операции* из SQL_ADD может быть вызван в состоянии S6. Это вторая основная разница в поведении **SQLBulkOperations** с *операции* SQL_ADD может быть вызван в состоянии S5, тогда как **SQLSetPos** с  **Операция** из SQL_ADD невозможно. Для переходов инструкции, которые могут возникнуть для того же вызова в ODBC *3.x*, см. в разделе [приложении б: Таблицы перехода состояния ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).
