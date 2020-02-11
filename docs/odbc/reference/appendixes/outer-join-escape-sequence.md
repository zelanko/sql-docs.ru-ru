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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 576fe7268ccf71a8c926f6b1124ebbf8a8c711b0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68100642"
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
