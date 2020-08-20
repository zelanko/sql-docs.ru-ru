---
description: Escape-последовательность внешнего соединения
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
ms.openlocfilehash: 22517e676f9f8ac80622d368edcdb5a0ce1b283f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466096"
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
