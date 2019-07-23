---
title: SQL Server сведения об ошибке | Документация Майкрософт
description: Подробные сведения об ошибках SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
author: pmasl
ms.author: pelopes
ms.openlocfilehash: ddc9a1b1a242f9a92b1e854520d16abeb7baf809
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015650"
---
# <a name="sql-server-error-detail"></a>Подробные сведения об ошибках SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server определяет определяемый поставщиком интерфейс ошибок [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1). Интерфейс возвращает более подробные сведения об ошибке [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и полезен, если выполнение команды или операции работы с наборами строк завершились с ошибкой.  
  
 Существует два способа получения доступа к интерфейсу **ISQLServerErrorInfo**.  
  
 Как показано в приведенном ниже образце кода, потребитель может вызвать метод **IErrorRecords::GetCustomerErrorObject**, чтобы получить указатель на интерфейс **ISQLServerErrorInfo**. (Нет необходимости получать интерфейс **ISQLErrorInfo**.) Интерфейсы **ISQLErrorInfo** и **ISQLServerErrorInfo** представляют собой пользовательские объекты ошибок OLE DB. При этом объект **ISQLServerErrorInfo** является интерфейсом для получения информации об ошибках на сервере, включая такие данные, как имя процедуры и номера строк.  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 Другой способ получить указатель на интерфейс **ISQLServerErrorInfo** состоит в вызове метода **QueryInterface** для уже полученного указателя на интерфейс **ISQLErrorInfo**. Обратите внимание на то, что так как интерфейс **ISQLServerErrorInfo** содержит надмножество информации, доступной из интерфейса **ISQLErrorInfo**, имеет смысл получить непосредственно интерфейс **ISQLServerErrorInfo** с помощью метода **GetCustomerErrorObject**.  
  
 Интерфейс **ISQLServerErrorInfo** предоставляет одну функцию-член [ISQLServerErrorInfo::GetErrorInfo](../../oledb/ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md). Функция возвращает указатель на структуру SSERRORINFO и указатель на буфер строк. Оба указателя ссылаются на память, которую потребитель должен освободить с помощью метода **IMalloc::Free**.  
  
 Элементы структуры SSERRORINFO обрабатываются потребителем следующим образом.  
  
|Член|Описание|  
|------------|-----------------|  
|*pwszMessage*|Сообщение об ошибке [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Идентично строке, возвращаемой методом **IErrorInfo::GetDescription**.|  
|*pwszServer*|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для сеанса.|  
|*pwszProcedure*|При необходимости, имя процедуры, в которой произошла ошибка. Пустая строка в противном случае.|  
|*lNative*|Номер собственной ошибки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Идентичен значению, возвращаемому в параметре *plNativeError* метода **ISQLErrorInfo::GetSQLInfo**.|  
|*bState*|Состояние сообщения об ошибке [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|*bClass*|Серьезность сообщения об ошибке [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|Если применимо, номер строки хранимой процедуры, в которой возникла ошибка.|  
  
## <a name="see-also"></a>См. также:  
 [Ошибки](../../oledb/ole-db-errors/errors.md)   
 [RAISERROR (Transact-SQL)](../../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
