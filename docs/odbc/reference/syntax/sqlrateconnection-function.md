---
title: Функция SQLRateConnection | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLRateConnection function [ODBC]
ms.assetid: e8da2ffb-d6ef-4ca7-824f-57afd29585d8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3d36224329fa29a54f7163cb4e1ce6228f460875
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63262498"
---
# <a name="sqlrateconnection-function"></a>Функция SQLRateConnection
**Соответствие стандартам**  
 Представленные версии: Соответствие стандартам 3,81 ODBC: интерфейс ODBC  
  
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
 [Вход] Дескриптор маркера, представляющий новый запрос на подключение приложения.  
  
 *hCandidateConnection*  
 [Вход] Существующее соединение в пуле соединений. Соединение должно быть открыто.  
  
 *fRequiredTransactionEnlistment*  
 [Вход] Если значение равно TRUE, повторное использование существующего подключения *hCandidateConnection* для нового запроса на подключение (*hRequest*) требует дополнительных перечисления.  
  
 *Проводки*  
 [Вход] Если *fRequiredTransactionEnlistment* имеет значение TRUE, *проводки* представляет транзакции DTC, которая будет прикрепить запроса. Если *fRequiredTransactionEnlistment* имеет значение FALSE, *проводки* будет игнорироваться.  
  
 *pRating*  
 [Выход] *hCandidateConnection*оценка повторное использование для *hRequest*. Эта оценка будет находиться между 0 и 100 (включительно).  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Диспетчер драйверов не будет обрабатывать диагностических сведений, возвращаемых этой функцией.  
  
## <a name="remarks"></a>Примечания  
 **SQLRateConnection** формирует оценку от 0 до 100 (включительно), указывающее, насколько хорошо существующее подключение, которому соответствует запрос.  
  
|Оценка|Значение (когда возвращается значение SQL_SUCCESS, указывая)|  
|-----------|-----------------------------------------------|  
|0|*hCandidateConnection* не должны использоваться повторно для *hRequest*.|  
|Все значения от 1 до 98 (включительно)|Чем выше оценка, тем ближе, *hCandidateConnection* соответствует *hRequest*.|  
|99|Есть только несоответствия в не имеющие значения атрибутов.  Диспетчер драйверов следует остановить цикла оценки.|  
|100|Прекрасным решением.  Диспетчер драйверов следует остановить цикла оценки.|  
|Любое другое значение, большее 100|*hCandidateConnection* помечается как очередь недоставленных сообщений и он не будет использоваться повторно даже в запросе будущие подключения.|  
  
 Диспетчер драйверов пометит соединения как очередь недоставленных сообщений, если код возврата не было присвоено имя, отличное от SQL_SUCCESS, (включая SQL_SUCCESS_WITH_INFO) или оценка превышает 100. Что недействующего соединения не будут использоваться повторно (даже в будущие запросы на подключение) и будет со временем ожидания по истечении CPTimeout. Диспетчер драйверов будут продолжать найти другое соединение из пула скорость.  
  
 Если диспетчер драйверов повторно использовать соединение, результат строго меньше, чем 100 (в том числе 99), диспетчер драйверов вызывает SQLSetConnectAttr(SQL_ATTR_DBC_INFO_TOKEN) на сброс подключения обратно в состояние, запрашиваемой приложением. Драйвер не следует сбрасывать соединение при вызове этой функции.  
  
 Если *fRequiredTransactionEnlistment* имеет значение TRUE, повторное использование *hCandidateConnection* требуется дополнительный зачисления (*проводки* ! = NULL) или unenlistment ( *Проводки* == NULL). Это означает, затраты на повторное использование соединения и ли драйвер должен прикрепить / прикрепление соединения, если он будет повторно использовать подключение. Если *fRequireTransactionEnlistment* имеет значение FALSE, драйвер должен игнорировать значение *проводки*.  
  
 Диспетчер драйверов гарантирует, что родительский маркера HENV *hRequest* и *hCandidateConnection* одинаковы. Диспетчер драйверов гарантирует, что идентификатор пула, связанный с *hRequest* и *hCandidateConnection* одинаковы.  
  
 Приложения не эту функцию следует вызывать напрямую. Драйвер ODBC, который поддерживает пулы соединений с учетом драйвера необходимо реализовать эту функцию.  
  
 Включить sqlspi.h для разработки драйвера ODBC.  
  
## <a name="see-also"></a>См. также  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Организация пулов соединений с учетом драйвера](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
