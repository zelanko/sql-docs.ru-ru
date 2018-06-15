---
title: Уровни согласованности SQL | Документы Microsoft
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
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 3529df2c-a09b-4c16-9c60-eae7a06d903a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dcdb0f98d7260985e418a6eaeb670c40409c518d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32913299"
---
# <a name="sql-conformance-levels"></a>Уровни согласованности SQL
Указывает значение, возвращаемое вызовом уровень грамматику SQL-92, поддерживаемых драйвером **SQLGetInfo** с типом SQL_SQL_CONFORMANCE сведения. Указывает, соответствует ли драйвер уровни записи, переходном состоянии FIPS, промежуточного или Full, определенные в SQL-92.  
  
 Все драйверы ODBC должны поддерживать минимальную грамматику SQL, описанной в [минимальную грамматику SQL](../../../odbc/reference/appendixes/sql-minimum-grammar.md) в грамматику SQL приложение C:. Этой грамматике является подмножеством начального уровня для SQL-92. Драйверы может поддерживать дополнительные SQL и обеспечения соответствия уровень SQL-92 начального, промежуточного или Full или FIPS 127-2 промежуточном уровне. Драйверы, соответствующие стандарту SQL-92 или FIPS 127-2 данного уровня может поддерживать дополнительные возможности во всех более высоких уровнях но не полностью соответствует стандарту этого уровня. Чтобы определить, поддерживается ли функция, приложение должно вызывать **SQLGetInfo** с типом соответствующие сведения. Уровень соответствия функции SQL описан в соответствующий тип данных. (См. [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) описание функции.)
