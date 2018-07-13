---
title: ISSAbort::Abort (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSAbort::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: a5bca169-694b-4895-84ac-e8fba491e479
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05673bb90cd0958344a6a12550f15c122489219a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416293"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
  Отменяет текущий набор строк и любые пакетные команды, ассоциированные с текущей командой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>Примечания  
 Если команда, выполнение которой прерывается, принадлежит хранимой процедуре, выполнение этой хранимой процедуры (и любых вызвавших ее процедур, а также командного пакета, из которого производился вызов процедуры) будет прервано. Если сервер в это время передавал клиенту результирующий набор, эта передача будет прекращена. Если клиент не хочет получать результирующий набор, перед освобождением набора строк можно вызвать метод **ISSAbort::Abort** ; это ускорит высвобождение набора строк, но если в это время существует открытая транзакция и ее свойство XACT_ABORT имеет значение ON, при вызове **ISSAbort::Abort** произойдет откат транзакции.  
  
 После того как метод **ISSAbort::Abort** вернет результат S_OK, связанный с ним интерфейс **IMultipleResults** становится непригодным к использованию и вплоть до освобождения в ответ на любые вызовы методов возвращает результат DB_E_CANCELED (кроме методов, определенных для интерфейса **IUnknown** ). Если из интерфейса **IMultipleResults** до вызова метода **Abort** был получен интерфейс **IRowset**, он также входит в непригодное к использованию состояние и в ответ на любые вызовы методов возвращает результат DB_E_CANCELED (кроме методов, определенных для интерфейсов **IUnknown** и **IRowset::ReleaseRows**), пока не будет освобожден успешным вызовом метода **ISSAbort::Abort**.  
  
> [!NOTE]  
>  Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], если сервера XACT_ABORT имеет значение ON, **ISSAbort::Abort** завершит и выполнить откат текущего явного или неявного транзакции при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Более ранние версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не прекратят текущих транзакций.  
  
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
 Произошла ошибка поставщика; Подробные сведения, используйте [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) интерфейс.  
  
 E_UNEXPECTED  
 Непредвиденный вызов метода. Например, объект находится в состоянии зомби, потому что метод **ISSAbort::Abort** уже был вызван.  
  
 E_OUTOFMEMORY  
 Ошибка, связанная с нехваткой памяти.  
  
## <a name="see-also"></a>См. также  
 [ISSAbort &#40;OLE DB&#41;](../../database-engine/dev-guide/issabort-ole-db.md)  
  
  
