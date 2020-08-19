---
description: Escape-последовательности интервалов
title: Escape-последовательности интервалов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interval literals [ODBC]
- escape sequences [ODBC], interval
- ODBC escape sequences [ODBC], interval
ms.assetid: 303e8dab-8f13-4fa5-857f-15cc1f75bdd6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e2ef792403352568ce5f8d92c07a5b0e1027b507
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483297"
---
# <a name="interval-escape-sequences"></a>Escape-последовательности интервалов
ODBC использует escape-последовательности для литералов интервала. Синтаксис этой escape-последовательности выглядит следующим образом:  
  
 {*Interval-Literal*}  
  
 Синтаксис BNF *-литерала интервала*см. в разделе [синтаксис литералов интервала](../../../odbc/reference/appendixes/interval-literal-syntax.md) далее в этом приложении.  
  
 Escape-последовательность литерала Interval поддерживается, если типы данных интервала поддерживаются источником данных. Приложение должно вызывать **SQLGetTypeInfo** , чтобы определить, поддерживаются ли эти типы данных.
