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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ed366acde11778342387d3bcb152a6619a6a3778
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138866"
---
# <a name="interoperability-of-sql-statements"></a>Совместимость инструкций SQL
Как и остальная часть приложения, инструкции SQL могут быть взаимодействующими или специфичными для СУБД. Как и в остальной части приложения, выбор способа взаимодействия инструкций SQL зависит от типа приложения. Менее вероятно, что пользовательские приложения используют взаимодействующие инструкции SQL, так как они обычно предназначены для использования возможностей одной или, возможно, двух СУБД. Универсальные приложения используют взаимодействующие инструкции SQL, так как они предназначены для работы с различными СУБД. И вертикальные приложения, как правило, находятся в промежутке между, требуя определенного уровня функциональности, но в противном случае с помощью взаимодействующих инструкций SQL.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Выбор грамматики SQL](../../../odbc/reference/develop-app/choosing-an-sql-grammar.md)  
  
-   [Построение инструкций SQL с поддержкой взаимодействия](../../../odbc/reference/develop-app/constructing-interoperable-sql-statements.md)
