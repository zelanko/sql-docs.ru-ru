---
title: Функция SQLRateConnection | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLRateConnection function [ODBC]
ms.assetid: e8da2ffb-d6ef-4ca7-824f-57afd29585d8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f6db1bd9703229ba6e2833865bad44494b9ecc3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlrateconnection-function"></a>Функция SQLRateConnection
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 3,81 ODBC: ODBC  
  
 **Сводка**  
 **SQLRateConnection** определяет, если драйвер можно повторно использовать существующее соединение в пуле соединений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SQLRETURN  SQLRateConnection(  
                SQLHDBC_INFO_TOKEN   hRequest,  
                SQLHDBC              hCandidateConnection,  
                BOOL                 fRequiredTransactionEnlistment,  
                TRANSID              transId,  
                DWORD *              pRating );  
```  
  
## <a name="arguments"></a>Аргументы  
 *hRequest*  
 [Вход] Дескриптор токена, представляющий новый запрос подключения приложения.  
  
 *hCandidateConnection*  
 [Вход] Существующие соединения в пуле соединений. Соединение должно быть открыто.  
  
 *fRequiredTransactionEnlistment*  
 [Вход] Значение TRUE, если повторное использование существующего подключения *hCandidateConnection* новый запрос подключения (*hRequest*) требует дополнительных прикрепления.  
  
 *Проводки*  
 [Вход] Если *fRequiredTransactionEnlistment* имеет значение TRUE, *проводки* представляет, запрос будет прикреплен транзакции DTC. Если *fRequiredTransactionEnlistment* имеет значение FALSE, *проводки* будет игнорироваться.  
  
 *pRating*  
 [Выход] *hCandidateConnection*повторного использования оценка для *hRequest*. Эта оценка будет находиться между 0 и 100 (включительно).  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Диспетчер драйверов не будет обрабатывать диагностических сведений, возвращаемых этой функцией.  
  
## <a name="remarks"></a>Замечания  
 **SQLRateConnection** формирует оценку от 0 до 100 (включительно), показывающее, насколько хорошо существующее подключение соответствует запрос.  
  
|Оценка|Значение (когда возвращается значение SQL_SUCCESS)|  
|-----------|-----------------------------------------------|  
|0|*hCandidateConnection* не должны использоваться повторно для *hRequest*.|  
|Все значения в диапазоне от 1 до 98 (включительно)|Чем выше оценка, тем ближе, *hCandidateConnection* соответствует *hRequest*.|  
|99|Есть только несоответствия в незначащие атрибуты.  Диспетчер драйверов следует остановить цикла оценки.|  
|100|Найденного совпадения.  Диспетчер драйверов следует остановить цикла оценки.|  
|Любое другое значение, больше чем 100|*hCandidateConnection* помечается как сообщений и он не будут использоваться повторно даже в запросе будущих соединений.|  
  
 Диспетчера драйверов отметит соединения как сообщений, если код возврата отличное от SQL_SUCCESS (включая SQL_SUCCESS_WITH_INFO) или оценка больше 100. Что неработающего соединения не будут использоваться повторно (даже в будущие запросы на подключение) и будет со временем ожидания по истечении CPTimeout. Диспетчер драйверов будут продолжать найти другое соединение из пула скорость.  
  
 Если диспетчер драйверов повторно соединение, результат строго меньше, чем 100 (включая 99), диспетчер драйверов вызывает SQLSetConnectAttr(SQL_ATTR_DBC_INFO_TOKEN) на сброс подключения обратно в состоянии, запрошенный приложением. Драйвер не должен сбросить подключение при вызове этой функции.  
  
 Если *fRequiredTransactionEnlistment* имеет значение TRUE, повторное использование *hCandidateConnection* требуется дополнительный прикрепления (*проводки* ! = NULL) или unenlistment ( *Проводки* == NULL). Это указывает на стоимость повторное использование соединения и ли драйвер следует прикрепить / исключить соединение из оно соединения, если он будет повторно использовать подключение. Если *fRequireTransactionEnlistment* имеет значение FALSE, драйвер не следует использовать значение *проводки*.  
  
 Диспетчер драйверов гарантирует, что родительский HENV handle *hRequest* и *hCandidateConnection* совпадают. Диспетчер драйверов гарантирует, что идентификатор пула, связанный с *hRequest* и *hCandidateConnection* совпадают.  
  
 Приложения не должны напрямую вызывать эту функцию. Драйвер ODBC, который поддерживает пулы соединений с учетом драйвера необходимо реализовать эту функцию.  
  
 Включить sqlspi.h для разработки драйвера ODBC.  
  
## <a name="see-also"></a>См. также  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Организация пулов соединений с учетом драйвера](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
