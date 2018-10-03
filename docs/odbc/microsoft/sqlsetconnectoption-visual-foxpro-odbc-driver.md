---
title: SQLSetConnectOption (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 398d098615a0453cb016286867836388fd817540
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47631792"
---
# <a name="sqlsetconnectoption-visual-foxpro-odbc-driver"></a>SQLSetConnectOption (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения Visual FoxPro ODBC-драйвером. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: частичная  
  
 Соответствия API ODBC: 1 уровень  
  
 Задает параметры, которые управляют аспектами подключений. Эта функция поддерживается частично: драйвер поддерживает все значения для *fOption* аргумент, но не поддерживает некоторые *vParam* значений в параметре *fOption* аргумент SQL_TXN_ISOLATION.  
  
 В следующей таблице описаны только те аргументы, поведение, характерное для реализации драйвер ODBC для Visual FoxPro **SQLSetConnectOption**.  
  
|*fOption*|Примечания|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|Если SQL_AUTOCOMMIT_OFF, приложение должно явно фиксации или отката транзакции с [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); драйвера ODBC для Visual FoxPro не фиксирует инструкции могут быть частью транзакции по завершении автоматически. Драйвер начать транзакцию, если инструкция является могут быть частью транзакции.|  
|SQL_CURRENT_QUALIFIER|Может иметь полную спецификацию [базы данных](../../odbc/microsoft/visual-foxpro-terminology.md) имя или полный путь к каталогу, который содержит ноль или более [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md).|  
|SQL_LOGINTIMEOUT|Возвращает строку «драйвер не поддерживает» ошибка.|  
|SQL_CURSORS|Возвращает строку «драйвер не поддерживает» ошибка.|  
|SQL_PACKET_SIZE|Возвращает строку «драйвер не поддерживает» ошибка.|  
|SQL_TXN_ISOLATION|Драйвер позволяет только SQL_TXN_READ_COMMITTED.<br /><br /> Следующие *vParam*s не поддерживаются:<br /><br /> ЗНАЧЕНИЯМИ SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Дополнительные сведения см. в разделе [SQLSetConnectOption](../../odbc/reference/syntax/sqlsetconnectoption-function.md) в *Справочник по программированию ODBC*.
