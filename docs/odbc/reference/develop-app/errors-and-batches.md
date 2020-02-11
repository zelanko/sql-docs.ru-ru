---
title: Ошибки и пакеты | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC], errors
- sql_success_with_info [ODBC]
- sql_success [ODBC]
- SQL statements [ODBC], batches
- sql_error [ODBC]
ms.assetid: 6debd41d-9f4c-4f4c-a44b-2993da5306f0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6902b82c74e953d6009d7e5352608477d92122d6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68051129"
---
# <a name="errors-and-batches"></a>Ошибки и пакеты
При возникновении ошибки при выполнении пакета инструкций SQL возможны следующие четыре результата. (Каждый возможный результат зависит от конкретного источника данных и может даже зависеть от инструкций, включенных в пакет.)  
  
-   Инструкции в пакете не выполняются.  
  
-   Инструкции в пакете не выполняются и выполняется откат транзакции.  
  
-   Все инструкции, предшествующие оператору Error, выполняются.  
  
-   Выполняются все инструкции, кроме оператора Error.  
  
 В первых двух случаях **SQLExecute** и **SQLExecDirect** возвращают SQL_ERROR. В двух последних случаях они могут возвращать SQL_SUCCESS_WITH_INFO или SQL_SUCCESS в зависимости от реализации. Во всех случаях дополнительные сведения об ошибке можно получить с помощью **SQLGetDiagField**, **SQLGetDiagRec**или **SqlError**. Однако природа и глубина этих сведений относятся к источнику данных. Более того, эта информация вряд ли будет четко идентифицирована инструкцию Error.
