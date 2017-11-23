---
title: "Скалярная функция Escape-последовательность | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ca49a0f372ef192336318fc2af3135adf4c37d1e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="scalar-function-escape-sequence"></a>Скалярная функция Escape-последовательность
Для скалярных функций ODBC используется escape-последовательности. Ниже приведен синтаксис escape-последовательности:  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>Замечания  
 В форме БЭКУСА-Наура используется следующий синтаксис:  
  
 *ODBC скаляр функция escape* :: =  
  
 *ODBC-esc инициатор* fn *скалярная функция, ODBC-esc-признак конца*  
  
 *Скалярная функция* :: = *имя функции* (*список аргументов*)  
  
 (Определения Нетерминальные слова *имя функции* и *имя функции* (*список аргументов*) являются производными от список скалярных функций в [ Приложение д скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).)  
  
 *ODBC-esc инициатор* :: = {}  
  
 *ODBC esc признак конца* :: =}  
  
 Чтобы определить источник данных поддерживает процедур и драйвер поддерживает синтаксис вызова процедуры ODBC, приложение может вызвать **SQLGetInfo**. Дополнительные сведения см. в разделе [приложение E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).
