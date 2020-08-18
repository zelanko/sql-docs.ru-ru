---
description: SQLGetConnectOption (драйвер ODBC для Visual FoxPro)
title: SQLGetConnectOption (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
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
ms.openlocfilehash: dd22ec3862ff2f0f3c4f7b5aa9dbeff53a5d8cfe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411790"
---
# <a name="sqlgetconnectoption-visual-foxpro-odbc-driver"></a>SQLGetConnectOption (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу ODBC для Visual FoxPro. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: частичная  
  
 Соответствие API ODBC: уровень 1  
  
 Возвращает текущее значение параметра соединения. Эта функция поддерживается частично: драйвер поддерживает все значения для аргумента *параметром fOption* , но не поддерживает некоторые значения *впарам* для аргумента *параметром fOption* SQL_TXN_ISOLATION.  
  
 В следующей таблице описаны только те аргументы, поведение которых характерно для реализации **SQLGetConnectOption**драйвера ODBC для Visual FoxPro.  
  
|*Параметром fOption*|Remarks|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|При выборе SQL_AUTOCOMMIT_OFF приложение должно явно зафиксировать или откатить транзакции с помощью [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); Драйвер ODBC для Visual FoxPro не фиксирует инструкцию transactа автоматически после завершения. Драйвер начинает транзакцию, если инструкция является инструкцией transactа.|  
|SQL_CURRENT_QUALIFIER|Может быть полным именем базы данных (DBC-файлом) или полным путем к каталогу, содержащим ноль или более таблиц (DBF-файлов).|  
|SQL_LOGINTIMEOUT|Возвращает ошибку "драйвер не поддерживается".|  
|SQL_CURSORS|Возвращает ошибку "драйвер не поддерживается".|  
|SQL_PACKET_SIZE|Возвращает ошибку "драйвер не поддерживается".|  
|SQL_TXN_ISOLATION|Драйвер допускает только SQL_TXN_READ_COMMITTED.<br /><br /> Следующие *впарам*s не поддерживаются:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Дополнительные сведения см. в разделе [SQLGetConnectOption](../../odbc/reference/syntax/sqlgetconnectoption-function.md) в *справочнике программиста по ODBC*.
