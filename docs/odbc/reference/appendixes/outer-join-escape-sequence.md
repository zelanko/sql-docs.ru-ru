---
title: Escape-последовательности внешнего соединения | Документы Microsoft
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
- outer join escape sequence [ODBC]
- escape sequences [ODBC], outer join
- ODBC escape sequences [ODBC], outer join
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: af6a98b3e1a7848fa242dfceb890c472e1d16f74
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907529"
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
  
 *внешнее соединение* :: = *имя таблицы* [*корреляционное имя*] {СЛЕВА &#124; ПРАВО &#124; полный}  
  
 ВНЕШНЕЕ соединение {*имя таблицы* [*корреляционное имя*] &#124; *внешнего соединения*} ON  
  
 *Поиск-*  
  
 *условия*  
  
 *Корреляционное имя* :: = *определенное имя пользователя*  
  
 *ODBC-esc инициатор* :: = {}  
  
 *ODBC esc признак конца* :: =}  
  
 Чтобы определить, какие части этой инструкции, поддерживаются, приложение вызывает **SQLGetInfo** с типом SQL_OJ_CAPABILITIES сведения. Для внешних соединений *условие поиска* должен содержать условие соединения между указанным *имена таблиц*.
