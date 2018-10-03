---
title: Escape-последовательность внешнего соединения | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequence [ODBC]
- escape sequences [ODBC], outer join
- ODBC escape sequences [ODBC], outer join
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba08d33efca6fa90531f89bd57a307f42f343ebd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47817690"
---
# <a name="outer-join-escape-sequence"></a>Escape-последовательность внешнего соединения
ODBC использует escape-последовательности для внешних соединений. Синтаксис escape-последовательность выглядит следующим образом:  
  
```  
{oj outer-join}  
```  
  
## <a name="remarks"></a>Примечания  
 В форме Бэкуса-Наура синтаксис выглядит следующим образом:  
  
 *Внешний join-escape-последовательность ODBC* :: =  
  
 *ODBC-esc инициатор* oj *внешнего соединения, ODBC-esc-признак конца*  
  
 *внешнее соединение* :: = *имя таблицы* [*корреляционное имя*] {СЛЕВА &#124; СПРАВА &#124; полный}  
  
 ВНЕШНЕЕ соединение {*имя таблицы* [*корреляционное имя*] &#124; *внешнего соединения*} ON  
  
 *Поиск-*  
  
 *условие*  
  
 *Корреляционное имя* :: = *определенное имя пользователя*  
  
 *ODBC-esc инициатор* :: = {}  
  
 *ODBC-esc-признак конца* :: =}  
  
 Чтобы определить, какие части Эта инструкция поддерживаются, приложение вызывает **SQLGetInfo** с типом SQL_OJ_CAPABILITIES сведения. Для внешних соединений *условие поиска* должен содержать только условия соединения между указанными *имена таблиц*.
