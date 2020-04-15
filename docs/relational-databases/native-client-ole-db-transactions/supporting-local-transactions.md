---
title: Поддержка локальных транзакций | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- SQL Server Native Client OLE DB provider, transactions
- local transactions [OLE DB]
ms.assetid: 78f2e5fc-b6fb-4eda-9f71-991a4d6c4902
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8533747bbe5ccb79a06b10a754c4af45ab241843
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280334"
---
# <a name="supporting-local-transactions"></a>Поддержка локальных транзакций
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Сеанс разграничает возможности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] транзакций для локальной транзакции поставщика NATIVE Client OLE DB. Когда по указанию потребителя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик Native Client OLE DB отправляет запрос [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]в подключенный экземпляр, запрос [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] представляет собой единицу работы для поставщика Native Client OLE DB. Локальные транзакции всегда обертывания [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] одного или нескольких единиц работы на одной сессии поставщика Native Client OLE DB.  
  
 Используя режим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматического автоматического обслуживания поставщика автофиксации Native Client OLE DB, единая единица работы рассматривается как область локальной транзакции. В локальной транзакции участвует только одна единица работы. Когда сеанс создается, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик Native Client OLE DB начинает транзакцию для сеанса. При успешном завершении единицы работы выполненная работа фиксируется. При сбое выполняется откат всей начатой работы; потребителю сообщается об ошибке. В любом случае [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик Native Client OLE DB начинает новую локальную транзакцию для сеанса, чтобы вся работа проводилась в рамках транзакции.  
  
 Потребитель-поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB может направить более точный контроль над локальной областью транзакций с помощью интерфейса **ITransactionLocal.** Если сеанс потребителя инициирует транзакцию, все рабочие единицы сеанса между точкой начала транзакции и последующими неизбежными вызовами методов **Commit** или **Abort** рассматриваются как единая операция. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB неявно начинает транзакцию, когда направляет на это потребителя. Если потребитель не запрашивает хранения, сеанс восстанавливает режим родительской транзакции. Как правило, это режим автозавершения.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB поддерживает параметры **ITransactionLocal::StartTransaction** следующим образом.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*isoLevel*[in]|Уровень изоляции, который должен использоваться с этой транзакцией. В локальных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] транзакциях поставщик Native Client OLE DB поддерживает следующее:<br /><br /> **ISOLATIONLEVEL_UNSPECIFIED**<br /><br /> **ISOLATIONLEVEL_CHAOS**<br /><br /> **ISOLATIONLEVEL_READUNCOMMITTED**<br /><br /> **ISOLATIONLEVEL_READCOMMITTED**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_CURSORSTABILITY**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_SERIALIZABLE**<br /><br /> **ISOLATIONLEVEL_ISOLATED**<br /><br /> **ISOLATIONLEVEL_SNAPSHOT**<br /><br /> <br /><br /> Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] уровень изоляции ISOLATIONLEVEL_SNAPSHOT допустим для аргумента *isoLevel* независимо от того, включено ли в базе данных управление версиями. Однако произойдет ошибка, если пользователь попытается выполнить инструкцию, когда управление версиями не включено, а база данных предназначена не только для чтения. Кроме того, ошибка XACT_E_ISOLATIONLEVEL возникнет, если для *isoLevel* задано значение ISOLATIONLEVEL_SNAPSHOT при соединении с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|*isoFlags*[in]|Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращает ошибку для любого значения, кроме нуля.|  
|*pOtherOptions*[in]|Если не NULL, поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB запрашивает объект опций из интерфейса. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращает XACT_E_NOTIMEOUT если участник *ulTimeout* объекта опционов не равен нулю. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB игнорирует значение участника *szDescription.*|  
|*pulTransactionLevel*[out]|Если не NULL, поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращает вложенный уровень транзакции.|  
  
 Для локальных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] транзакций поставщик Native Client OLE DB реализует параметры **ITransaction::Abort** следующим образом.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*pboidReason*[in]|При установке не учитывается. Может иметь значение NULL.|  
|*fRetaining*[in]|Если задано значение TRUE, то для сеанса неявным образом запускается новая транзакция. Эта транзакция должна быть зафиксирована или завершена объектом-получателем. Когда FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик Native Client OLE DB возвращается в режим автоматического обслуживания для сеанса.|  
|*fAsync*[in]|Асинхронный аборт не поддерживается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщиком Native Client OLE DB. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращает XACT_E_NOTSUPPORTED, если значение не FALSE.|  
  
 Для локальных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] транзакций поставщик Native Client OLE DB реализует параметры **ITransaction::Commit** следующим образом.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*fRetaining*[in]|Если задано значение TRUE, то для сеанса неявным образом запускается новая транзакция. Эта транзакция должна быть зафиксирована или завершена объектом-получателем. Когда FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик Native Client OLE DB возвращается в режим автоматического обслуживания для сеанса.|  
|*grfTC*[in]|Асинхронные и первоочередные возвраты не поддерживаются поставщиком [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращает XACT_E_NOTSUPPORTED за любую ценность, кроме XACTTC_SYNC.|  
|*grfRM*[in]|Должно быть равно 0.|  
  
 Строки поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client OLE DB на сеансе сохраняются при локальной операции коммитов или прерывания работы в зависимости DBPROP_ABORTPRESERVE от значений свойств строк и DBPROP_COMMITPRESERVE. По умолчанию эти свойства являются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VARIANT_FALSE и все строки поставщика NATIVE Client OLE DB на сеансе теряются после прерывания или операции коммита.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB не реализует интерфейс **ITransactionObject.** При попытке потребителя получить ссылку на интерфейс возвращается E_NOINTERFACE.  
  
 В этом примере используется интерфейс **ITransactionLocal**.  
  
```  
// Interfaces used in the example.  
IDBCreateSession*   pIDBCreateSession   = NULL;  
ITransaction*       pITransaction       = NULL;  
IDBCreateCommand*   pIDBCreateCommand   = NULL;  
IRowset*            pIRowset            = NULL;  
  
HRESULT             hr;  
  
// Get the command creation and local transaction interfaces for the  
// session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
if (FAILED(hr = pIDBCreateCommand->QueryInterface(IID_ITransactionLocal,  
    (void**) &pITransaction)))  
    {  
    // Process error. Release any references and return.  
    }  
  
// Start the local transaction.  
if (FAILED(hr = ((ITransactionLocal*) pITransaction)->StartTransaction(  
    ISOLATIONLEVEL_REPEATABLEREAD, 0, NULL, NULL)))  
    {  
    // Process error from StartTransaction. Release any references and  
    // return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then terminate.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, XACTTC_SYNC, 0)))  
        {  
        // Get error from failed commit.  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>См. также:  
 [Операций](../../relational-databases/native-client-ole-db-transactions/transactions.md)   
 [Работа с изоляцией моментального снимка](../../relational-databases/native-client/features/working-with-snapshot-isolation.md)  
  
  
