---
title: Функция S'LAsyncNotificationCallBack back (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c56aedc9-f7f7-4641-b605-f0f98ed4400c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e6c182c48b8e5ddb70204ddd3a94d9651f97595d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294541"
---
# <a name="sqlasyncnotificationcallback-function"></a>Функция SQLAsyncNotificationCallback
**Соответствия**  
 Представлена версия: ODBC 3.8  
  
 Соответствие стандартам: Нет  
  
 **Сводка**  
 **SLAsyncNotificationCallBack** позволяет водителю перезвонить менеджеру драйвера, когда есть некоторый прогресс для текущей асинхронной операции после того, как водитель возвращается SQL_STILL_EXECUTING. **S'LAsyncNotificationCallBack** может вызываться только драйвером.  
  
 Драйверы не вызывают **S'LAsyncNotificationCallBack** с функционеном именем **S'LAsyncNotificationCallBack.** Вместо этого менеджер драйвера передает указатель функции водителю в качестве значения для SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK или SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK атрибута соответствующей ручки соединения или ручки оператора, соответственно. Различным ручкам могут быть назначены различные значения указателя функции. Тип указателя функции определяется как SQL_ASYNC_NOTIFICATION_CALLBACK.  
  
 **S'LAsyncNotificationCallBack** является нит-безопасным. Водитель может использовать несколько потоков, вызывая **S'LAsyncNotificationCallback** на разных ручках одновременно.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef SQLRETURN (SQL_API *SQL_ASYNC_NOTIFICATION_CALLBACK)(  
   SQLPOINTER pContex,   
   BOOL fLast);  
```  
  
## <a name="arguments"></a>Аргументы  
 *pContex*  
 Указатель на структуру данных, определяемую менеджером драйверов. Значение передается водителю через S'LSetConnectAttr (SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT) или S'LSetStmtAttr (SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT).  Водитель не имеет доступа к значению.  
  
 *fLast*  
 Used by a driver to indicates that this callback function invocation is the last one for the current asynchronous operation. Водитель возвращает обратный код, кроме SQL_STILL_EXECUTING, когда менеджер драйвера вызывает функцию снова. Менеджер драйвера может использовать эту информацию, например, для заблаговременного информирования приложения о завершении асинхронной операции.  
  
 Если *ручка* не является действительной ручкой типа, указанной *HandleType,* **s'LCancelHandle** возвращается SQL_INVALID_HANDLE.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS или SQL_ERROR.  
  
## <a name="diagnostics"></a>Диагностика  
 **SLAsyncNotificationCallBack** может вернуть SQL_ERROR в следующих двух ситуациях (они указывают на проблему реализации в драйвере или менеджере драйвера.  
  
|Error|Описание|  
|-----------|-----------------|  
|Подключение или выписка не запрашивали уведомления.||  
|Недействительная *ручка*|Водитель прошел в недействительной ручке, что не удалось внутренней проверки драйвера менеджер испытаний.|  
  
## <a name="see-also"></a>См. также:  
 [Асинхронное исполнение (Метод опроса)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
