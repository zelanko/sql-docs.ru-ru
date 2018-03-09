---
title: "ISSCommandWithParameters::GetParameterProperties (OLE DB) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords: GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
caps.latest.revision: "29"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5a157de9b398914ce7dd9648cfd5612ffbf48a6a
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Возвращает массив структур SSPARAMPROPS, представляющих собой множества свойств, по одному множеству свойств SSPARAMPROPS на каждый параметр определяемого пользователем типа или XML.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT GetParameterProperties(  
      DB_UPARAMS *pcParams,  
      SSPARAMPROPS **prgParamProperties);  
```  
  
## <a name="arguments"></a>Аргументы  
 *pcParams*[out] [in]  
 Указатель на буфер, содержащий количество структур SSPARAMPROPS возвращается в *prgParamProperties*.  
  
 *prgParamProperties*[out]  
 Указатель на область памяти, в которую будет возвращен массив структур SSPARAMPROPS. Поставщик выделяет память для структур и возвращает адрес этой памяти; потребитель освобождает эту память с **IMalloc::Free** когда он больше не нужна структуры. Перед вызовом метода **IMalloc::Free** для *prgParamProperties*, пользователь должен также вызвать **VariantClear** для *vValue* свойства каждой структуры DBPROP, чтобы предотвратить утечку памяти в случаях, если вариант содержит ссылочный тип (например, BSTR.) Если *pcParams* равен нулю на выходе или происходит ошибка, отличная от DB_E_ERRORSOCCURRED, поставщик не выделяет памяти и гарантирует, что *prgParamProperties* является указателем null на выходе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **GetParameterProperties** метод возвращает те же коды ошибок, что и метод ядра OLE DB **ICommandProperties::GetProperties** невозможно вызвать метод, за исключением того, что DB_S_ERRORSOCCURRED или DB_E_ERRORSOCCURED.  
  
## <a name="remarks"></a>Замечания  
 **ISSCommandWithParameters::GetParameterProperties** согласованное поведение по отношению к **GetParameterInfo**. Если [ISSCommandWithParameters::SetParameterProperties](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) или **SetParameterInfo** не были вызваны или были вызваны с cParams, равное нулю, **GetParameterInfo** извлекающий сведения о параметрах и возвращает это. Если **ISSCommandWithParameters::SetParameterProperties** или **SetParameterInfo** был вызван хотя бы один параметр **ISSCommandWithParameters::GetParameterProperties** возвращает свойства только для этих параметров, для которых **ISSCommandWithParameters::SetParameterProperties** был вызван. Если **ISSCommandWithParameters::SetParameterProperties** вызывается после **ISSCommandWithParameters::GetParameterProperties** или **GetParameterInfo**, последующие вызовы **ISSCommandWithParameters::GetParameterProperties** возвращает переопределенные значения тех параметров, для которых **ISSCommandWithParameters::SetParameterProperties** был вызван.  
  
 Структура SSPARAMPROPS определена следующим образом.  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|Член|Description|  
|------------|-----------------|  
|*iOrdinal*|Порядковый номер переданного параметра.|  
|*cPropertySets*|Количество структур DBPROPSET в *rgPropertySets*.|  
|*rgPropertySets*|Указатель на буфер, в который будет возвращен массив структур DBPROPSET.|  
  
## <a name="see-also"></a>См. также:  
 [ISSCommandWithParameters &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
