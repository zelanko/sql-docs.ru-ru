---
title: Параметры подключения | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connection options [ODBC]
- ODBC driver for Oracle [ODBC], connection options
- custom connection options [ODBC]
ms.assetid: abfdc133-cb33-435f-a467-fbe15444f687
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b0b5f81b708f520edb03aa80261e62170ddc11a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32899719"
---
# <a name="connect-options"></a>Параметры подключения
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Эти параметры позволяют настройку подключения к базе данных в приложении.  
  
|Параметр подключения|Примечания|  
|--------------------|-----------|  
|SQL_AUTOCOMMIT|При выборе SQL_AUTOCOMMIT_OFF ваше приложение должно явно фиксации или отката транзакции с [SQLTransact](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md).|  
|SQL_ODBC_CURSORS|Этот атрибут подключения реализуется диспетчера драйверов.|  
|SQL_OPT_TRACE|Этот атрибут подключения реализуется диспетчера драйверов.|  
|SQL_OPT_TRACEFILE|Этот атрибут подключения реализуется диспетчера драйверов.|  
|SQL_TRANSLATE_DLL|Возвращает ошибку: «Драйвер не поддерживает».|  
|SQL_TRANSLATE_OPTION|32-разрядное значение, передаваемое .dll для трансляции.|  
|SQL_TXN_ISOLATION|Драйвер допускает использование только SQL_TXN_READ_COMMITTED.<br /><br /> Не поддерживаются следующие vParams:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
|SQL_ATTR_ENLIST_IN_DTC|Этот атрибут подключения ODBC 3.0 позволяет использовать драйвер ODBC для Oracle в распределенных транзакциях, координируемых служб компонентов Microsoft (или MTS, если вы используете Windows NT). Он предоставляет указатель на интерфейс *pITransaction* для транзакции как *vParam* аргумент.|  
|SQL_ATTR_CONNECTION_DEAD|Этот атрибут подключения ODBC 3.5 только для чтения позволяет определить, является ли сбой подключения к серверу Oracle. Получить только; не удалось установить.|
