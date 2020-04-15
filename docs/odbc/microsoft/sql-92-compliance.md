---
title: Соответствие требованиям СЗЛ-92 Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], SQL-92 compliance
- desktop database drivers [ODBC], SQL-92 compliance
- SQL-92 compliance [ODBC]
- ODBC desktop database drivers [ODBC], SQL-92 compliance
ms.assetid: 50c8c7df-df01-4f4d-ad62-d059cf29d73a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9ac0ae5873e545afb8fcac9dd003c984b1ed303a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300704"
---
# <a name="sql-92-compliance"></a>Соответствие SQL-92
Драйверы базы данных ODBC desktop и базовый движок Microsoft Jet не соответствуют требованиям S'L-92. Они поддерживают многие функции, которые были определены в S'L-92. Некоторые функции, поддерживаемые в драйвере, не поддерживаются в S'L-92. Для получения дополнительной информации, *см.* Ниже приведены основные различия между ними:  
  
-   Драйверы настольных баз данных, используемые в настольной базе данных, поддерживают более мощные выражения, чем те, которые указаны в S'L-92.  
  
-   К предикату BETWEEN применяются различные правила.  
  
-   СЗЛ, используемый драйверами настольных баз данных, и ANSI S'L поддерживает различные ключевые слова.  
  
 Следующие функции S'L-92 не поддерживаются Microsoft Jet S'L:  
  
-   Заявления о безопасности, такие как GRANT и LOCK.  
  
-   ОТЛИЧИЕ с агрегированными ссылками функции.  
  
 Следующие функции являются усовершенствования в S'L, используемые драйверами настольных баз данных, которые не указаны s'L-92:  
  
-   Заявление TRANSFORM, обеспечивающее поддержку перекрестных запросов.  
  
-   Дополнительные агрегированные функции **(StDev** и **VarP**).  
  
> [!NOTE]  
>  Драйверы настольных баз данных поддерживают стандартный синтаксис ANSI в процентах (процент) и q (подчеркиваю), а не (звездочка) и ? (вопросительный знак).
