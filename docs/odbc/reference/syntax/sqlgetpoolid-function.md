---
title: Функция Склжетпулид | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetPoolID function [ODBC]
ms.assetid: 95a8666a-ad68-4d89-bf65-f2cc797f8820
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 32cc973f4dab5bde7bcedade0365d233987dda72
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303321"
---
# <a name="sqlgetpoolid-function"></a>Функция SQLGetPoolID
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 3,81: ODBC  
  
 **Сводка**  
 **Склжетпулид** получает идентификатор пула.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
  
SQLRETURN  SQLGetPoolID (  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                POOLID *              pPoolID );  
```  
  
## <a name="arguments"></a>Аргументы  
 *хдбЦинфотокен*  
 Входной Маркер маркера, который содержит все сведения о соединении.  
  
 *ппулид*  
 Проверки Идентификатор пула, который используется для идентификации набора соединений, которые могут быть взаимозаменяемы (возможно, требуется дополнительный сброс).  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **склжетпулид** возвращает SQL_ERROR или SQL_SUCCESS_WITH_INFO, диспетчер драйверов будет использовать **параметром handletype** SQL_HANDLE_DBC_INFO_TOKEN и **обработчик** *хдбЦинфотокен*.  
  
## <a name="remarks"></a>Remarks  
 **Склжетпулид** используется для получения идентификатора пула с учетом набора сведений о соединении (из **склсетконнектаттрфордбЦинфо**, **склсетдриверконнектинфо**и **склсетконнектинфо**). Этот идентификатор пула используется для идентификации набора соединений, которые могут быть взаимозаменяемы (возможно, требуется дополнительный сброс). Идентификатор пула будет использоваться для идентификации пула подключений для этой группы соединений.  
  
 Всякий раз, когда драйвер возвращает SQL_ERROR или SQL_INVALID_HANDLE, диспетчер драйверов возвращает ошибку приложению (в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) или [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Всякий раз, когда драйвер возвращает SQL_SUCCESS_WITH_INFO, диспетчер драйверов получает диагностические сведения от *хдбЦинфотокен*и возвращает SQL_SUCCESS_WITH_INFO приложению в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) и [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Приложения не должны вызывать эту функцию напрямую. Драйвер ODBC, поддерживающий пулы соединений с учетом драйверов, должен реализовывать эту функцию.  
  
 Включите склспи. h для разработки драйвера ODBC.  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Организация пулов соединений с учетом драйверов](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
