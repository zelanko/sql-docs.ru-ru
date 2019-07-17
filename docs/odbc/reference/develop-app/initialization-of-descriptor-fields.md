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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c78162bcf0421fee609abe5fcacf9613e0f8020b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138943"
---
# <a name="initialization-of-descriptor-fields"></a>Инициализация полей дескриптора
При выделении дескриптор строки приложения, его поля получать начальные значения, как указано в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Начальное значение в поле SQL_DESC_TYPE — SQL_DEFAULT. Это обеспечивает для стандартной обработки данных в базе данных для представления приложения. Приложение может задать различных подходов к обработке данных, задав поля записи дескриптора.  
  
 Начальное значение SQL_DESC_ARRAY_SIZE в дескрипторе заголовке равно 1. Приложения можно изменить это поле для включения нескольких строк выборки.  
  
 Концепция значение по умолчанию не является допустимым для поля IRD. Приложения могут получить доступ к полям IRD, только при наличии подготовленных или выполненных инструкции, связанные с ней.  
  
 Некоторые поля IPD определены только в том случае, после IPD автоматически заполнения драйвером. Если это не так, они будут неопределенными. Эти поля могут SQL_DESC_CASE_SENSITIVE, SQL_DESC_FIXED_PREC_SCALE, SQL_DESC_TYPE_NAME, SQL_DESC_UNSIGNED и SQL_DESC_LOCAL_TYPE_NAME.
