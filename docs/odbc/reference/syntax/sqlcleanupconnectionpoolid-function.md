---
title: Функция S'LCleanupConnectionPoolID Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLCleanupConnectionPoolID function [ODBC]
ms.assetid: 1fc61908-e003-4587-b91a-32f40569fb99
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a74a92cc05ecd41e99ff87642c7fe3ee527e0c98
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301324"
---
# <a name="sqlcleanupconnectionpoolid-function"></a>Функция SQLCleanupConnectionPoolID
**Соответствия**  
 Версия Введена: СООТВЕТСТВИе стандартам ODBC 3.81: ODBC  
  
 **Сводка**  
 **SLCleanupConnectionPoolID** информирует водителя о том, что идентификатор пула был приурочен. Идентификатор пула может тайм-аут всякий раз, когда все соединения в пуле, связанные с этим идентификатором пула, были приурочены. Дополнительную информацию о тайм-ауте можно получить [в компонентах доступа к данным Майкрософт.](https://msdn.microsoft.com/library/ms810829.aspx)  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
  
SQLRETURN  SQLCleanupConnectionPoolID (  
                SQLHENV    EnvironmentHandle  
                SQLPOOLID  PoolID );  
```  
  
## <a name="arguments"></a>Аргументы  
 *Окружающая средаРучка*  
 (Вход) Окружающая ручка бассейна.  
  
 *PoolID*  
 (Вход) Бассейн, связанный с идентификатором пула, который был приурочен.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Менеджер драйвера не обрабатывает диагностическую информацию, возвращенную из **S'LCleanupConnectionPoolID.**  
  
 Приложение не может получить сообщение об ошибке, возвращенное водителем.  
  
## <a name="remarks"></a>Remarks  
 В любое время можно вызвать вызов **sLCleanupConnectionPoolID,** но менеджер драйвера гарантирует, что ни один другой поток одновременно не вызывает **S'LGetPoolID** и ни один другой поток одновременно не вызывает **S'LRateConnection** и **S'LPoolConnect** с токеном информации о подключении, назначенным с этим идентификатором пула. Таким образом, драйвер должен убедиться, что эта функция является безопасной.  
  
 Водитель может очистить ресурсы, связанные с идентификатором пула.  
  
 Приложения не должны вызывать эту функцию напрямую. Драйвер ODBC, поддерживающий объединение соединения с пониманием водителя, должен реализовать эту функцию.  
  
 Включите sqlspi.h для разработки драйверов ODBC.  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Пулинг соединения с информацией о драйверах](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
