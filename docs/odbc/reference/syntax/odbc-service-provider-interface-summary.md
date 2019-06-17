---
title: Сводка по интерфейсу поставщика служб ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ace6085b-355b-435b-8734-503fc3c12ec2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d5f3c133b105c905b79589d86952658b6d39f0f6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62653391"
---
# <a name="odbc-service-provider-interface-summary"></a>Сводка по интерфейсу поставщика служб ODBC
Ниже перечислены функции интерфейса ODBC поставщика услуг. Дополнительные сведения о синтаксисе и семантике для каждой функции см. в разделе [Справочник по ODBC службы поставщика интерфейса (SPI)](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md).  
  
|Имя функции|Цель|  
|-------------------|-------------|  
|[SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Совпадение с кодом [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), но он задает атрибут в маркере сведения соединения вместо на дескриптор соединения.|  
|[SQLSetDriverConnectInfo](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|Задает строку подключения в info маркер подключения для приложения [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) вызова.|  
|[SQLSetConnectInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Задает источник данных, идентификатор пользователя и пароль в info маркер подключения для приложения [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) вызова.|  
|[SQLGetPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Извлекает идентификатор пула.|  
|[SQLRateConnection](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Определяет, если драйвер можно повторно использовать существующее соединение в пуле соединений.|  
|[SQLPoolConnect](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Создайте новое соединение, если нет подключения в пуле может быть повторно использован.|  
|[SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Информирует драйвер, истекло время ожидания идентификатор пула.|
