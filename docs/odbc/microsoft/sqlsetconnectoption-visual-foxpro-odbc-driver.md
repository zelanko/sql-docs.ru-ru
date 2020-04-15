---
title: SLSetConnectOption (Визуальный драйвер FoxPro ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5a35449e-4694-4ee5-9fa1-45d5a8fe7823
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2af208663f1e91250faad0ca9538b76bcec43b06
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301505"
---
# <a name="sqlsetconnectoption-visual-foxpro-odbc-driver"></a>SQLSetConnectOption (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Частичная  
  
 Соответствие API ODBC: Уровень 1  
  
 Устанавливает параметры, которые регулируют аспекты соединений. Эта функция частично поддерживается: драйвер поддерживает все значения для аргумента *fOption,* но не поддерживает некоторые значения *vParam* для аргумента *fOption* SQL_TXN_ISOLATION.  
  
 В следующей таблице описаны только те аргументы, связанные с поведением, характерным для реализации Visual FoxPro ODBC Driver **в s'LSetConnectOption.**  
  
|*fOption*|Remarks|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|Если вы выберете SQL_AUTOCOMMIT_OFF, приложение должно явно совершать или откатывать транзакции с [помощью S'LTransact;](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md) Водитель Visual FoxPro ODBC не совершает автоматически трансформатируемое заявление по завершении. Драйвер начинает транзакцию, если выписка является транзакционной.|  
|SQL_CURRENT_QUALIFIER|Может быть полностью квалифицированным [названием базы данных](../../odbc/microsoft/visual-foxpro-terminology.md) или полностью квалифицированным путем к каталогу, содержащему ноль или более [бесплатных таблиц.](../../odbc/microsoft/visual-foxpro-terminology.md)|  
|SQL_LOGINTIMEOUT|Возвращает ошибку "Водитель не способен".|  
|SQL_CURSORS|Возвращает ошибку "Водитель не способен".|  
|SQL_PACKET_SIZE|Возвращает ошибку "Водитель не способен".|  
|SQL_TXN_ISOLATION|Водитель позволяет только SQL_TXN_READ_COMMITTED.<br /><br /> Следующие *vParam*s не поддерживаются:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Для получения более подробной информации, *ODBC Programmer's Reference* [см.](../../odbc/reference/syntax/sqlsetconnectoption-function.md)
