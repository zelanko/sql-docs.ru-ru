---
title: ISSCommandWithParameters::SetParameterProperties (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b4ccbc15cd4493f4d0d9654e9da130ac192f9f8c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416923"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a>ISSCommandWithParameters::SetParameterProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Задает свойства каждого параметра по порядковому номеру или задает массовые свойства параметра, указывая массив структур SSPARAMPROPS.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT SetParameterProperties(  
      DB_UPARAMS cParams,   
      SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a>Аргументы  
 *cParams*[in]  
 Количество структур SSPARAMPROPS в *rgParamProperties* массива. Если это число равно нулю, **ISSCommandWithParameters::SetParameterProperties** приведет к удалению всех свойств, которые могли быть указаны для любых параметров в команде.  
  
 *rgParamProperties*[in]  
 Массив задаваемых структур SSPARAMPROPS.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **ISSCommandWithParameters::SetParameterProperties** метод возвращает те же коды ошибок, как ядро OLE DB **ICommandProperties::SetProperties** метод.  
  
## <a name="remarks"></a>Примечания  
 Настройка свойств параметров с помощью этого метода разрешена для каждого параметра в отдельности по порядковому номеру или с одним **ISSCommandWithParameters::SetParameterProperties** вызвать после структура SSPARAMPROPS строится из массива свойств.  
  
 **SetParameterInfo** метод должен вызываться перед вызовом **ISSCommandWithParameters::SetParameterProperties** метод. Вызов метода `SetParameterProperties(0, NULL)` очищает все указанные свойства параметра, тогда как вызов метода `SetParameterInfo(0,NULL,NULL)` очищает все сведения о параметре, в том числе все свойства, которые могут быть связаны с параметром.  
  
 Вызов **ISSCommandWithParameters::SetParameterProperties** для указания свойства параметра, который не относится к типу DBTYPE_XML и DBTYPE_UDT, возвратит DB_E_ERRORSOCCURRED или DB_S_ERRORSOCCURRED и пометит  *dwStatus* поле все DBPROPs, содержащегося в структуре SSPARAMPROPS для этого параметра с DBPROPSTATUS_NOTSET. Чтобы обнаружить, к какому параметру относится DB_E_ERRORSOCCURRED или DB_S_ERRORSOCCURRED, необходимо пройти по массиву DBPROP каждого набора DBPROPSET, содержащегося в структуре SSPARAMPROPS.  
  
 Если **ISSCommandWithParameters::SetParameterProperties** вызывается для указания свойства параметров, сведения о имеют еще не был установлен с **SetParameterInfo**, поставщик возвращает E_ НЕПРЕДВИДЕННЫЙ с следующее сообщение об ошибке:  
  
 Невозможно вызвать метод SetParameterProperties для указанных параметров, не вызывая предварительно метод SetParameterInfo. До задания свойств параметров необходимо задать сведения о параметрах.  
  
 Если вызов **ISSCommandWithParameters::SetParameterProperties** содержит некоторые параметры, где сведения о параметрах был набор и некоторые параметры, где сведения о параметрах не было задано, то свойства dwStatus в DBPROPSET набора свойств SSPARAMPROPS вернутся со значением DBSTATUS_NOTSET.  
  
 Структура SSPARAMPROPS определена следующим образом.  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 Улучшения в ядро базы данных, начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] разрешить ISSCommandWithParameters::SetParameterProperties получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значения, возвращаемые методом ISSCommandWithParameters::SetParameterProperties в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [обнаружение метаданных](../../relational-databases/native-client/features/metadata-discovery.md).  
  
|Член|Описание|  
|------------|-----------------|  
|*iOrdinal*|Порядковый номер переданного параметра.|  
|*cPropertySets*|Количество структур DBPROPSET в *rgPropertySets*.|  
|*rgPropertySets*|Указатель на буфер, в который будет возвращен массив структур DBPROPSET.|  
  
## <a name="see-also"></a>См. также  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
