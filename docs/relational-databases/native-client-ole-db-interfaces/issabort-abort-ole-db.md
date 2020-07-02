---
title: ISSAbort::Abort (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSAbort::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
ms.assetid: a5bca169-694b-4895-84ac-e8fba491e479
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 835b526053bbf524f2b3d5a87ffea855aaad10c9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785380"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Отменяет текущий набор строк и любые пакетные команды, ассоциированные с текущей командой.  
  
Интерфейс **ISSAbort** , доступ к которому обеспечивает поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , предоставляет метод **ISSAbort::Abort** , используемый для отмены текущего набора строк, а также любых команд, находящихся в одном пакете с командой, первоначально создавшей этот набор строк, и еще не завершивших выполнение.  
  
 Интерфейс**ISSAbилиt** является специфичным для поставщика собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; доступ к этому интерфейсу можно получить с помощью метода **QueryInterface** интерфейса **IMultipleResults** объекта, возвращенного методом **ICommand::Execute** или **IOpenRowset::OpenRowset**.  
  
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
 Произошла ошибка конкретного поставщика; для получения дополнительных сведений используйте интерфейс [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) .  
  
 E_UNEXPECTED  
 Непредвиденный вызов метода. Например, объект находится в состоянии зомби, потому что метод **ISSAbort::Abort** уже был вызван.  
  
 E_OUTOFMEMORY  
 Ошибка, связанная с нехваткой памяти.  
  
## <a name="see-also"></a>См. также  
 [ISSAbort &#40;OLE DB&#41;](https://msdn.microsoft.com/library/7c4df482-4a83-4da0-802b-3637b507693a)  
  
  
