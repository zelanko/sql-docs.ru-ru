---
title: Escape-последовательность внешнего объединения | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 37ce446328d263f492cdfd369f6e8f9f64fe6dfc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303615"
---
# <a name="outer-join-escape-sequence"></a>Escape-последовательность внешнего соединения
ODBC использует escape-последовательности для внешних соединений. Синтаксис этой escape-последовательности выглядит следующим образом:  
  
```  
{oj outer-join}  
```  
  
## <a name="remarks"></a>Remarks  
 В нотации BNF синтаксис выглядит следующим образом:  
  
 *ODBC-OUTER-JOIN — escape* :: =  
  
 *ODBC-ESC-инициатор* ОЖ *внешнее соединение ODBC-ESC-признак конца*  
  
 *внешнее соединение* :: = *Table-name* [*корреляционный имя*] {Left &#124; право &#124; полное}  
  
 ВНЕШНее соединение {имя*таблицы* [*корреляционное*имя] &#124; *внешнее соединение*} включено  
  
 *осуществлять*  
  
 *выполняет*  
  
 *Correlation-Name* :: = *пользовательское имя*  
  
 *ODBC-ESC-инициатор* :: = {  
  
 *ODBC-ESC-признак конца* :: =}  
  
 Чтобы определить, какие части этой инструкции поддерживаются, приложение вызывает **SQLGetInfo** с типом сведений SQL_OJ_CAPABILITIES. Для внешних соединений *условие поиска* должно содержать только условие объединения между указанными *именами таблиц*.
