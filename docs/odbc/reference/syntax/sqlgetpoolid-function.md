---
title: Функция S'LGetPoolID Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303321"
---
# <a name="sqlgetpoolid-function"></a>Функция SQLGetPoolID
**Соответствия**  
 Версия Введена: СООТВЕТСТВИе стандартам ODBC 3.81: ODBC  
  
 **Сводка**  
 **SQLGetPoolID** Идентификатор пула получает идентификатор пула.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
  
SQLRETURN  SQLGetPoolID (  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                POOLID *              pPoolID );  
```  
  
## <a name="arguments"></a>Аргументы  
 *hDbcInfoToken*  
 (Вход) Ручка маркеров, содержащая всю информацию о подключении.  
  
 *pPoolID*  
 (Выход) Идентификатор пула, который используется для определения набора соединений, которые могут быть использованы взаимозаменяемы (возможно, требует дополнительного сбоя).  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **s'LGetPoolID** возвращается SQL_ERROR или SQL_SUCCESS_WITH_INFO, менеджер драйвера будет использовать **HandleType** SQL_HANDLE_DBC_INFO_TOKEN и **ручку** *hDbcInfoToken*.  
  
## <a name="remarks"></a>Remarks  
 **Для** получения идентификатора пула используется идентификатор пула с набором информации о подключении (от **S'LSetConnectAttrForDbcInfo,** **S'LSetDriverConnectInfo,** и **S'LSetConnectInfo , и S'LSetConnectInfo**). Этот идентификатор пула используется для определения набора соединений, которые могут быть использованы взаимозаменяемы (возможно, требующих дополнительной перезагрузки). Идентификатор пула будет использоваться для определения пула соединения для этой группы соединений.  
  
 Всякий раз, когда водитель возвращает SQL_ERROR или SQL_INVALID_HANDLE, менеджер драйвера возвращает ошибку в приложение (в [S'LConnect](../../../odbc/reference/syntax/sqlconnect-function.md) или [S'LDriverConnect).](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
 Всякий раз, когда водитель возвращается SQL_SUCCESS_WITH_INFO, менеджер драйвера получает диагностическую информацию от *hDbcInfoToken,* и возвращает SQL_SUCCESS_WITH_INFO в приложение в [S'LConnect](../../../odbc/reference/syntax/sqlconnect-function.md) и [S'LDriverConnect.](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
 Приложения не должны вызывать эту функцию напрямую. Драйвер ODBC, поддерживающий объединение соединения с пониманием водителя, должен реализовать эту функцию.  
  
 Включите sqlspi.h для разработки драйверов ODBC.  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Пулинг соединения с информацией о драйверах](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
