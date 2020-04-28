---
title: Взаимодействие инструкций SQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC]
- interoperability of SQL statements [ODBC], about interoperability
ms.assetid: 3b24c499-829c-4e65-90cf-a3a0f6d0a186
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d3d7a76c67096d2e76fe1cd3d4b15f73122699e7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302805"
---
# <a name="interoperability-of-sql-statements"></a>Совместимость инструкций SQL
Как и остальная часть приложения, инструкции SQL могут быть взаимодействующими или специфичными для СУБД. Как и в остальной части приложения, выбор способа взаимодействия инструкций SQL зависит от типа приложения. Менее вероятно, что пользовательские приложения используют взаимодействующие инструкции SQL, так как они обычно предназначены для использования возможностей одной или, возможно, двух СУБД. Универсальные приложения используют взаимодействующие инструкции SQL, так как они предназначены для работы с различными СУБД. И вертикальные приложения, как правило, находятся в промежутке между, требуя определенного уровня функциональности, но в противном случае с помощью взаимодействующих инструкций SQL.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Выбор грамматики SQL](../../../odbc/reference/develop-app/choosing-an-sql-grammar.md)  
  
-   [Построение инструкций SQL с поддержкой взаимодействия](../../../odbc/reference/develop-app/constructing-interoperable-sql-statements.md)
