---
title: SQL-92 соответствия | Документы Microsoft
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
- Jet-based ODBC drivers [ODBC], SQL-92 compliance
- desktop database drivers [ODBC], SQL-92 compliance
- SQL-92 compliance [ODBC]
- ODBC desktop database drivers [ODBC], SQL-92 compliance
ms.assetid: 50c8c7df-df01-4f4d-ad62-d059cf29d73a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d6f256f16960332de497e6a861137ca42a0480f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sql-92-compliance"></a>SQL-92 соответствия
Драйверы ODBC системной базы данных и базовой ядра Microsoft Jet не соответствует SQL-92. Они поддерживают множество функций, которые были определены в SQL-92. Некоторые функции, поддерживаемые в драйвере не поддерживаются в SQL-92. Дополнительные сведения см. в разделе *Microsoft Jet базы данных подсистемы Руководство программиста*. Ниже приведены основные различия между ними.  
  
-   Используемое драйверами системной базы данных SQL поддерживает более мощные выражения, чем SQL-92.  
  
-   Для предиката BETWEEN применяются различные правила.  
  
-   SQL, используемые драйверов базы данных и ANSI SQL поддерживает разные ключевые слова.  
  
 Microsoft Jet SQL не поддерживаются следующие функции SQL-92:  
  
-   Инструкции безопасности, такие как предоставление и БЛОКИРОВКИ.  
  
-   РАЗЛИЧНЫЕ значения с помощью ссылки в статистической функции.  
  
 Усовершенствования в SQL, используемое драйверами системной базы данных, которые не указаны, SQL-92 имеют следующие возможности:  
  
-   Инструкция ПРЕОБРАЗОВАНИЯ, предоставляя поддержку перекрестных запросов.  
  
-   Дополнительные статистические функции (**StDev** и **VarP**).  
  
> [!NOTE]  
>  Драйверы системной базы данных поддерживает стандартный синтаксис ANSI (в процентах) % и _ (символ подчеркивания) не * (звездочка) и? (вопросительный знак).
