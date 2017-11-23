---
title: "Инициализация поля дескриптора | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- initializing descriptor fields [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1da157cb-8ea9-4a56-983b-1c45650217c5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ea0725d098999471ae87bcb6ca4af9a4b18565f2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="initialization-of-descriptor-fields"></a>Инициализация поля дескриптора
Когда выделяется дескриптор строк приложения, его полей получать начальные значения, как указано в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Начальное значение поля SQL_DESC_TYPE — SQL_DEFAULT. Это обеспечивает для стандартной обработки базы данных для представления в приложение. Приложение может задать другой способ обработки данных, поля дескриптора записи.  
  
 Начальное значение SQL_DESC_ARRAY_SIZE в заголовке дескриптор-1. Это поле для включения нескольких строк выборки можно изменить приложение.  
  
 Является недопустимым в полях IRD понятие значение по умолчанию. Приложение может получить доступ к полям IRD, только при наличии подготовленных или выполненных инструкции, связанные с ним.  
  
 Некоторые поля IPD определяются только после IPD автоматически заполняется с помощью драйвера. В противном случае они определены. Эти поля являются SQL_DESC_CASE_SENSITIVE, SQL_DESC_FIXED_PREC_SCALE, SQL_DESC_TYPE_NAME, SQL_DESC_UNSIGNED и SQL_DESC_LOCAL_TYPE_NAME.
