---
title: SLExecDirect (Визуальный водитель FoxPro ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExecDirect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5004060f-8510-4018-87a4-d41789e69d3e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 40c0a3404a3e7a9a67b6f71d197343eddb417955
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298674"
---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Полная  
  
 Соответствие ODBC API: базовый уровень  
  
 Выполняет новую, [предпарируемую выписку s'L](../../odbc/microsoft/visual-foxpro-terminology.md). Драйвер Visual FoxPro ODBC использует текущие значения переменных параметра, если в сообщении отсутствуют какие-либо параметры.  
  
 Для создания командной команды пакетной подачи несколько заявлений s'L одновременно используйте запятую (;) для разделения каждого оператора S'L в пакете.  
  
 Если в таблице, представлении или поле в названиях содержатся пробелы, приложи имена в задние кавычки. Например, если база данных содержит таблицу под названием My Table и поле My Field, приложить каждый элемент идентификатора следующим образом:  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 Для получения более подробной информации, *ODBC Programmer's Reference* [см.](../../odbc/reference/syntax/sqlexecdirect-function.md)
