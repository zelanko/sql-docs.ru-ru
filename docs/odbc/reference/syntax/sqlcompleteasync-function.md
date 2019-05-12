---
title: Функция SQLCompleteAsync | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 736867be33531a73c0ada66a3be0f1245f1c483a
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537601"
---
# <a name="sqlcompleteasync-function"></a>Функция SQLCompleteAsync
**Соответствие стандартам**  
 Представленные версии: ODBC 3.8  
  
 Соответствие стандартам: None  
  
 **Сводка**  
 **SQLCompleteAsync** может использоваться для определения, по завершении асинхронной функции с помощью либо обработки на основе уведомлений или опроса. Дополнительные сведения об асинхронных операциях см. в разделе [асинхронное выполнение](../../../odbc/reference/develop-app/asynchronous-execution.md).  
  
 **SQLCompleteAsync** реализована только диспетчер драйверов ODBC.  
  
 В режиме асинхронной обработки на основе уведомлений **SQLCompleteAsync** следует вызывать после диспетчер драйверов вызывает объект события, используемый для уведомления. **SQLCompleteAsync** завершает асинхронную обработку и асинхронная функцию создаст код возврата.  
  
 В режиме опроса на основе асинхронной обработки **SQLCompleteAsync** является альтернативой для вызова исходной асинхронные функции без указания аргументов в исходном вызове асинхронной функции. **SQLCompleteAsync** может использоваться независимо от того, отвечает за включение библиотеки курсоров ODBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLCompleteAsync(  
      SQLSMALLINT HandleType,  
      SQLHANDLE   Handle,  
      RETCODE *   AsyncRetCodePtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HandleType*  
 [Вход] Тип токена, на котором для завершения асинхронной обработки. Допустимые значения: SQL_HANDLE_DBC или значение SQL_HANDLE_STMT.  
  
 *Дескриптор*  
 [Вход] Дескриптор, на котором для завершения асинхронной обработки. Если *обрабатывать* не является допустимым дескриптором типа, заданного параметром *HandleType*, **SQLCompleteAsync** возвращает SQL_INVALID_HANDLE.  
  
 Если *обрабатывать* не является допустимым дескриптором типа, заданного параметром *HandleType*, **SQLCompleteAsync** возвращает SQL_INVALID_HANDLE.  
  
 *AsyncRetCodePtr*  
 [Выход] Указатель на буфер, который будет содержать код возврата асинхронный интерфейс API. Если *AsyncRetCodePtr* имеет значение NULL, **SQLCompleteAsync** возвращает ошибку SQL_ERROR.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, значение SQL_ERROR, SQL_NO_DATA или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Если **SQLCompleteAsync** возвращает SQL_SUCCESS, приложение должно получить код возврата асинхронной функции из буфера, на которые указывают *AsyncRetCodePtr*. Связанные SQLSTATE, если таковые имеются, можно получить, вызвав **SQLGetDiagRec** с *HandleType* SQL_HANDLE_STMT и дескриптора инструкции или *HandleType* из SQL_ HANDLE_DBC и дескриптор соединения. Эти диагностические записи связаны с асинхронной функцией, не это **SQLCompleteAsync** функции.  
  
 **SQLCompleteAsync** возвращает код, отличный от SQL_SUCCESS, чтобы указать, что **SQLCompleteAsync** выполняется неправильно. **SQLCompleteAsync** не будет учитывать любые диагностические записи в этом случае. Ниже приведены возможные коды возврата.  
  
-   SQL_INVALID_HANDLE: Указывает дескриптор *HandleType* и *обрабатывать* не является допустимым дескриптором.  
  
-   ЗНАЧЕНИЕ SQL_ERROR: *AsyncRetCodePtr* имеет значение NULL или асинхронной обработки не включен для дескриптора.  
  
-   SQL_NO_DATA: В режиме уведомлений асинхронная операция не выполняется, или диспетчер драйверов не получал уведомление о приложения. В режиме опроса асинхронной операции не выполняется.  
  
## <a name="comments"></a>Комментарии  
 В режиме опроса на основе асинхронной обработки *AsyncRetCodePtr* может быть SQL_STILL_EXECUTING при **SQLCompleteAsync** возвращает значение SQL_SUCCESS. Приложения должны периодически опрашивать до *AsyncRetCodePtr* не SQL_STILL_EXECUTING. В режиме асинхронной обработки на основе уведомлений *AsyncRetCodePtr* никогда не будет SQL_STILL_EXECUTING.  
  
## <a name="see-also"></a>См. также  
 [Асинхронное выполнение (метод опроса)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
