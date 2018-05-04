---
title: ISSCommandWithParameters::GetParameterProperties (OLE DB) | Документы Microsoft
description: ISSCommandWithParameters::GetParameterProperties (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- GetParameterProperties method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: e14ad816408347e17a8b5d5ff12b678bcc49377f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

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
 Указатель на область памяти, в которую будет возвращен массив структур SSPARAMPROPS. Поставщик выделяет память для структур и возвращает адрес этой памяти, потребитель освобождает эту память с **IMalloc::Free** когда он больше не нужна структуры. Перед вызовом метода **IMalloc::Free** для *prgParamProperties*, пользователь должен также вызвать **VariantClear** для *vValue* свойство каждой структуры DBPROP, чтобы предотвратить утечку памяти в случаях, если вариант содержит ссылку типа, такие как BSTR. Если *pcParams* равен нулю на выходе или происходит ошибка, отличная от DB_E_ERRORSOCCURRED, поставщик не выделяет памяти и гарантирует *prgParamProperties* является указателем null на выходе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **GetParameterProperties** метод возвращает те же коды ошибок, что и метод ядра OLE DB **ICommandProperties::GetProperties** метод, за исключением того, что DB_S_ERRORSOCCURRED или DB_E_ERRORSOCCURED не может быть создано.  
  
## <a name="remarks"></a>Замечания  
 **ISSCommandWithParameters::GetParameterProperties** метод согласованное поведение по отношению к **GetParameterInfo**. Если [ISSCommandWithParameters::SetParameterProperties](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) или **SetParameterInfo** не были вызваны или были вызваны с cParams, равное нулю, **GetParameterInfo**извлекающий сведения о параметрах и возвращает его. Если **ISSCommandWithParameters::SetParameterProperties** или **SetParameterInfo** был вызван хотя бы один параметр **ISSCommandWithParameters::GetParameterProperties**  метод возвращает свойства только для этих параметров, для которых **ISSCommandWithParameters::SetParameterProperties** был вызван. Если **ISSCommandWithParameters::SetParameterProperties** вызывается после **ISSCommandWithParameters::GetParameterProperties** или **GetParameterInfo**, Последующие вызовы **ISSCommandWithParameters::GetParameterProperties** возвращает переопределенные значения тех параметров, для которых **ISSCommandWithParameters::SetParameterProperties** был вызван метод.  
  
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
 [ISSCommandWithParameters & #40; OLE DB & #41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
