---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 62f1033abeaa32499602534f7f43b17fefe55ce9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47767262"
---
# <a name="sqlgetconnectoption-visual-foxpro-odbc-driver"></a>SQLGetConnectOption (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения Visual FoxPro ODBC-драйвером. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: частичная  
  
 Соответствия API ODBC: 1 уровень  
  
 Возвращает текущее значение параметра соединения. Эта функция поддерживается частично: драйвер поддерживает все значения для *fOption* аргумент, но не поддерживает некоторые *vParam* значений в параметре *fOption* аргумент SQL_TXN_ISOLATION.  
  
 В следующей таблице описаны только те аргументы, поведение, характерное для реализации драйвер ODBC для Visual FoxPro **SQLGetConnectOption**.  
  
|*fOption*|Примечания|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|Если SQL_AUTOCOMMIT_OFF, приложение должно явно фиксации или отката транзакции с [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); драйвера ODBC для Visual FoxPro не фиксирует инструкции могут быть частью транзакции по завершении автоматически. Драйвер начать транзакцию, если инструкция является могут быть частью транзакции.|  
|SQL_CURRENT_QUALIFIER|Может быть полное доменное имя базы данных (файл .dbc) или полный путь к каталогу, содержащему ноль или более таблиц (.dbf файлы).|  
|SQL_LOGINTIMEOUT|Возвращает ошибку «Драйвер не поддерживает».|  
|SQL_CURSORS|Возвращает ошибку «Драйвер не поддерживает».|  
|SQL_PACKET_SIZE|Возвращает ошибку «Драйвер не поддерживает».|  
|SQL_TXN_ISOLATION|Драйвер позволяет только SQL_TXN_READ_COMMITTED.<br /><br /> Следующие *vParam*s не поддерживаются:<br /><br /> ЗНАЧЕНИЯМИ SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Дополнительные сведения см. в разделе [SQLGetConnectOption](../../odbc/reference/syntax/sqlgetconnectoption-function.md) в *Справочник по программированию ODBC*.
