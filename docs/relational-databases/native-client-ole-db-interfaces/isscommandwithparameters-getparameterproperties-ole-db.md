---
title: ISSCommandWithParameters::GetParameterProperties (OLE DB) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c96abfb3a15580222a94bd490793cd17b7d13e14
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2018
ms.locfileid: "35703655"
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
 Указатель на область памяти, в которую будет возвращен массив структур SSPARAMPROPS. Поставщик выделяет память для структур и возвращает адрес этой памяти; потребитель освобождает эту память с **IMalloc::Free** когда он больше не нужна структуры. Перед вызовом метода **IMalloc::Free** для *prgParamProperties*, пользователь должен также вызвать **VariantClear** для *vValue* свойство для каждой структуры DBPROP во избежание утечки памяти в случаях, если вариант содержит ссылку типа (например, BSTR.) Если *pcParams* равен нулю на выходе или происходит ошибка, отличная от DB_E_ERRORSOCCURRED, поставщик не выделяет памяти и гарантирует, что *prgParamProperties* является указателем null на выходе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **GetParameterProperties** метод возвращает те же коды ошибок, что и метод ядра OLE DB **ICommandProperties::GetProperties** метод, за исключением того, что DB_S_ERRORSOCCURRED или DB_E_ERRORSOCCURED не может быть создано.  
  
## <a name="remarks"></a>Примечания  
 **ISSCommandWithParameters::GetParameterProperties** согласованное поведение по отношению к **GetParameterInfo**. Если [ISSCommandWithParameters::SetParameterProperties](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) или **SetParameterInfo** не были вызваны или были вызваны с cParams, равное нулю, **GetParameterInfo**извлекающий сведения о параметрах и возвращает это. Если **ISSCommandWithParameters::SetParameterProperties** или **SetParameterInfo** был вызван хотя бы один параметр **ISSCommandWithParameters::GetParameterProperties**  возвращает свойства только для этих параметров, для которых **ISSCommandWithParameters::SetParameterProperties** был вызван. Если **ISSCommandWithParameters::SetParameterProperties** вызывается после **ISSCommandWithParameters::GetParameterProperties** или **GetParameterInfo**, Последующие вызовы **ISSCommandWithParameters::GetParameterProperties** возвращает переопределенные значения тех параметров, для которых **ISSCommandWithParameters::SetParameterProperties** был вызван.  
  
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
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
