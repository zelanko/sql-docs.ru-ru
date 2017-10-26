---
title: "Функция SQLCompleteAsync | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQLCompleteAsync
helpviewer_keywords:
- SQLCompleteAsync function [ODBC]
ms.assetid: 1b97c46a-d2e5-4540-8239-9d975e5321c6
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 83f44395e0c7ed8d102bee046b19aefe96c156b5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlcompleteasync-function"></a>Функция SQLCompleteAsync
**Соответствия**  
 Появился в версии: ODBC 3.8  
  
 Соответствие стандартам: нет  
  
 **Сводка**  
 **SQLCompleteAsync** можно использовать для определения по завершении асинхронной функции с помощью либо обработки, основанных на уведомления или опроса. Дополнительные сведения об асинхронных операциях см. в разделе [асинхронное выполнение](../../../odbc/reference/develop-app/asynchronous-execution.md).  
  
 **SQLCompleteAsync** реализована только диспетчер драйверов ODBC.  
  
 В режиме асинхронной обработки на основе уведомлений **SQLCompleteAsync** должен вызываться после того, диспетчер драйверов вызывает объект события для уведомления. **SQLCompleteAsync** завершает асинхронную обработку и асинхронные функции создают код возврата.  
  
 В режиме асинхронной обработки на основе опроса **SQLCompleteAsync** является альтернативой вызов исходной асинхронной функции, без необходимости указания аргументов в вызове исходного асинхронной функции. **SQLCompleteAsync** может использоваться независимо от того, включение библиотеку курсоров ODBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
  
SQLRETURN SQLCompleteAsync(  
      SQLSMALLINT HandleType,  
      SQLHANDLE   Handle,  
      RETCODE *   AsyncRetCodePtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HandleType*  
 [Вход] Тип дескриптора, на котором для выполнения асинхронной обработки. Допустимые значения: SQL_HANDLE_DBC или значение SQL_HANDLE_STMT.  
  
 *Дескриптор*  
 [Вход] Дескриптор для выполнения асинхронной обработки. Если *обработки* не является допустимым дескриптором типа, заданного параметром *HandleType*, **SQLCompleteAsync** возвращает SQL_INVALID_HANDLE.  
  
 Если *обработки* не является допустимым дескриптором типа, заданного параметром *HandleType*, **SQLCompleteAsync** возвращает SQL_INVALID_HANDLE.  
  
 *AsyncRetCodePtr*  
 [Выход] Указатель на буфер, который будет содержать код возврата асинхронный интерфейс API. Если *AsyncRetCodePtr* имеет значение NULL, **SQLCompleteAsync** возвращает значение SQL_ERROR.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_ERROR, SQL_NO_DATA или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Если **SQLCompleteAsync** возвращает SQL_SUCCESS, приложение должно получить код возврата асинхронной функции из буфера, на который указывает *AsyncRetCodePtr*. Связанные SQLSTATE, если таковые имеются, можно получить путем вызова **SQLGetDiagRec** с *HandleType* значение SQL_HANDLE_STMT и дескриптора инструкции или *HandleType* из SQL_ HANDLE_DBC и дескриптор соединения. Эти диагностические записи связаны с асинхронной функции, не это **SQLCompleteAsync** функции.  
  
 **SQLCompleteAsync** возвращает код, отличный от SQL_SUCCESS, чтобы указать, что **SQLCompleteAsync** не вызывается. **SQLCompleteAsync** не будут отправлены любые диагностические записи в этом случае. Ниже приведены возможные коды возврата.  
  
-   SQL_INVALID_HANDLE: Дескриптор обозначается *HandleType* и *обработки* не является допустимым дескриптором.  
  
-   Значение SQL_ERROR: *AsyncRetCodePtr* имеет значение NULL или асинхронная обработка не включен для дескриптора.  
  
-   Значение SQL_NO_DATA: В режиме уведомления асинхронная операция не выполняется или диспетчер драйверов не сообщил приложения. В режиме опроса асинхронной операции не выполняется.  
  
## <a name="comments"></a>Комментарии  
 В режиме асинхронной обработки на основе опроса *AsyncRetCodePtr* может быть SQL_STILL_EXECUTING при **SQLCompleteAsync** возвращает SQL_SUCCESS. Приложения должны поддерживать опроса до *AsyncRetCodePtr* не SQL_STILL_EXECUTING. В режиме асинхронной обработки на основе уведомлений *AsyncRetCodePtr* никогда не будет SQL_STILL_EXECUTING.  
  
## <a name="see-also"></a>См. также:  
 [Асинхронное выполнение (метод опроса)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)

