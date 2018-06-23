---
title: ISQLServerErrorInfo::GetErrorInfo (OLE DB) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetErrorInfo method
ms.assetid: 83265c9c-eaf9-41f0-9f73-b0ae0972f0d5
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eb6b9a2967ac5a0a8ecef4c0fca7cdaea831957f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101742"
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
 Указатель на структуру SSERRORINFO. Если происходит сбой метода или не [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сведения, связанные с ошибкой, поставщик не выделяет памяти и гарантирует, что *ppSSErrorInfo* аргумент — указатель null на выходе.  
  
 *ppErrorStrings*[out]  
 Указатель на Юникод-указатель символьной строки. Если происходит сбой метода или не [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сведения, связанные с ошибкой, поставщик не выделяет памяти и гарантирует, что *ppErrorStrings* аргумент — указатель null на выходе. Освобождение *ppErrorStrings* аргумент с **IMalloc::Free** высвобождаются три отдельных строковых члена возвращенной структуры SSERRORINFO, как память выделяется в блоке.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод выполнен успешно.  
  
 E_INVALIDARG  
 Либо *ppSSErrorInfo* или *ppErrorStrings* аргумент имеет значение NULL.  
  
 E_OUTOFMEMORY  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента не удалось выделить достаточно памяти для выполнения запроса.  
  
## <a name="remarks"></a>Примечания  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента выделяет память для строк SSERRORINFO и olechar, КОТОРЫЕ возвращаются переданными пользователем указателями. Потребитель должен освободить эту память с помощью **IMalloc::Free** метод, когда он больше не требуется доступ к данным ошибки.  
  
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
|*pwszMessage*|Сообщение об ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это сообщение возвращается через **IErrorInfo::GetDescription** метод.|  
|*pwszServer*|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], где произошла ошибка.|  
|*pwszProcedure*|Имя сформировавшей ошибку хранимой процедуры, если эта ошибка произошла в хранимой процедуре; иначе пустая строка.|  
|*lNative*|Номер ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Номер ошибки идентичен возвращается в *plNativeError* параметр **ISQLErrorInfo::GetSQLInfo** метод.|  
|*bState*|Состояние ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*bClass*|Степень серьезности ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|Если это применимо, строка хранимой процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая сформировала сообщение об ошибке. Если ошибка не связана с процедурой, значение по умолчанию составляет 1.|  
  
 Указатели в структуре ссылаться адреса в строке, возвращенной в *ppErrorStrings* аргумент.  
  
## <a name="see-also"></a>См. также  
 [ISQLServerErrorInfo &#40;OLE DB&#41;](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)   
 [RAISERROR (Transact-SQL)](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
