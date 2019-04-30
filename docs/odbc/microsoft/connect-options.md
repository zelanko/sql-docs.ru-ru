---
title: Параметры подключения | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection options [ODBC]
- ODBC driver for Oracle [ODBC], connection options
- custom connection options [ODBC]
ms.assetid: abfdc133-cb33-435f-a467-fbe15444f687
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 06695bf1770c9e362decac5702dcd924d47c23bb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63301765"
---
# <a name="connect-options"></a>Параметры подключения
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Эти параметры позволяют настраивать подключения к базе данных в приложении.  
  
|Параметр подключения|Примечания|  
|--------------------|-----------|  
|SQL_AUTOCOMMIT|Если SQL_AUTOCOMMIT_OFF, приложение должно явно фиксации или отката транзакции с [SQLTransact](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md).|  
|SQL_ODBC_CURSORS|Этот атрибут подключения реализуется диспетчера драйверов.|  
|SQL_OPT_TRACE|Этот атрибут подключения реализуется диспетчера драйверов.|  
|SQL_OPT_TRACEFILE|Этот атрибут подключения реализуется диспетчера драйверов.|  
|SQL_TRANSLATE_DLL|Возвращает следующую ошибку: «Драйвер не поддерживает».|  
|SQL_TRANSLATE_OPTION|32-разрядное значение, передаваемые от перевода DLL-файл.|  
|SQL_TXN_ISOLATION|Драйвер позволяет только SQL_TXN_READ_COMMITTED.<br /><br /> Не поддерживаются следующие vParams:<br /><br /> ЗНАЧЕНИЯМИ SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
|SQL_ATTR_ENLIST_IN_DTC|Этот атрибут подключения ODBC 3.0 позволяет использовать драйвер ODBC для Oracle в распределенных транзакциях, координируемых с помощью служб компонентов Майкрософт (или MTS, если вы используете Windows NT). Он предоставляет указатель на интерфейс *pITransaction* для транзакции, что *vParam* аргумент.|  
|SQL_ATTR_CONNECTION_DEAD|Этот атрибут подключения ODBC 3.5 только для чтения позволяет определить, является ли ошибка подключения к серверу Oracle. Get. Невозможно задать.|
