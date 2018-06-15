---
title: ISQLServerErrorInfo::GetErrorInfo (OLE DB) | Документы Microsoft
description: ISQLServerErrorInfo::GetErrorInfo (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
apitype: COM
helpviewer_keywords:
- GetErrorInfo method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 085b171b9987e8546560550fbf9a71eadbf8de31
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35305753"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a>ISQLServerErrorInfo::GetErrorInfo (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Возвращает указатель на драйвер OLE DB для SQL Server SSERRORINFO структура, содержащая [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сведения об ошибке.  
  
 Драйвер OLE DB для SQL Server определяет **ISQLServerErrorInfo** Ошибка интерфейса. Этот интерфейс для извлечения сведений из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ошибку, в том числе уровень серьезности и состояние.  

  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT GetErrorInfo(  
   SSERRORINFO**ppSSErrorInfo,  
   OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a>Аргументы  
 *ppSSErrorInfo*[out]  
 Указатель на структуру SSERRORINFO. Если происходит сбой метода или не [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сведения, связанные с ошибкой, поставщик не выделяет памяти и гарантирует, что *ppSSErrorInfo* аргумент — указатель null на выходе.  
  
 *ppErrorStrings*[out]  
 Указатель на Юникод-указатель символьной строки. Если происходит сбой метода или не [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сведения, связанные с ошибкой, поставщик не выделяет памяти и гарантирует, что *ppErrorStrings* аргумент — указатель null на выходе. Освобождение *ppErrorStrings* аргумент с **IMalloc::Free** высвобождаются три отдельных строковых члена возвращенной структуры SSERRORINFO, как память выделяется в блоке.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод выполнен успешно.  
  
 E_INVALIDARG  
 Либо *ppSSErrorInfo* или *ppErrorStrings* аргумент имеет значение NULL.  
  
 E_OUTOFMEMORY  
 Драйвер OLE DB для SQL Server не удалось выделить достаточно памяти для выполнения запроса.  
  
## <a name="remarks"></a>Примечания  
 Драйвер OLE DB для SQL Server выделяет память для строк SSERRORINFO и olechar, КОТОРЫЕ возвращаются переданными пользователем указателями. Потребитель должен освободить эту память с помощью **IMalloc::Free** метод, когда он больше не требуется доступ к данным ошибки.  
  
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
|*pwszMessage*|Сообщение об ошибке [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Это сообщение возвращается через **IErrorInfo::GetDescription** метод.|  
|*pwszServer*|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], где произошла ошибка.|  
|*pwszProcedure*|Имя сформировавшей ошибку хранимой процедуры, если эта ошибка произошла в хранимой процедуре; иначе пустая строка.|  
|*lNative*|Номер ошибки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Номер ошибки идентичен возвращается в *plNativeError* параметр **ISQLErrorInfo::GetSQLInfo** метод.|  
|*bState*|Состояние ошибки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|*bClass*|Степень серьезности ошибки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|Если это применимо, строка хранимой процедуры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], которая сформировала сообщение об ошибке. Если ошибка не связана с процедурой, значение по умолчанию составляет 1.|  
  
 Указатели в структуре ссылаться адреса в строке, возвращенной в *ppErrorStrings* аргумент.  
  
## <a name="see-also"></a>См. также  
 [ISQLServerErrorInfo &#40;OLE DB&#41;](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)   
 [RAISERROR (Transact-SQL)](../../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
