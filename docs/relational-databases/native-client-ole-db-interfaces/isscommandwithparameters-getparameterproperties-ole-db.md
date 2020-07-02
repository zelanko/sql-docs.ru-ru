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
ms.openlocfilehash: 26678d79897b4c60e71e39c8c502c38b50d2d965
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785328"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

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
 Указатель на область памяти, в которую будет возвращен массив структур SSPARAMPROPS. Поставщик выделяет память для структур и возвращает адрес в эту память. Потребитель освобождает эту память с помощью **unalloc:: Free** , если она больше не нуждается в структурах. Перед вызовом метода **unalloc:: Free** для *пргпарампропертиес*потребитель должен также вызвать **вариантклеар** для свойства *управляемое vValue* каждой структуры DBPROP, чтобы предотвратить утечку памяти в случаях, когда вариант содержит ссылочный тип (например, BSTR). Если *пкпарамс* имеет нулевое значение на выходе или возникает ошибка, отличная от DB_E_ERRORSOCCURRED, поставщик не выделяет память и гарантирует, что *пргпарампропертиес* является пустым указателем на выходе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Метод **GetParameterProperties** возвращает те же коды ошибок, что и метод Core OLE DB **ICommandProperties::** , за исключением того, что DB_S_ERRORSOCCURRED и DB_E_ERRORSOCCURED не могут быть вызваны.  
  
## <a name="remarks"></a>Примечания  
 **ISSCommandWithParameters:: GetParameterProperties** действует согласованно с уважением **GetParameterInfo**. Если [ISSCommandWithParameters:: SetParameterProperties](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) или **SetParameterInfo** не были вызваны или вызваны с кпарамс равными нулю, **GetParameterInfo** наследует сведения о параметрах и возвращает this. Если **ISSCommandWithParameters:: SetParameterProperties** или **SetParameterInfo** были вызваны по крайней мере для одного параметра, **ISSCommandWithParameters:: GetParameterProperties** Возвращает свойства только для тех параметров, для которых был вызван **ISSCommandWithParameters:: SetParameterProperties** . Если **ISSCommandWithParameters:: SetParameterProperties** вызывается после **ISSCommandWithParameters:: GetParameterProperties** или **GetParameterInfo**, последующие вызовы **ISSCommandWithParameters:: GetParameterProperties** возвращают переопределенные значения для этих параметров, для которых был вызван **ISSCommandWithParameters:: SetParameterProperties** .  
  
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

## <a name="see-also"></a>См. также  
 [ISSCommandWithParameters (OLE DB)](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
