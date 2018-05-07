---
title: SQLGetConnectOption (драйвер ODBC для Visual FoxPro) | Документы Microsoft
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
- SQLGetConnectOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5703eb39-f3b2-4f3a-8676-a5625ae29a41
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23654dc89260423ce51fcde1fd60e554a3095209
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetconnectoption-visual-foxpro-odbc-driver"></a>SQLGetConnectOption (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: частичная  
  
 Соответствия ODBC API: 1 уровень  
  
 Возвращает текущее значение параметра соединения. Эта функция поддерживается частично: драйвер поддерживает все значения для *fOption* аргумент, но не поддерживает некоторые *vParam* значения для *fOption* аргумент SQL_TXN_ISOLATION.  
  
 В следующей таблице описаны только те аргументы, поведение, характерное для драйвера ODBC для Visual FoxPro реализация **SQLGetConnectOption**.  
  
|*fOption*|Замечания|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|При выборе SQL_AUTOCOMMIT_OFF ваше приложение должно явно фиксации или отката транзакции с [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); драйвер ODBC для Visual FoxPro не фиксирует автоматически выполнении инструкции после завершения. Драйвер начать транзакцию, при выполнении инструкции.|  
|SQL_CURRENT_QUALIFIER|Может быть полное доменное имя базы данных (.dbc-файл) или полный путь к каталогу, содержащему ноль или более таблиц (расширением DBF-файлы).|  
|SQL_LOGINTIMEOUT|Возвращает ошибку «Драйвер не поддерживает».|  
|SQL_CURSORS|Возвращает ошибку «Драйвер не поддерживает».|  
|SQL_PACKET_SIZE|Возвращает ошибку «Драйвер не поддерживает».|  
|SQL_TXN_ISOLATION|Драйвер допускает использование только SQL_TXN_READ_COMMITTED.<br /><br /> Следующие *vParam*s не поддерживаются:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Дополнительные сведения см. в разделе [SQLGetConnectOption](../../odbc/reference/syntax/sqlgetconnectoption-function.md) в *справочнике программиста ODBC*.
