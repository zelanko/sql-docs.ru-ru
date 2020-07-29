---
title: ISSCommandWithParameters::GetParameterProperties (OLE DB) | Документация Майкрософт
description: ISSCommandWithParameters::GetParameterProperties (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- GetParameterProperties method
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 288657a0871046168e7319d5c650a12eab61c6ce
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006757"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

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
 Указатель на область памяти, в которую будет возвращен массив структур SSPARAMPROPS. Поставщик выделяет память под структуры и возвращает адрес этой памяти. Когда структуры больше не нужны потребителю, он освобождает память вызовом метода **IMalloc::Free**. До вызова метода **IMalloc::Free** для объекта *prgParamProperties* потребитель должен также вызвать метод **VariantClear** для свойства *vValue* каждой структуры DBPROP, чтобы предотвратить утечку памяти в случае, если вариант содержит ссылочный тип (например, BSTR). Если указатель *pcParams* равен нулю на выходе или происходит любая ошибка, отличная от DB_E_ERRORSOCCURRED, поставщик не выделяет память и обеспечивает равенство указателя *prgParamProperties* NULL на выходе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Метод **GetParameterProperties** возвращает те же коды ошибок, что и базовый метод OLE DB **ICommandProperties::GetProperties**, за исключением того факта, что он не может вернуть DB_S_ERRORSOCCURRED или DB_E_ERRORSOCCURED.  
  
## <a name="remarks"></a>Remarks  
 Метод **ISSCommandWithParameters::GetParameterProperties** ведет себя аналогично функции **GetParameterInfo**. Если метод [ISSCommandWithParameters::SetParameterProperties](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) или функция **SetParameterInfo** не были вызваны или были вызваны с нулевым параметром cParams, **GetParameterInfo** выводит информацию о параметре и возвращает ее. Если хотя бы для одного параметра был вызван один из методов **ISSCommandWithParameters::SetParameterProperties** или **SetParameterInfo**, метод **ISSCommandWithParameters::GetParameterProperties** возвращает свойства только тех параметров, для которых вызывался метод **ISSCommandWithParameters::SetParameterProperties**. Если метод **ISSCommandWithParameters::SetParameterProperties** вызывается после метода **ISSCommandWithParameters::GetParameterProperties** или функции **GetParameterInfo**, последующие вызовы метода **ISSCommandWithParameters::GetParameterProperties** возвращают переопределенные значения тех параметров, для которых вызывался метод **ISSCommandWithParameters::SetParameterProperties**.  
  
 Структура SSPARAMPROPS определена следующим образом.  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|Участник|Description|  
|------------|-----------------|  
|*iOrdinal*|Порядковый номер переданного параметра.|  
|*cPropertySets*|Количество структур DBPROPSET в *rgPropertySets*.|  
|*rgPropertySets*|Указатель на буфер, в который будет возвращен массив структур DBPROPSET.|  
  
## <a name="see-also"></a>См. также:  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
