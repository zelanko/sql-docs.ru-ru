---
title: SQLTransact (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e554a8669b6e6e95e234a5b939477a8bb2f7b8cc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67948868"
---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения Visual FoxPro ODBC-драйвером. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: Полное  
  
 Соответствие API ODBC: Уровня ядра  
  
 Запрашивает операцию commit или rollback для всех активных операций на все дескрипторы инструкций (*hstmt*s), связанных с подключением или для всех подключений, связанных с дескриптором среды, *henv*. **SQLTransact** работает только для источников данных, которые являются [баз данных](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Если фиксация завершается неудачей, если в ручном режиме, транзакция остается активным; Вы можете выполнить откат транзакции или повторите операцию фиксации. При сбое операции фиксации в режиме автоматической транзакции, транзакция откатывается автоматически. транзакция не может быть неактивной.  
  
 Дополнительные сведения см. в разделе [SQLTransact](../../odbc/reference/syntax/sqltransact-function.md) в *Справочник по программированию ODBC*.
