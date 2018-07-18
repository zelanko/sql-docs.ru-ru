---
title: ISSAbort::Abort (OLE DB) | Документы Microsoft
description: ISSAbort::Abort (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSAbort::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 39f56dd6c058c82783c8cff786e210884cd3bf0c
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690267"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Отменяет текущий набор строк и любые пакетные команды, ассоциированные с текущей командой.  
  
**ISSAbort** предоставляет интерфейс, который предоставляется в драйвер OLE DB для SQL Server, **ISSAbort::Abort** метод, используемый для отмены текущего набора строк, а также все команды в пакетном режиме с помощью команды первоначально создавшей набор строк и который еще не завершивших выполнение.  
  
 **ISSAbort** доступен драйвер OLE DB для SQL Server интерфейса с помощью **QueryInterface** на **IMultipleResults** объект, возвращаемый **ICommand::Execute**  или **IOpenRowset::OpenRowset**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>Примечания  
 Если команда выполняется прерывание в хранимой процедуре, а также пакета команд, который содержит вызов хранимой процедуры прекращается выполнение хранимой процедуры (и все процедуры, которые процедуры). Если сервер находится в процессе передачи результирующего набора для клиента, передача будет остановлен. Если клиент не хочет получать результирующий набор, перед освобождением набора строк можно вызвать метод **ISSAbort::Abort** ; это ускорит высвобождение набора строк, но если в это время существует открытая транзакция и ее свойство XACT_ABORT имеет значение ON, при вызове **ISSAbort::Abort** произойдет откат транзакции.  
  
 После **ISSAbort::Abort** возвращает значение S_OK, связанный с ним **IMultipleResults** интерфейс переходит в нерабочем состоянии и возвращает результат DB_E_CANCELED все вызовы методов (за исключением методов, определенных **IUnknown** интерфейса) до освобождения. Если из интерфейса **IMultipleResults** до вызова метода **Abort** был получен интерфейс **IRowset**, он также входит в непригодное к использованию состояние и в ответ на любые вызовы методов возвращает результат DB_E_CANCELED (кроме методов, определенных для интерфейсов **IUnknown** и **IRowset::ReleaseRows**), пока не будет освобожден успешным вызовом метода **ISSAbort::Abort**.  
  
> [!NOTE]  
>  Начиная с версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], если параметр сервера XACT_ABORT имеет значение ON, выполнение **ISSAbort::Abort** завершить работу и откат текущей неявные или явные транзакции, при подключении к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Более ранние версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не прекратят текущих транзакций.  
  
## <a name="arguments"></a>Аргументы  
 Нет.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод **ISSAbort::Abort** возвращает значение S_OK, если было прервано выполнение программного пакета, и DB_E_CANTCANCEL в противном случае. Если выполнение программного пакета уже было прервано ранее, возвращается DB_E_CANCELED.  
  
 DB_E_CANCELED  
 Выполнение пакета уже было прервано.  
  
 DB_E_CANTCANCEL  
 Выполнение пакета не было прервано.  
  
 E_FAIL  
 Ошибка поставщика; Дополнительные сведения, используйте [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) интерфейса.  
  
 E_UNEXPECTED  
 Непредвиденный вызов метода. Например, объект находится в состоянии зомби, потому что метод **ISSAbort::Abort** уже был вызван.  
  
 E_OUTOFMEMORY  
 Ошибка, связанная с нехваткой памяти.  
  
  
