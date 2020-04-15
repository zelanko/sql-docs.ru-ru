---
title: ISSCommandWithParameters::GetParameterProperties (OLE DB)
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 26c95c64f0f2922ef11946841b160879f001e358
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290095"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Возвращает массив структур SSPARAMPROPS, представляющих собой множества свойств, по одному множеству свойств SSPARAMPROPS на каждый параметр определяемого пользователем типа или XML.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetParameterProperties(  
      DB_UPARAMS *pcParams,  
      SSPARAMPROPS **prgParamProperties);  
```  
  
## <a name="arguments"></a>Аргументы  
 *pcParams*[out][in]  
 Указатель на область памяти, где содержится количество структур SSPARAMPROPS, возвращаемых в параметре *prgParamProperties*.  
  
 *prgParamProperties*[out]  
 Указатель на область памяти, в которую будет возвращен массив структур SSPARAMPROPS. Поставщик выделяет память для структур и возвращает адрес в эту память; потребитель выпускает эту память с **IMalloc::Free,** когда он больше не нуждается в структурах. Прежде чем звонить **IMalloc::Бесплатно** для *prgParamProperties*, потребитель должен также позвонить **VariantClear** для *vValue* собственности каждой структуры DBPROP для того, чтобы предотвратить утечку памяти в тех случаях, когда вариант содержит тип ссылки (например, BSTR.) Если *pcParams* равен нулю на выходе или ошибка, кроме DB_E_ERRORSOCCURRED происходит, поставщик не выделяет памяти и гарантирует, что *prgParamProperties* является нулевая указатель на выходе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Метод **GetParameterProperties** возвращает те же коды ошибок, что и основной метод OLE DB **ICommandProperties::GetProperties,** за исключением того, что DB_S_ERRORSOCCURRED и DB_E_ERRORSOCCURED не могут быть подняты.  
  
## <a name="remarks"></a>Remarks  
 **ISSCommandWith Параметры::GetParameterPropertiesСвойства** ведут себя последовательно по отношению к **GetParameterInfo**. Если [ISSCommandWithПараметры::SetParameterProperties](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) или **SetParameterInfo** не были вызваны или были вызваны с cParams, равными нулю, **GetParameterInfo** получает информацию о параметрах и возвращает это. Если **ISSCommandWithПараметры::SetParameterProperties** или **SetParameterInfo** были вызваны по крайней мере для одного параметра, **ISSCommandWithПараметры::GetParameterProperties** возвращает свойства только для тех параметров, для которых **ISSCommandWithParameters::SetParameterProperties** has been called. Если **ISSCommandWithПараметры::SetParameterPropertiesназываете** называется после **ISSCommandWithParameters::GetParameterProperties** или **GetParameterInfo**, последующие звонки на **ISSCommandWithParameters::GetParameterProperties** вернуть переопределенные значения для тех параметров, для которых **ISSCommandWithParameters::SetParameterProperties** has been called.  
  
 Структура SSPARAMPROPS определена следующим образом.  

```cpp
struct SSPARAMPROPS {
    DBORDINAL iOrdinal;
    ULONG cPropertySets;
    DBPROPSET *rgPropertySets;
};
```

|Участник|Описание|  
|------------|-----------------|  
|*iOrdinal*|Порядковый номер переданного параметра.|  
|*cPropertySets*|Количество структур DBPROPSET в *rgPropertySets*.|  
|*rgPropertySets*|Указатель на буфер, в который будет возвращен массив структур DBPROPSET.|  
|||

## <a name="see-also"></a>См. также:  
 [ISSCommandWithParameters (OLE DB)](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
