---
title: Функция S'LCompleteAsync Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
f1_keywords:
- SQLCompleteAsync
helpviewer_keywords:
- SQLCompleteAsync function [ODBC]
ms.assetid: 1b97c46a-d2e5-4540-8239-9d975e5321c6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4e09d61ef516e846798dd3af2d07dafa78af4605
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299659"
---
# <a name="sqlcompleteasync-function"></a>Функция SQLCompleteAsync
**Соответствия**  
 Представлена версия: ODBC 3.8  
  
 Соответствие стандартам: Нет  
  
 **Сводка**  
 **Для** определения того, когда асинхронная функция завершена, можно использовать для определения того, когда асинхронная функция выполняется с помощью обработки на основе уведомлений или опросов. Для получения дополнительной информации об асинхронных операциях [см.](../../../odbc/reference/develop-app/asynchronous-execution.md)  
  
 **SLCompleteAsync** реализуется только в менеджере драйверов ODBC.  
  
 В режиме асинхронной обработки на основе уведомлений необходимо вызывать **S'LCompleteAsync** после того, как менеджер драйвера поднимает объект события, используемый для уведомления. **SLCompleteAsync** завершает асинхронную обработку, а асинхронная функция генерирует код возврата.  
  
 В режиме асинхронной обработки на основе **опроса, S'LCompleteAsync** является альтернативой вызову исходной асинхронной функции, без необходимости указывать аргументы в первоначальном асинхронном вызове функции. **СЗЛПолИАсин** может быть использован независимо от того, включена ли библиотека ODBC Cursor.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLCompleteAsync(  
      SQLSMALLINT HandleType,  
      SQLHANDLE   Handle,  
      RETCODE *   AsyncRetCodePtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HandleType*  
 (Вход) Тип ручки, на которой выполняется асинхронная обработка. Допустимые значения являются SQL_HANDLE_DBC или SQL_HANDLE_STMT.  
  
 *Дескриптор*  
 (Вход) Ручка, на которой выполняется асинхронная обработка. Если *ручка* не является действительной ручкой типа, указанного *HandleType,* **s'LCompleteAsync** возвращается SQL_INVALID_HANDLE.  
  
 Если *ручка* не является действительной ручкой типа, указанного *HandleType,* **s'LCompleteAsync** возвращается SQL_INVALID_HANDLE.  
  
 *AsyncRetCodePtr*  
 (Выход) Указатель на буфер, который будет содержать код возврата асинхронного API. Если *AsyncRetCodePtr* является NULL, **S'LCompleteAsync** возвращается SQL_ERROR.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_ERROR, SQL_NO_DATA или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Если **S'LCompleteAsync** возвращается SQL_SUCCESS, приложение должно получить код возврата асинхронной функции из буфера, на который указывает *AsyncRetCodePtr.* Связанные с этим S'LSTATE, если таковые имеются, могут быть получены, позвонив по **телефону S'LGetDiagRec** с *помощью* SQL_HANDLE_STMT и ручки выписки или *ручки связи HandleType* of SQL_HANDLE_DBC и ручкой соединения. Эти диагностические записи связаны с асинхронной функцией, а не с этой функцией **S'LCompleteAsync.**  
  
 **SLCompleteAsync** возвращает код, отличный от SQL_SUCCESS, чтобы указать, что **S'LCompleteAsync** не вызывается правильно. В этом случае **sLCompleteAsync** не будет размещать диагностическую запись. Возможные коды возврата:  
  
-   SQL_INVALID_HANDLE: Ручка, указанная *HandleType* и *Handle,* не является действительной ручкой.  
  
-   SQL_ERROR: *AsyncRetCodePtr* является NULL или асинхронная обработка не включена на ручке.  
  
-   SQL_NO_DATA: В режиме уведомления асинхронная операция не выполняется или менеджер драйвера не уведомил приложение. В режиме опроса асинхронная операция не выполняется.  
  
## <a name="comments"></a>Комментарии  
 В режиме асинхронной обработки на основе опроса *AsyncRetCodePtr* может быть SQL_STILL_EXECUTING, когда **s'LCompleteAsync** возвращается SQL_SUCCESS. Приложение должно держать опрос до тех пор, пока *AsyncRetCodePtr* не будет SQL_STILL_EXECUTING. В режиме асинхронной обработки на основе уведомлений *AsyncRetCodePtr* никогда не будет SQL_STILL_EXECUTING.  
  
## <a name="see-also"></a>См. также:  
 [Асинхронное исполнение (Метод опроса)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
