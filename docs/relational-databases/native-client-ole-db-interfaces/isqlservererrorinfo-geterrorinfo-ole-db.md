---
title: 'ISQLServerErrorInfo:: Жетерроринфо (OLE DB) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
apitype: COM
helpviewer_keywords:
- GetErrorInfo method
ms.assetid: 83265c9c-eaf9-41f0-9f73-b0ae0972f0d5
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e9ba54dd905127dc87cb3c14f74036c78daae1a1
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73789357"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a>ISQLServerErrorInfo::GetErrorInfo (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Возвращает указатель на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент OLE DB поставщика SSERRORINFO, содержащий сведения об ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет интерфейс для работы с ошибками **ISQLServerErrorInfo** . Этот интерфейс возвращает подробные сведения об ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в том числе уровень серьезности и состояние.  

  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT GetErrorInfo(  
   SSERRORINFO**ppSSErrorInfo,  
   OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a>Аргументы  
 *ppSSErrorInfo*[out]  
 Указатель на структуру SSERRORINFO. Если данный метод не дает результатов или отсутствуют сведения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], связанные с этой ошибкой, поставщик не выделяет памяти и гарантирует, что аргумент *ppSSErrorInfo* при выводе имеет значение NULL.  
  
 *ppErrorStrings*[out]  
 Указатель на Юникод-указатель символьной строки. Если данный метод не дает результатов или отсутствуют сведения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], связанные с этой ошибкой, поставщик не выделяет памяти и гарантирует, что аргумент *ppErrorStrings* при выводе имеет значение NULL. При освобождении аргумента *ppErrorStrings* с помощью метода **IMalloc::Free** высвобождаются три индивидуальных строковых компонента возвращенной структуры SSERRORINFO, так как память выделяется одним блоком.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод выполнен успешно.  
  
 E_INVALIDARG  
 Аргумент *ппссерроринфо* или *пперрорстрингс* имеет значение null.  
  
 E_OUTOFMEMORY  
 Поставщику [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB не удалось выделить достаточно памяти для выполнения запроса.  
  
## <a name="remarks"></a>Замечания  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB выделяет память для строк SSERRORINFO и ОЛЕЧАР, возвращаемых с помощью указателей, переданных потребителем. Пользователь должен освободить эту память с помощью метода **IMalloc::Free**, когда последнему уже не будет требоваться доступ к данным ошибки.  
  
 Структура SSERRORINFO определена следующим образом.  
  
```  
typedef struct tagSSErrorInfo  
   {  
   LPOLESTR pwszMessage;  
   LPOLESTR pwszServer;  
   LPOLESTR pwszProcedure;  
   LONG lNative;  
   BYTE bState;  
   BYTE bClass;  
   WORD wLineNumber;  
   }  
SSERRORINFO;  
```  
  
|Член|Описание|  
|------------|-----------------|  
|*pwszMessage*|Сообщение об ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это сообщение возвращается с помощью метода **IErrorInfo::GetDescription**.|  
|*pwszServer*|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], где произошла ошибка.|  
|*pwszProcedure*|Имя сформировавшей ошибку хранимой процедуры, если эта ошибка произошла в хранимой процедуре; иначе пустая строка.|  
|*lNative*|Номер ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Номер ошибки идентичен номеру, возвращаемому в параметре *plNativeError* метода **ISQLErrorInfo::GetSQLInfo**.|  
|*bState*|Состояние ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*bClass*|Степень серьезности ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|Если это применимо, строка хранимой процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая сформировала сообщение об ошибке. Если ошибка не связана с процедурой, значение по умолчанию составляет 1.|  
  
 Указатели в адресах ссылок на структуры в строке, возвращенной в аргументе *ppErrorStrings*.  
  
## <a name="see-also"></a>См. также раздел  
 [ISQLServerErrorInfo &#40;OLE DB&#41; ](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)   
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
