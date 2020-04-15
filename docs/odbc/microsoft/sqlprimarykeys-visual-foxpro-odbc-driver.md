---
title: SLPrimaryKeys (Визуальный водитель FoxPro ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLPrimaryKeys function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8dbe2903-efdc-45e0-a079-9e357c5fd81b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 83631d22bd07017c4eba8f6af171443ab8c76d9c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301549"
---
# <a name="sqlprimarykeys-visual-foxpro-odbc-driver"></a>SQLPrimaryKeys (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Полная  
  
 Соответствие ODBC API: Уровень 2  
  
 Возвращает имена столбцов, составляющих основной ключ для таблицы. Реализация Visual FoxPro ODBC Driver **s'LPrimaryKeys** ведет себя следующим образом:  
  
-   Игнорирует аргументы *szTableOwner* и *cbTableOwner.*  
  
-   Работает только для источников данных, которые являются [базами данных.](../../odbc/microsoft/visual-foxpro-terminology.md) Водитель возвращает ошибку "Водитель не поддерживает эту функцию", если источник данных является каталогом [свободных таблиц.](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
 Для получения более подробной информации, *ODBC Programmer's Reference*см. [SQLPrimaryKeys](../../odbc/reference/syntax/sqlprimarykeys-function.md)
