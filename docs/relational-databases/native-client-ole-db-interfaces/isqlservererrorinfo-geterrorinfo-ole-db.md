---
title: ISQLServerErrorInfo::GetErrorInfo (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
apitype: COM
helpviewer_keywords:
- GetErrorInfo method
ms.assetid: 83265c9c-eaf9-41f0-9f73-b0ae0972f0d5
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0a157d42f4bb464cef821f344d0218ecd150e76f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410605"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a>ISQLServerErrorInfo::GetErrorInfo (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Возвращает указатель на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SSERRORINFO поставщика OLE DB для собственного клиента структуру, содержащую [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сведения об ошибке.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента определяет **ISQLServerErrorInfo** Ошибка интерфейса. Этот интерфейс возвращает сведения из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возникновения ошибки, включая уровень серьезности и состояние.  

  
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
 Указатель на Юникод-указатель символьной строки. Если происходит сбой метода или не [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сведения, связанные с ошибкой, поставщик не выделяет памяти и гарантирует, что *ppErrorStrings* аргумент — указатель null на выходе. Освобождение *ppErrorStrings* аргумент с **IMalloc::Free** метод освобождает три отдельных строковых члены возвращаемой структуры SSERRORINFO, поскольку память выделяется в блоке.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод выполнен успешно.  
  
 E_INVALIDARG  
 Либо *ppSSErrorInfo* или *ppErrorStrings* аргумент имел значение NULL.  
  
 E_OUTOFMEMORY  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента не удалось выделить достаточно памяти для выполнения запроса.  
  
## <a name="remarks"></a>Примечания  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента выделяет память для строк SSERRORINFO и olechar, которые ВОЗВРАЩАЮТСЯ переданными пользователем указателями. Потребитель должен освободить эту память с помощью **IMalloc::Free** метод, если он больше не требуется доступ к данным ошибки.  
  
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
|*lNative*|Номер ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Номер ошибки идентичен, возвращаемых в *plNativeError* параметр **ISQLErrorInfo::GetSQLInfo** метод.|  
|*bState*|Состояние ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*bClass*|Степень серьезности ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|Если это применимо, строка хранимой процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая сформировала сообщение об ошибке. Если ошибка не связана с процедурой, значение по умолчанию составляет 1.|  
  
 Указатели в структуре ссылаются на адреса в строке, возвращаемой *ppErrorStrings* аргумент.  
  
## <a name="see-also"></a>См. также  
 [ISQLServerErrorInfo &#40;OLE DB&#41;](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)   
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
