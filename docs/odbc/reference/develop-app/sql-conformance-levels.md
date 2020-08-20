---
description: Уровни соответствия SQL
title: Уровни соответствия SQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 3529df2c-a09b-4c16-9c60-eae7a06d903a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 525cda9094213e6decf30643c23a7db623511e14
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499807"
---
# <a name="sql-conformance-levels"></a>Уровни соответствия SQL
Уровень грамматики SQL-92, поддерживаемый драйвером, определяется значением, возвращаемым вызовом **SQLGetInfo** с типом сведений SQL_SQL_CONFORMANCE. Указывает, соответствует ли драйвер записи, переходного, промежуточного или полного уровня FIPS, определенных в SQL-92.  
  
 Все драйверы ODBC должны поддерживать минимальную грамматику SQL, описанную в разделе [Минимальная грамматика SQL](../../../odbc/reference/appendixes/sql-minimum-grammar.md) в приложении C: грамматика SQL. Эта грамматика является подмножеством начального уровня для SQL-92. Драйверы могут поддерживать дополнительный код SQL и соответствовать записи SQL-92, промежуточному или полному уровню, а также уровню FIPS 127-2 Transitional. Драйверы, соответствующие заданному уровню SQL-92 или FIPS 127-2, могут поддерживать дополнительные функции на любом из более высоких уровней, но не полностью совместимы с этим уровнем. Чтобы определить, поддерживается ли функция, приложение должно вызвать **SQLGetInfo** с соответствующим типом данных. Уровень соответствия функции SQL описан в соответствующем типе данных. (См. Описание функции [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) .)
