---
title: "Параметры подключения | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection options [ODBC]
- ODBC driver for Oracle [ODBC], connection options
- custom connection options [ODBC]
ms.assetid: abfdc133-cb33-435f-a467-fbe15444f687
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9bb45857d47ef145c5693f6718696cbf75ccd666
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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

