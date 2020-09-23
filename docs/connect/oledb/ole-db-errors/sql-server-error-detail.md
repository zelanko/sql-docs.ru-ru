---
title: Сведения об ошибке SQL Server (драйвер OLE DB)
description: Сведения об интерфейсе ошибок конкретного поставщика ISQLServerErrorInfo в драйвере OLE DB Driver for SQL Server, который возвращает сведения об ошибке SQL Server.
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f532b124fa23a65a71480b4bcb1bf31272a3081e
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862220"
---
# <a name="sql-server-error-detail"></a>Подробные сведения об ошибках SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB Driver for SQL Server предоставляет зависящий от поставщика интерфейс для обработки ошибок [ISQLServerErrorInfo](https://docs.microsoft.com/sql/connect/oledb/ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db?view=sql-server-ver15). Интерфейс возвращает более подробные сведения об ошибке [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и полезен, если выполнение команды или операции работы с наборами строк завершились с ошибкой.  
  
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
  
|Участник|Description|  
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
  
  
