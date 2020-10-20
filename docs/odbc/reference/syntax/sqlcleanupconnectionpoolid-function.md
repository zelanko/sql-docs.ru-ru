---
description: Функция SQLCleanupConnectionPoolID
title: Функция Склклеанупконнектионпулид | Документация Майкрософт
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
ms.openlocfilehash: 20ad05559aa172ff7e8937359bad93f85347a92a
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92193449"
---
# <a name="sqlcleanupconnectionpoolid-function"></a>Функция SQLCleanupConnectionPoolID
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 3,81: ODBC  
  
 **Сводка**  
 **Склклеанупконнектионпулид** информирует драйвер о том, что истекло время ожидания для идентификатора пула. Время ожидания для идентификатора пула может исключаться при превышении времени истечения всех подключений в пуле, связанных с этим ИДЕНТИФИКАТОРом пула. Дополнительные сведения о времени ожидания подключения см. [в статье Использование пулов в компонентах доступа к данным Microsoft](/previous-versions/ms810829(v=msdn.10)) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
  
SQLRETURN  SQLCleanupConnectionPoolID (  
                SQLHENV    EnvironmentHandle  
                SQLPOOLID  PoolID );  
```  
  
## <a name="arguments"></a>Аргументы  
 *енвиронменсандле*  
 Входной Маркер среды пула.  
  
 *пулид*  
 Входной Пул, связанный с ИДЕНТИФИКАТОРом пула, для которого истекло время ожидания.  
  
## <a name="returns"></a>Возвращаемое значение  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Диспетчер драйверов не будет обрабатывать диагностические данные, возвращенные из **склклеанупконнектионпулид**.  
  
 Приложение не может получить сообщение об ошибке, возвращенное драйвером.  
  
## <a name="remarks"></a>Remarks  
 **Склклеанупконнектионпулид** можно вызывать в любое время, но диспетчер драйверов гарантирует, что ни один другой поток не вызывает **склжетпулид** , а другой поток не вызывает одновременно **склратеконнектион** и **склпулконнект** с маркером сведений о соединении, назначенным этому идентификатору пула. Поэтому драйвер должен убедиться, что эта функция является потокобезопасной.  
  
 Драйвер может очистить ресурсы, связанные с ИДЕНТИФИКАТОРом пула.  
  
 Приложения не должны вызывать эту функцию напрямую. Драйвер ODBC, поддерживающий пулы соединений с учетом драйверов, должен реализовывать эту функцию.  
  
 Включите склспи. h для разработки драйвера ODBC.  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Организация пулов соединений с учетом драйверов](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)