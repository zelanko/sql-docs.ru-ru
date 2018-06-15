---
title: Функция SQLAsyncNotificationCallback | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c56aedc9-f7f7-4641-b605-f0f98ed4400c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c785f8547730817c0b1723da38f7ee021aa4f00
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32916981"
---
# <a name="sqlasyncnotificationcallback-function"></a>Функция SQLAsyncNotificationCallback
**Соответствия**  
 Появился в версии: ODBC 3.8  
  
 Соответствие стандартам: нет  
  
 **Сводка**  
 **SQLAsyncNotificationCallback** позволяет драйверу диспетчера драйверов обратного вызова при наличии некоторых ход выполнения для текущей асинхронной операции после драйвер возвращает значение SQL_STILL_EXECUTING. **SQLAsyncNotificationCallback** можно только вызывается драйвером.  
  
 Не вызывайте драйверы **SQLAsyncNotificationCallback** с именем функции **SQLAsyncNotificationCallback**. Вместо этого диспетчер драйверов передает указатель на функцию в драйвер как значение для атрибута SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK или SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK соответствующий дескриптор подключения или дескриптора инструкции соответственно. Различные маркеры можно назначить другой функцией значения указателя. Тип указателя на функцию определяется как SQL_ASYNC_NOTIFICATION_CALLBACK.  
  
 **SQLAsyncNotificationCallback** является потокобезопасным. Драйвер может быть использован несколькими потоками вызов **SQLAsyncNotificationCallback** на разных обрабатывает одновременно.  
  
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
 Использовать драйвер для указывает, что этот вызов функции обратного вызова является последним для текущей асинхронной операции. Драйвер вернет код возврата от SQL_STILL_EXECUTING, когда диспетчер драйверов вызывает функцию еще раз. Диспетчер драйверов использовать эти сведения, например, для оповещения приложения заранее, будет выполнена асинхронная операция.  
  
 Если *обработки* не является допустимым дескриптором типа, заданного параметром *HandleType*, **SQLCancelHandle** возвращает SQL_INVALID_HANDLE.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS или SQL_ERROR.  
  
## <a name="diagnostics"></a>Диагностика  
 **SQLAsyncNotificationCallback** может вернуть значение SQL_ERROR для следующих двух ситуациях (они указывают проблема реализации в драйвере или диспетчера драйверов.  
  
|Ошибка|Описание|  
|-----------|-----------------|  
|Соединение или оператор не запрашивали уведомления.||  
|Недопустимый *обработки*|Драйвер передан недопустимый дескриптор сбой внутреннего диспетчера драйверов проверочные тесты.|  
  
## <a name="see-also"></a>См. также  
 [Асинхронное выполнение (метод опроса)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
