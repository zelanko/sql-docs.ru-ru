---
title: Ошибки и пакеты (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 36a402686a695a08748df24a7b40a228d7a2ca7f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300434"
---
# <a name="errors-and-batches"></a>Ошибки и пакеты
При возникновении ошибки при выполнении пакета инструкций S'L возможен один из следующих четырех исходов. (Каждый возможный результат зависит от источника данных и может даже зависеть от утверждений, включенных в пакет.)  
  
-   Операторы в пакете не выполняются.  
  
-   Операторы в пакете не выполняются, и транзакция откатывается.  
  
-   Все операторы до выполнения оператора ошибки выполнены.  
  
-   Все операторы, кроме оператора ошибки, выполняются.  
  
 В первых двух случаях, **S'LExecute** и **S'LExecDirect** возвращения SQL_ERROR. В последних двух случаях они могут вернуться SQL_SUCCESS_WITH_INFO или SQL_SUCCESS, в зависимости от их осуществления. Во всех случаях, дальнейшая информация об ошибках может быть получена с **помощью S'LGetDiagField**, **S'LGetDiagRec**, или **S'LError**. Однако характер и глубина этой информации являются конкретными источниками данных. Кроме того, эта информация вряд ли точно идентифицирует заявление по ошибке.
