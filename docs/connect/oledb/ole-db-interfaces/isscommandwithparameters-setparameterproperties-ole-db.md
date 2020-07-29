---
title: ISSCommandWithParameters::SetParameterProperties (OLE DB) | Документация Майкрософт
description: ISSCommandWithParameters::SetParameterProperties (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- SetParameterProperties method
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 643549a08c10bd43e9c6c9b676fab380b7731965
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006715"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a>ISSCommandWithParameters::SetParameterProperties (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Задает свойства каждого параметра по порядковому номеру или задает массовые свойства параметра, указывая массив структур SSPARAMPROPS.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT SetParameterProperties(  
      DB_UPARAMS cParams,   
      SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a>Аргументы  
 *cParams*[in]  
 Количество структур SSPARAMPROPS в массиве *rgParamProperties*. Если это число равно 0, то метод **ISSCommandWithParameters::SetParameterProperties** удалит все свойства, которые могли быть указаны для всех параметров команды.  
  
 *rgParamProperties*[in]  
 Массив задаваемых структур SSPARAMPROPS.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Метод **ISSCommandWithParameters::SetParameterProperties** возвращает те же коды ошибок, что и базовый метод OLE DB **ICommandProperties::SetProperties**.  
  
## <a name="remarks"></a>Remarks  
 С помощью этого метода разрешается задавать свойства для каждого параметра по порядковому номеру параметра или путем одного вызова метода **ISSCommandWithParameters::SetParameterProperties**, если структура SSPARAMPROPS строится из массива свойств.  
  
 Метод **SetParameterInfo** необходимо вызывать до вызова метода **ISSCommandWithParameters::SetParameterProperties**. Вызов метода `SetParameterProperties(0, NULL)` очищает все указанные свойства параметра, тогда как вызов метода `SetParameterInfo(0,NULL,NULL)` очищает все сведения о параметре, в том числе все свойства, которые могут быть связаны с параметром.  
  
 Вызов метода **ISSCommandWithParameters::SetParameterProperties** с целью указания свойств параметра, тип которого отличен от DBTYPE_XML или DBTYPE_UDT, возвратит DB_E_ERRORSOCCURRED или DB_S_ERRORSOCCURRED и пометит поле *dwStatus* как DBPROPSTATUS_NOTSET для всех структур DBPROP, содержащихся в структурах SSPARAMPROPS для этого параметра. Чтобы обнаружить, к какому параметру относится DB_E_ERRORSOCCURRED или DB_S_ERRORSOCCURRED, необходимо пройти по массиву DBPROP каждого набора DBPROPSET, содержащегося в структуре SSPARAMPROPS.  
  
 Если метод **ISSCommandWithParameters::SetParameterProperties** вызывается, чтобы задать свойства параметров, сведения о которых еще не были заданы с помощью метода **SetParameterInfo**, то поставщик возвратит E_UNEXPECTED со следующим сообщением об ошибке:  
  
 Невозможно вызвать метод SetParameterProperties для указанных параметров, не вызывая предварительно метод SetParameterInfo. До задания свойств параметров необходимо задать сведения о параметрах.  
  
 Если вызов метода **ISSCommandWithParameters::SetParameterProperties** содержит некоторые параметры с заданными сведениями и некоторые параметры с незаданными сведениями, то свойства dwStatus в структуре DBPROPSET набора свойств SSPARAMPROPS будут возвращены со значением DBSTATUS_NOTSET.  
  
 Структура SSPARAMPROPS определена следующим образом.  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 Улучшения ядра СУБД, появившиеся с версии [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], позволяют методу ISSCommandWithParameters::SetParameterProperties получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значений, которые метод ISSCommandWithParameters::SetParameterProperties возвращает в предыдущих версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Обнаружение метаданных](../../oledb/features/metadata-discovery.md).  
  
|Участник|Description|  
|------------|-----------------|  
|*iOrdinal*|Порядковый номер переданного параметра.|  
|*cPropertySets*|Количество структур DBPROPSET в *rgPropertySets*.|  
|*rgPropertySets*|Указатель на буфер, в который будет возвращен массив структур DBPROPSET.|  
  
## <a name="see-also"></a>См. также:  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
