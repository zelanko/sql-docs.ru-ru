---
title: Функция SLRateConnection (англ. Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d29033460a7f89fc4a8b1c371a4d32bdf94a2a05
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288884"
---
# <a name="sqlrateconnection-function"></a>Функция SQLRateConnection
**Соответствия**  
 Версия Введена: СООТВЕТСТВИе стандартам ODBC 3.81: ODBC  
  
 **Сводка**  
 **SLRateConnection** определяет, может ли драйвер повторно использовать существующее соединение в пуле соединения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
  
SQLRETURN  SQLRateConnection(  
                SQLHDBC_INFO_TOKEN   hRequest,  
                SQLHDBC              hCandidateConnection,  
                BOOL                 fRequiredTransactionEnlistment,  
                TRANSID              transId,  
                DWORD *              pRating );  
```  
  
## <a name="arguments"></a>Аргументы  
 *hЗапрос*  
 (Вход) Ручка маркера, представляющая новый запрос на подключение приложения.  
  
 *hCandidateConnection*  
 (Вход) Существующее соединение в пуле соединения. Соединение должно находиться в открытом состоянии.  
  
 *fRequiredТранзакцияЗаягнет*  
 (Вход) Если true, повторное использование *существующего подключения hCandidateConnection* для нового запроса соединения *(hRequest*) требует дополнительного зачисления.  
  
 *transId*  
 (Вход) Если *fRequiredTransactionEnlistment* является правдой, *transId* представляет транзакцию DTC, которую завербует запрос. Если *fRequiredTransactionЗаявевой* является FALSE, *transId* будет проигнорирован.  
  
 *pRating*  
 (Выход) *hCandidateConnection*'s рейтинг повторного использования для *hRequest*. Этот рейтинг будет в период между 0 и 100 (включительно).  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Менеджер драйвера не обрабатывает диагностическую информацию, возвращенную из этой функции.  
  
## <a name="remarks"></a>Remarks  
 **SLRateConnection** производит балл ы от 0 до 100 (включительно), что указывает на то, насколько хорошо существующее соединение соответствует запросу.  
  
|Оценка|Значение (когда SQL_SUCCESS возвращается)|  
|-----------|-----------------------------------------------|  
|0|*hCandidateConnection* не должен использоваться повторно для *hRequest.*|  
|Любые значения от 1 до 98 (включительно)|Чем выше оценка, тем ближе, что *hCandidateConnection* совпадает с *hRequest*.|  
|99|Есть только несоответствия в незначительных атрибутов.  Менеджер драйвера должен остановить цикл рейтинга.|  
|100|Идеальное совпадение.  Менеджер драйвера должен остановить цикл рейтинга.|  
|Любое другое значение, превышающее 100|*hCandidateConnection* помечен как мертвый и не будет повторно использоваться даже в будущем запросе на подключение.|  
  
 Менеджер драйвера будет отмечать соединение как мертвое, если код возврата является чем-то иным, чем SQL_SUCCESS (включая SQL_SUCCESS_WITH_INFO) или рейтинг превышает 100. Это мертвое соединение не будет повторно использоваться (даже в будущих запросах на подключение) и в конечном итоге будет приурочено после пропуска CPTimeout. Менеджер драйвера будет продолжать находить другое соединение из пула для оценить.  
  
 Если менеджер драйвера повторно использовал соединение, оценка которого строго меньше 100 (включая 99), менеджер драйвера вызовет S'LSetConnectAttr (SQL_ATTR_DBC_INFO_TOKEN) для сбросить соединение обратно в состояние, запрошенное приложением. Водитель не должен сбросить соединение в этом вызове функции.  
  
 Если *fRequiredTransactionEnlistment* является правдой, повторное использование *hCandidateConnection* нуждается в дополнительном зачислении *(transId* ! NULL) или незачислении *(transId* - NULL). Это указывает на стоимость повторного использования соединения и должен ли водитель завербовать/отсоединить соединение, если он собирается повторно использовать соединение. Если *fRequireTransactionЗаягвент* является FALSE, водитель должен игнорировать значение *transId.*  
  
 Менеджер драйвера гарантирует, что материнская ручка *HENV hRequest* и *hCandidateConnection* одинаковы. Менеджер драйвера гарантирует, что идентификатор пула, связанный с *hRequest* и *hCandidateConnection,* одинаков.  
  
 Приложения не должны вызывать эту функцию напрямую. Драйвер ODBC, поддерживающий объединение соединения с пониманием водителя, должен реализовать эту функцию.  
  
 Включите sqlspi.h для разработки драйверов ODBC.  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Пулинг соединения с информацией о драйверах](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
