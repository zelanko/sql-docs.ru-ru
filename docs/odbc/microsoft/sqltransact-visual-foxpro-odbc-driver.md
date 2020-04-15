---
title: СЗЛТрансакт (Визуальный водитель FoxPro ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTransact function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 92cf86c0-f7a8-44d7-b59f-a1342677440b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3910f24578bcbc409a84573e994c0680ed5949b2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299224"
---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Полная  
  
 Соответствие ODBC API: базовый уровень  
  
 Запрашивает операцию фиксации или отката для всех активных операций на всех декретах оператора *(hstmt*s), связанных с соединением или для всех соединений, связанных с обработкой среды, *henv*. **S'LTransact** работает только для источников данных, которые являются [базами данных.](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
 Если коммит завершается в ручном режиме, транзакция остается активной; вы можете откатить транзакцию или повторить операцию фиксации. Если операция коммита завершается сбой, когда в автоматическом режиме транзакции транзакция откатывается автоматически; транзакция не может быть неактивной.  
  
 Для получения более подробной информации, *ODBC Programmer's Reference*см. [SQLTransact](../../odbc/reference/syntax/sqltransact-function.md)
