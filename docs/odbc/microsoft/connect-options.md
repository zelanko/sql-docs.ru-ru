---
description: Параметры подключения
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 22326ca650f575c6a4f0503093306d8b68581475
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483687"
---
# <a name="connect-options"></a>Параметры подключения
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Эти параметры позволяют настраивать подключение к базе данных в приложении.  
  
|Параметр подключения|Примечания|  
|--------------------|-----------|  
|SQL_AUTOCOMMIT|При выборе SQL_AUTOCOMMIT_OFF приложение должно явно зафиксировать или откатить транзакции с помощью [SQLTransact](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md).|  
|SQL_ODBC_CURSORS|Этот атрибут соединения реализуется в диспетчере драйверов.|  
|SQL_OPT_TRACE|Этот атрибут соединения реализуется в диспетчере драйверов.|  
|SQL_OPT_TRACEFILE|Этот атрибут соединения реализуется в диспетчере драйверов.|  
|SQL_TRANSLATE_DLL|Возвращает ошибку: "драйвер не поддерживается".|  
|SQL_TRANSLATE_OPTION|32-разрядное значение, передаваемое в файл Translation. dll.|  
|SQL_TXN_ISOLATION|Драйвер допускает только SQL_TXN_READ_COMMITTED.<br /><br /> Следующие Впарамс не поддерживаются:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
|SQL_ATTR_ENLIST_IN_DTC|Этот атрибут подключения ODBC 3,0 позволяет использовать драйвер ODBC для Oracle в распределенных транзакциях, управляемых службами компонентов Майкрософт (или MTS, если используется Windows NT). Он предоставляет указатель интерфейса *питрансактион* транзакции в качестве аргумента *впарам* .|  
|SQL_ATTR_CONNECTION_DEAD|Этот атрибут подключения ODBC 3,5, предназначенный только для чтения, позволяет определить, завершилось ли соединение с сервером Oracle. Только получение; не удается задать значение.|
