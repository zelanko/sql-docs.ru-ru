---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ee8f9b9879a3533e8196bbc89f8ae0b0a132293a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036095"
---
# <a name="sqlcleanupconnectionpoolid-function"></a>Функция SQLCleanupConnectionPoolID
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 3,81: ODBC  
  
 **Сводка**  
 **Склклеанупконнектионпулид** информирует драйвер о том, что истекло время ожидания для идентификатора пула. Время ожидания для идентификатора пула может исключаться при превышении времени истечения всех подключений в пуле, связанных с этим ИДЕНТИФИКАТОРом пула. Дополнительные сведения о времени ожидания подключения см. [в статье Использование пулов в компонентах доступа к данным Microsoft](https://msdn.microsoft.com/library/ms810829.aspx) .  
  
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
  
## <a name="returns"></a>Возвращает  
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
