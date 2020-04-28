---
title: Инициализация полей дескриптора | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- initializing descriptor fields [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1da157cb-8ea9-4a56-983b-1c45650217c5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e4ed6479a60f1d0695107c216b2f0c94a55f68ff
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300124"
---
# <a name="initialization-of-descriptor-fields"></a>Инициализация полей дескриптора
При выделении дескриптора строки приложения его поля получают начальные значения, как указано в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Начальное значение поля SQL_DESC_TYPE SQL_DEFAULT. Это обеспечивает стандартную обработку данных базы данных для представления в приложении. Приложение может указать другую обработку данных, установив поля записи дескриптора.  
  
 Начальное значение SQL_DESC_ARRAY_SIZE в заголовке дескриптора равно 1. Приложение может изменить это поле, чтобы включить выборку многострочные.  
  
 Понятие значения по умолчанию недопустимо для полей IRD. Приложение может получить доступ к полям IRD только при наличии связанной с ней подготовленной или выполненной инструкции.  
  
 Определенные поля IPD определяются только после того, как IPD автоматически заполняется драйвером. В противном случае они не определены. Это поля SQL_DESC_CASE_SENSITIVE, SQL_DESC_FIXED_PREC_SCALE, SQL_DESC_TYPE_NAME, SQL_DESC_UNSIGNED и SQL_DESC_LOCAL_TYPE_NAME.
