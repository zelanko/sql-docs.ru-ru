---
title: Сводка интерфейса поставщика служб ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ace6085b-355b-435b-8734-503fc3c12ec2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b2f7e459cc7b89106bf1b7ebcd49c699d43da9f6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298901"
---
# <a name="odbc-service-provider-interface-summary"></a>Сводка по интерфейсу поставщика служб ODBC
В следующей таблице описываются функции интерфейса поставщика служб ODBC. Дополнительные сведения о синтаксисе и семантике каждой функции см. в разделе [Справочник по интерфейсу поставщика служб ODBC (SPI)](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md).  
  
|Имя функции|Назначение|  
|-------------------|-------------|  
|[склсетконнектаттрфордбЦинфо](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|То же, что и [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), но он задает атрибут для маркера сведений о соединении, а не для маркера подключения.|  
|[склсетдриверконнектинфо](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|Задает строку подключения в токене сведений о соединении для вызова [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) приложения.|  
|[склсетконнектинфо](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Задает источник данных, идентификатор пользователя и пароль в токене сведений о соединении для вызова [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) приложения.|  
|[склжетпулид](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Получает идентификатор пула.|  
|[склратеконнектион](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Определяет, может ли драйвер повторно использовать существующее подключение в пуле соединений.|  
|[склпулконнект](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Создать новое соединение, если невозможно повторно использовать подключение в пуле.|  
|[склклеанупконнектионпулид](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Информирует драйвер о том, что истекло время ожидания для идентификатора пула.|
