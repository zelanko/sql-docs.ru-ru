---
title: СЗЛПодготовка (Визуальный водитель FoxPro ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLPrepare function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 0c4cb5a4-9729-4b2e-a0c6-52027b92e8fc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 14c9358d04e539eb2c77a00e195e8216cd0f5496
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301560"
---
# <a name="sqlprepare-visual-foxpro-odbc-driver"></a>SQLPrepare (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Полная  
  
 Соответствие ODBC API: базовый уровень  
  
 Подготавливает выписку по S'L, планируя, как оптимизировать и выполнить выписку. Заявление о СЗЛ составляется для выполнения по данным [sLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
 Если в таблице, представлении или названиях полей содержатся пробелы, приложи имена в задние кавычки (') знаки. Например, если база данных содержит таблицу под названием My Table и поле My Field, приложить каждый элемент идентификатора следующим образом:  
  
```  
SELECT * FROM `My Table`.`My Field`  
```  
  
 Для получения более подробной информации, *ODBC Programmer's Reference*см. [SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md)
