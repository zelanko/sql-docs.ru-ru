---
title: ISSCommandWithParameters::GetParameterProperties (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d492a64b6d8a4e8ddf7de27067f1f0bcfef205e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140297"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
  Возвращает массив структур SSPARAMPROPS, представляющих собой множества свойств, по одному множеству свойств SSPARAMPROPS на каждый параметр определяемого пользователем типа или XML.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT GetParameterProperties(  
DB_UPARAMS *pcParams,  
SSPARAMPROPS **prgParamProperties);  
```  
  
## <a name="arguments"></a>Аргументы  
 *pcParams*[out][in]  
 Указатель на область памяти, где содержится количество структур SSPARAMPROPS, возвращаемых в параметре *prgParamProperties*.  
  
 *prgParamProperties*[out]  
 Указатель на область памяти, в которую будет возвращен массив структур SSPARAMPROPS. Поставщик выделяет память для структур и возвращает адрес этой памяти; Поставщик высвобождает эту память с помощью **IMalloc::Free** когда он больше не нужна структуры. Перед вызовом **IMalloc::Free** для *prgParamProperties*, он должен также вызвать **VariantClear** для *vValue* свойство каждой структуры DBPROP, чтобы предотвратить утечку памяти в случаях, если вариант содержит ссылку, введите (например, BSTR.) Если *pcParams* равен нулю на выходе или происходит ошибка, отличная от DB_E_ERRORSOCCURRED, поставщик не выделяет памяти и гарантирует, что *prgParamProperties* является указателем null на выходе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **GetParameterProperties** метод возвращает те же коды ошибок, как ядро OLE DB **ICommandProperties::GetProperties** метод, за исключением этого DB_S_ERRORSOCCURRED и или DB_E_ERRORSOCCURED не может быть вызывается.  
  
## <a name="remarks"></a>Примечания  
 **ISSCommandWithParameters::GetParameterProperties** согласованное поведение по отношению к **GetParameterInfo**. Если [ISSCommandWithParameters::SetParameterProperties](isscommandwithparameters-setparameterproperties-ole-db.md) или **SetParameterInfo** не были вызваны или были вызваны с cParams, равным нулю, **GetParameterInfo**информацию о параметре и возвращает это. Если **ISSCommandWithParameters::SetParameterProperties** или **SetParameterInfo** был вызван хотя бы один параметр **ISSCommandWithParameters::GetParameterProperties**  возвращает свойства только для этих параметров, для которых **ISSCommandWithParameters::SetParameterProperties** был вызван. Если **ISSCommandWithParameters::SetParameterProperties** вызывается после **ISSCommandWithParameters::GetParameterProperties** или **GetParameterInfo**, Последующие вызовы **ISSCommandWithParameters::GetParameterProperties** возвращают переопределенные значения тех параметров, для которого **ISSCommandWithParameters::SetParameterProperties** был вызван.  
  
 Структура SSPARAMPROPS определена следующим образом.  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|Член|Описание|  
|------------|-----------------|  
|*iOrdinal*|Порядковый номер переданного параметра.|  
|*cPropertySets*|Количество структур DBPROPSET в *rgPropertySets*.|  
|*rgPropertySets*|Указатель на буфер, в который будет возвращен массив структур DBPROPSET.|  
  
## <a name="see-also"></a>См. также  
 [ISSCommandWithParameters &#40;OLE DB&#41;](isscommandwithparameters-ole-db.md)  
  
  
