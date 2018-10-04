---
title: ISQLServerErrorInfo::GetErrorInfo (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetErrorInfo method
ms.assetid: 83265c9c-eaf9-41f0-9f73-b0ae0972f0d5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9131c65236a0efffa19aab2bd10b1fd8e309653b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48198384"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a>ISQLServerErrorInfo::GetErrorInfo (OLE DB)
  Возвращает указатель на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SSERRORINFO поставщика OLE DB для собственного клиента структуру, содержащую [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сведения об ошибке.  
  
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
 Либо *ppSSErrorInfo* или *ppErrorStrings* аргумент имел значение NULL.  
  
 E_OUTOFMEMORY  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента не удалось выделить достаточно памяти для выполнения запроса.  
  
## <a name="remarks"></a>Примечания  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента выделяет память для строк SSERRORINFO и olechar, которые ВОЗВРАЩАЮТСЯ переданными пользователем указателями. Пользователь должен освободить эту память с помощью метода **IMalloc::Free**, когда последнему уже не будет требоваться доступ к данным ошибки.  
  
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
  
## <a name="see-also"></a>См. также  
 [ISQLServerErrorInfo &#40;OLE DB&#41;](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)   
 [RAISERROR (Transact-SQL)](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
