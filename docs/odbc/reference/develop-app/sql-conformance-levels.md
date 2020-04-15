---
title: Уровни соответствия СЗЛ Документы Майкрософт
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
ms.openlocfilehash: 875330ac78588566b4b1c212f7a65d2841127a61
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301385"
---
# <a name="sql-conformance-levels"></a>Уровни соответствия SQL
Уровень грамматики S'L-92, поддерживаемый водителем, указывается на значение, возвращенное вызовом в **S'LGetInfo** с SQL_SQL_CONFORMANCE типом информации. Это указывает на то, соответствует ли драйвер входным, переходным, промежуточным или полным уровням, определенным в S'L-92.  
  
 Все драйверы ODBC должны поддерживать минимальную грамматику СЗЛ, описанную в [минимальной грамматике СЗЛ](../../../odbc/reference/appendixes/sql-minimum-grammar.md) в приложении C: Грамматика S'L. Эта грамматика представляет собой подмножество уровня входа в S'L-92. Драйверы могут поддерживать дополнительные S'L и соответствовать входе S'L-92, промежуточному или полному уровню, или к переходному уровню FIPS 127-2. Водители, которые соответствуют заданного уровню S'L-92 или FIPS 127-2, могут поддерживать дополнительные функции на любом из более высоких уровней, но не полностью соответствующих этому уровню. Чтобы определить, поддерживается ли функция, приложение должно позвонить в **s'LGetInfo** с соответствующим типом информации. Уровень соответствия функции S'L описан в соответствующем информационном типе. (См. описание функции [S'LGetInfo.)](../../../odbc/reference/syntax/sqlgetinfo-function.md)
