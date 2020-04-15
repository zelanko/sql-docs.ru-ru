---
title: SLGetConnectOption (Визуальный драйвер FoxPro ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetConnectOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5703eb39-f3b2-4f3a-8676-a5625ae29a41
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2dd801988343ded46305665ab2a99aa4e7d76cba
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298634"
---
# <a name="sqlgetconnectoption-visual-foxpro-odbc-driver"></a>SQLGetConnectOption (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Частичная  
  
 Соответствие API ODBC: Уровень 1  
  
 Возвращает текущую настройку параметра соединения. Эта функция частично поддерживается: драйвер поддерживает все значения для аргумента *fOption,* но не поддерживает некоторые значения *vParam* для аргумента *fOption* SQL_TXN_ISOLATION.  
  
 В следующей таблице описаны только те аргументы, связанные с поведением, характерным для реализации Visual FoxPro ODBC Driver **в s'LGetConnectOption.**  
  
|*fOption*|Remarks|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|Если вы выберете SQL_AUTOCOMMIT_OFF, приложение должно явно совершать или откатывать транзакции с [помощью S'LTransact;](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md) Водитель Visual FoxPro ODBC не совершает автоматически трансформатируемое заявление по завершении. Драйвер начинает транзакцию, если выписка является транзакционной.|  
|SQL_CURRENT_QUALIFIER|Может быть полностью квалифицированная база данных (.dbc file) имя или полностью квалифицированный путь к каталогу, содержащему ноль или более таблиц (.dbf файлы).|  
|SQL_LOGINTIMEOUT|Возвращает ошибку "Driver Not Capable".|  
|SQL_CURSORS|Возвращает ошибку "Driver Not Capable".|  
|SQL_PACKET_SIZE|Возвращает ошибку "Driver Not Capable".|  
|SQL_TXN_ISOLATION|Водитель позволяет только SQL_TXN_READ_COMMITTED.<br /><br /> Следующие *vParam*s не поддерживаются:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Для получения более подробной информации, *ODBC Programmer's Reference* [см.](../../odbc/reference/syntax/sqlgetconnectoption-function.md)
