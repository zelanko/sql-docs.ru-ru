---
title: Параметры Маркеры Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- parameter markers [ODBC]
ms.assetid: 07213d04-cd31-45fd-a8c8-2e16e09eeaf4
author: David-Engel
ms.author: v-daenge
ms.reviewer: ''
ms.openlocfilehash: 132473de586094f79dd34c999d44f6dd59aefaef
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303575"
---
# <a name="parameter-markers"></a>Маркеры параметров
В соответствии со спецификацией S'L-92 приложение не может размещать параметры маркеров в следующих местах. Для более полного списка можно ознакомиться с спецификацией S'L-92.  
  
-   В списке **SELECT**  
  
-   Как оба *выражения* в *сравнении-предикат*  
  
-   Как и в обе стороны двоичного оператора  
  
-   Как и в первом, так и во втором действиях операции **BETWEEN**  
  
-   Как и первая, так и третья операции **ПО**  
  
-   Как выражение, так и первое значение операции **IN**  
  
-   В качестве непредиливого или - операции  
  
-   В качестве аргумента *ссылки на набор функций*  
  
 Для получения более подробной информации о параметрах, см. Для получения дополнительной информации о параметрах [см.](../../../odbc/reference/develop-app/statement-parameters.md)
