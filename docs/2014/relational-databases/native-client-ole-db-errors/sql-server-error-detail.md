---
title: Подробные сведения об ошибках SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
ms.assetid: 51500ee3-3d78-47ec-b90f-ebfc55642e06
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5c7535e4579204834fc8024b7c37c46675320b8f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63156391"
---
# <a name="sql-server-error-detail"></a>Подробные сведения об ошибках SQL Server
  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента определяет определяемый поставщиком интерфейс ошибок [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md). Интерфейс возвращает более подробные сведения об ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и полезен, если выполнение команды или операции работы с наборами строк завершились с ошибкой.  
  
 Существует два способа получения доступа к интерфейсу **ISQLServerErrorInfo**.  
  
 Как показано в приведенном ниже образце кода, потребитель может вызвать метод **IErrorRecords::GetCustomerErrorObject**, чтобы получить указатель на интерфейс **ISQLServerErrorInfo**. (Нет необходимости получать интерфейс **ISQLErrorInfo**.) Интерфейсы **ISQLErrorInfo** и **ISQLServerErrorInfo** представляют собой пользовательские объекты ошибок OLE DB. При этом объект **ISQLServerErrorInfo** является интерфейсом для получения информации об ошибках на сервере, включая такие данные, как имя процедуры и номера строк.  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 Другой способ получить указатель на интерфейс **ISQLServerErrorInfo** состоит в вызове метода **QueryInterface** для уже полученного указателя на интерфейс **ISQLErrorInfo**. Обратите внимание на то, что так как интерфейс **ISQLServerErrorInfo** содержит надмножество информации, доступной из интерфейса **ISQLErrorInfo**, имеет смысл получить непосредственно интерфейс **ISQLServerErrorInfo** с помощью метода **GetCustomerErrorObject**.  
  
 Интерфейс **ISQLServerErrorInfo** предоставляет одну функцию-член [ISQLServerErrorInfo::GetErrorInfo](../native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md). Функция возвращает указатель на структуру SSERRORINFO и указатель на буфер строк. Оба указателя ссылаются на память, которую потребитель должен освободить с помощью метода **IMalloc::Free**.  
  
 Элементы структуры SSERRORINFO обрабатываются потребителем следующим образом.  
  
|Участник|Описание|  
|------------|-----------------|  
|*pwszMessage*|Сообщение об ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Идентично строке, возвращаемой методом **IErrorInfo::GetDescription**.|  
|*pwszServer*|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для сеанса.|  
|*pwszProcedure*|При необходимости, имя процедуры, в которой произошла ошибка. Пустая строка в противном случае.|  
|*lNative*|Номер собственной ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Идентичен значению, возвращаемому в параметре *plNativeError* метода **ISQLErrorInfo::GetSQLInfo**.|  
|*bState*|Состояние сообщения об ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*bClass*|Серьезность сообщения об ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|Если применимо, номер строки хранимой процедуры, в которой возникла ошибка.|  
  
## <a name="see-also"></a>См. также  
 [Наличии](errors.md)   
 [RAISERROR (Transact-SQL)](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
