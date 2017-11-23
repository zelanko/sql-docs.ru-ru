---
title: "Escape-последовательности внешнего соединения | Документы Microsoft"
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
- outer join escape sequence [ODBC]
- escape sequences [ODBC], outer join
- ODBC escape sequences [ODBC], outer join
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 947a3ad16efa1b34176311b6ad70b36635dda6f6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="outer-join-escape-sequence"></a>Escape-последовательности внешнего соединения
ODBC использует escape-последовательности для внешних соединений. Ниже приведен синтаксис escape-последовательности:  
  
```  
{oj outer-join}  
```  
  
## <a name="remarks"></a>Замечания  
 В форме БЭКУСА-Наура используется следующий синтаксис:  
  
 *ODBC-внешнее join-escape* :: =  
  
 *ODBC-esc инициатор* oj *внешнего соединения, ODBC-esc-признак конца*  
  
 *внешнее соединение* :: = *имя таблицы* [*корреляционное имя*] {СЛЕВА &#124; ПРАВО &#124; ПОЛНЫЙ}  
  
 OUTER JOIN {*имя таблицы* [*корреляционное имя*] &#124; *внешнего соединения*} ON  
  
 *Поиск-*  
  
 *условия*  
  
 *Корреляционное имя* :: = *определенное имя пользователя*  
  
 *ODBC-esc инициатор* :: = {}  
  
 *ODBC esc признак конца* :: =}  
  
 Чтобы определить, какие части этой инструкции, поддерживаются, приложение вызывает **SQLGetInfo** с типом SQL_OJ_CAPABILITIES сведения. Для внешних соединений *условие поиска* должен содержать условие соединения между указанным *имена таблиц*.
