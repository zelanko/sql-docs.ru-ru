---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2e8ce5aeeb94a4f7a33b22054adc8067e0654ac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62690209"
---
# <a name="sql-conformance-levels"></a>Уровни соответствия SQL
Указывает значение, возвращаемое вызовом уровне грамматики SQL-92, поддерживаемых драйвером **SQLGetInfo** с типом SQL_SQL_CONFORMANCE сведения. Это указывает, соответствует ли драйвер уровни записи, FIPS Transitional, промежуточного или Full, определенные в SQL-92.  
  
 Все драйверы ODBC должны поддерживать минимальную грамматику SQL, описанных в [Минимальная Грамматика SQL](../../../odbc/reference/appendixes/sql-minimum-grammar.md) в приложение в: Грамматика SQL. Это является подмножеством начального уровня, из SQL-92. Драйверы может поддерживать дополнительные SQL и обеспечения соответствия уровень записи SQL-92, промежуточных или Full или FIPS 127-2 уровня переходном состоянии. Драйверы, соответствующие стандарту данный уровень SQL-92 или FIPS 127-2 может обеспечить поддержку дополнительных возможностей в любом из более высоких уровнях но не полностью соответствует стандарту этого уровня. Чтобы определить, поддерживается ли функция, приложение должно вызывать **SQLGetInfo** с типом соответствующую информацию. Уровень соответствия SQL функции описан в соответствующий тип данных. (См. в разделе [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) описание функции.)
