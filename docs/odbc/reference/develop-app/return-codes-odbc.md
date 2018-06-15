---
title: Коды возврата ODBC | Документы Microsoft
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
- return codes [ODBC]
- diagnostic information [ODBC], return codes
ms.assetid: e893b719-4392-476f-911a-5ed6da6f7e94
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 12751f87c9f9832567dc04ba7df7659e80e66897
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32913219"
---
# <a name="return-codes-odbc"></a>Коды возврата ODBC
Каждая функция в ODBC возвращает код, известный как его *возвращаемый код* указывающая общий успех или сбой функции. Программная логика обычно основана на кодах возврата.  
  
 Например, следующий код вызывает **SQLFetch** для получения строк в результирующем наборе. Она проверяет код возврата функции, чтобы определить, если результирующий набор достигнут конец (SQL_NO_DATA), если все сведения о предупреждении был возвращен (SQL_SUCCESS_WITH_INFO) или произошла ошибка (SQL_ERROR).  
  
```  
SQLRETURN   rc;  
SQLHSTMT    hstmt;  
  
while ((rc=SQLFetch(hstmt)) != SQL_NO_DATA) {  
   if (rc == SQL_SUCCESS_WITH_INFO) {  
      // Call function to display warning information.  
   } else if (rc == SQL_ERROR) {  
      // Call function to display error information.  
      break;  
   }  
   // Process row.  
}  
```  
  
 Код возврата SQL_INVALID_HANDLE всегда указывает на программную ошибку, поэтому не должен встречаться во время выполнения. Все другие коды возврата предоставляют сведения времени выполнения, хотя SQL_ERROR может означать программную ошибку.  
  
 В следующей таблице определены коды возврата.  
  
|Код возврата|Описание|  
|-----------------|-----------------|  
|SQL_SUCCESS|Функция успешно завершена. Приложение вызывает **SQLGetDiagField** для получения дополнительных сведений из записи заголовка.|  
|SQL_SUCCESS_WITH_INFO|Функция успешно завершена, возможно с некритичные ошибки (предупреждение). Приложение вызывает **SQLGetDiagRec** или **SQLGetDiagField** для получения дополнительных сведений.|  
|SQL_ERROR|Сбой функции. Приложение вызывает **SQLGetDiagRec** или **SQLGetDiagField** для получения дополнительных сведений. Содержимое из любой из выходных аргументов функции не определено.|  
|SQL_INVALID_HANDLE|Сбой функции из-за недопустимого дескриптора среды, соединения, оператор или дескриптора. Это указывает на программную ошибку. Дополнительные сведения недоступны из **SQLGetDiagRec** или **SQLGetDiagField**. Этот код возвращается только в том случае, если дескриптор является указателем null или имеет неправильный тип, например при передаче дескриптор инструкции для аргумента, который требует дескриптора соединения.|  
|ЗНАЧЕНИЕ SQL_NO_DATA|Больше нет данных была доступна. Приложение вызывает **SQLGetDiagRec** или **SQLGetDiagField** для получения дополнительных сведений. Один или несколько записей состояния, определяемым драйвером в 02xxx класса могут быть возвращены. **Примечание:** в ODBC 2. *x*, это возвращать код называется SQL_NO_DATA_FOUND.|  
|SQL_NEED_DATA|Дополнительные сведения о соединениях необходим или необходимы дополнительные данные, например, когда параметр данные передаются во время выполнения. Приложение вызывает **SQLGetDiagRec** или **SQLGetDiagField** для получения дополнительных сведений в том случае, если таковые имеются.|  
|SQL_STILL_EXECUTING|Функция, которая была запущена асинхронно все еще выполняется. Приложение вызывает **SQLGetDiagRec** или **SQLGetDiagField** для получения дополнительных сведений в том случае, если таковые имеются.|
