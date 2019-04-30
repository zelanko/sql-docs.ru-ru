---
title: Функция SQLAsyncNotificationCallback | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c56aedc9-f7f7-4641-b605-f0f98ed4400c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b78764e1dccb7118d43cc967f3b03838366d6eb0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63224514"
---
# <a name="sqlasyncnotificationcallback-function"></a>Функция SQLAsyncNotificationCallback
**Соответствие стандартам**  
 Представленные версии: ODBC 3.8  
  
 Соответствие стандартам: None  
  
 **Сводка**  
 **SQLAsyncNotificationCallback** позволяет драйверу обратный вызов в диспетчер драйверов, когда имеется наблюдать выполнение некоторых операций для текущей асинхронной операции после драйвер возвращает значение SQL_STILL_EXECUTING. **SQLAsyncNotificationCallback** можно только вызывается с помощью драйвера.  
  
 Не вызывайте драйверы **SQLAsyncNotificationCallback** именем функции **SQLAsyncNotificationCallback**. Вместо этого диспетчер драйверов передает указатель на функцию в драйвер как значение для атрибута SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK или SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK соответствующий дескриптор подключения или дескриптора инструкции соответственно. Маркеров можно назначить значения указателя другую функцию. Тип указателя функции определяется как SQL_ASYNC_NOTIFICATION_CALLBACK.  
  
 **SQLAsyncNotificationCallback** является поточно ориентированной. Драйвер можно использовать несколько потоков вызова **SQLAsyncNotificationCallback** на разных обрабатывает одновременно.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef SQLRETURN (SQL_API *SQL_ASYNC_NOTIFICATION_CALLBACK)(  
   SQLPOINTER pContex,   
   BOOL fLast);  
```  
  
## <a name="arguments"></a>Аргументы  
 *pContex*  
 Указатель на структуру данных, определенные диспетчером драйверов. Значение, передаваемое драйвер через SQLSetConnectAttr(SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT) или SQLSetStmtAttr(SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT).  Драйвер не имеет доступа к значению.  
  
 *fLast*  
 Использовать драйвер для указывает, что этот вызов функции обратного вызова является последним для текущей асинхронной операции. Когда диспетчер драйверов вызывает функцию снова, то драйвер вернет код возврата отличен от SQL_STILL_EXECUTING. Диспетчер драйверов может использовать эти сведения, например, для информирования приложения заранее которая будет выполнена асинхронная операция.  
  
 Если *обрабатывать* не является допустимым дескриптором типа, заданного параметром *HandleType*, **SQLCancelHandle** возвращает SQL_INVALID_HANDLE.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS или SQL_ERROR.  
  
## <a name="diagnostics"></a>Диагностика  
 **SQLAsyncNotificationCallback** может возвращать значение SQL_ERROR для следующих двух ситуациях (они указывают из-за проблемы реализации в драйвере или диспетчера драйверов.  
  
|Ошибка|Описание|  
|-----------|-----------------|  
|Соединение или оператор инициируются без запроса уведомления.||  
|Недопустимый *обработки*|Драйвер передан недопустимый дескриптор, которой не удалось внутреннего диспетчера драйверов проверочные тесты.|  
  
## <a name="see-also"></a>См. также  
 [Асинхронное выполнение (метод опроса)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
