---
title: СЗЛСТоКоннекта (Драйвер доступа) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLSetConnectOption
- SQLSetConnectOption function [ODBC], Access Driver
ms.assetid: 58399bc4-d0b1-4eaa-a474-c92b2d5855ea
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8e5f15575d34031d9886219af5677b4fc5f1d5aa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301537"
---
# <a name="sqlsetconnectoption-access-driver"></a>SQLSetConnectOption (драйвер для Access)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах доступа. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
|fOption|Комментарий|  
|-------------|-------------|  
|SQL_ACCESS_MODE|SQL_ACCESS_MODE fOption можно установить на SQL_MODE_READ_ONLY или SQL_MODE_READ_WRITE. Однако драйвер не препятствует обновлению, если SQL_ACCESS_MODE настроена на SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|При использовании драйвера Microsoft Access SQL_AUTOCOMMIT опция может быть установлена либо SQL_AUTOCOMMIT_ON, либо SQL_AUTOCOMMIT_OFF, поскольку драйвер Microsoft Access поддерживает транзакции.|  
|SQL_CURRENT_QUALIFIER|Поддерживается.|  
|SQL_LOGIN_TIMEOUT|Не поддерживается.|  
|SQL_OPT_TRACE|Поддерживается.|  
|SQL_OPT_TRACEFILE|Поддерживается.|  
|SQL_PACKET_SIZE|Не поддерживается.|  
|SQL_QUIET_MODE|Не поддерживается.|  
|SQL_TRANSLATE_DLL|Не поддерживается.|  
|SQL_TRANSLATION_OPTION|Не поддерживается.|  
|SQL_TXN_ISOLATION|SQL_TXN_ISOLATION всегда SQL_TXN_READ_COMMITTED.|  
  
 Атомные транзакции не поддерживаются драйвером Microsoft Access. При совершении транзакции с помощью драйвера Microsoft Access между моментом совершения транзакции и временем записи значений на диск существует конечная задержка. Эта задержка определяется задержкой, присущей двигателю Microsoft Jet. Время отойти от страницы не будет меньше минимального значения, даже если параметр PageTimeout установлен ниже этого значения. В результате нет никакой гарантии, что зафиксированные данные стабильны, так как изменения могут быть внесены во время задержки.
