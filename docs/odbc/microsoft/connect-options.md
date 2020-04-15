---
title: Параметры подключения Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 25cfe2a897b0c312f91cd0c1e41ad6fa11725ab8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281314"
---
# <a name="connect-options"></a>Параметры подключения
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставленный Oracle.  
  
 Эти параметры позволяют настроить соединение базы данных в приложении.  
  
|Опция подключения|Примечания|  
|--------------------|-----------|  
|SQL_AUTOCOMMIT|Если вы выберете SQL_AUTOCOMMIT_OFF, приложение должно явно совершать или откатывать транзакции с [помощью S'LTransact.](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md)|  
|SQL_ODBC_CURSORS|Этот атрибут соединения реализован в менеджере драйвера.|  
|SQL_OPT_TRACE|Этот атрибут соединения реализован в менеджере драйвера.|  
|SQL_OPT_TRACEFILE|Этот атрибут соединения реализован в менеджере драйвера.|  
|SQL_TRANSLATE_DLL|Ошибка возврата: "Водитель не способен".|  
|SQL_TRANSLATE_OPTION|32-битное значение перешло к переводу .dll.|  
|SQL_TXN_ISOLATION|Водитель позволяет только SQL_TXN_READ_COMMITTED.<br /><br /> Следующие vParams не поддерживаются:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
|SQL_ATTR_ENLIST_IN_DTC|Этот атрибут подключения ODBC 3.0 позволяет использовать драйвер ODBC для Oracle в распределенных транзакциях, координируемых Службами Microsoft Component Services (или МТС, если вы используете Windows NT). Он обеспечивает интерфейс указатель *pITransaction* к сделке в качестве аргумента *vParam.*|  
|SQL_ATTR_CONNECTION_DEAD|Этот атрибут подключения только для чтения ODBC 3.5 позволяет определить, не удалось ли подключение к серверу Oracle. Получить только; не может установить.|
