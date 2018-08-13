---
title: ISSAbort::Abort (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSAbort::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
ms.assetid: a5bca169-694b-4895-84ac-e8fba491e479
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 23e7cca6868d61b6a26901b6542732a60776a0e2
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39562831"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Отменяет текущий набор строк и любые пакетные команды, ассоциированные с текущей командой.  
  
**ISSAbort** интерфейс, который предоставляется в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента предоставляет **ISSAbort::Abort** метод, используемый для отмены текущего набора строк, а также все команды в пакетном режиме с командой, первоначально создавшей набор строк, и который еще не завершивших выполнение.  
  
 **ISSAbort** — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерфейс поставщика собственного клиента, доступный с помощью **QueryInterface** на **IMultipleResults** объект, возвращаемый ** ICommand::Execute** или **IOpenRowset::OpenRowset**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>Примечания  
 Если команда, выполнение которой прерывается, принадлежит хранимой процедуре, выполнение этой хранимой процедуры (и любых вызвавших ее процедур, а также командного пакета, из которого производился вызов процедуры) будет прервано. Если сервер в это время передавал клиенту результирующий набор, эта передача будет прекращена. Если клиент не хочет получать результирующий набор, перед освобождением набора строк можно вызвать метод **ISSAbort::Abort** ; это ускорит высвобождение набора строк, но если в это время существует открытая транзакция и ее свойство XACT_ABORT имеет значение ON, при вызове **ISSAbort::Abort** произойдет откат транзакции.  
  
 После того как метод **ISSAbort::Abort** вернет результат S_OK, связанный с ним интерфейс **IMultipleResults** становится непригодным к использованию и вплоть до освобождения в ответ на любые вызовы методов возвращает результат DB_E_CANCELED (кроме методов, определенных для интерфейса **IUnknown** ). Если из интерфейса **IMultipleResults** до вызова метода **Abort** был получен интерфейс **IRowset**, он также входит в непригодное к использованию состояние и в ответ на любые вызовы методов возвращает результат DB_E_CANCELED (кроме методов, определенных для интерфейсов **IUnknown** и **IRowset::ReleaseRows**), пока не будет освобожден успешным вызовом метода **ISSAbort::Abort**.  
  
> [!NOTE]  
>  Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], если состояние сервера XACT_ABORT имеет значение ON, вызов метода **ISSAbort::Abort** при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прекращает все транзакции, явные и неявные, и совершает их откат. Более ранние версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не прекратят текущих транзакций.  
  
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
 Произошла ошибка поставщика; Подробные сведения, используйте [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) интерфейс.  
  
 E_UNEXPECTED  
 Непредвиденный вызов метода. Например, объект находится в состоянии зомби, потому что метод **ISSAbort::Abort** уже был вызван.  
  
 E_OUTOFMEMORY  
 Ошибка, связанная с нехваткой памяти.  
  
## <a name="see-also"></a>См. также  
 [ISSAbort &#40;OLE DB&#41;](http://msdn.microsoft.com/library/7c4df482-4a83-4da0-802b-3637b507693a)  
  
  
