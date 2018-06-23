---
title: ISSCommandWithParameters::SetParameterProperties (OLE DB) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f17947c2b5eb0a8438c074ffca34dca728ae859a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099547"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a>ISSCommandWithParameters::SetParameterProperties (OLE DB)
  Задает свойства каждого параметра по порядковому номеру или задает массовые свойства параметра, указывая массив структур SSPARAMPROPS.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT SetParameterProperties(  
DB_UPARAMS cParams,   
SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a>Аргументы  
 *cParams*[in]  
 Количество структур SSPARAMPROPS в *rgParamProperties* массива. Если это число равно нулю, `ISSCommandWithParameters::SetParameterProperties` приведет к удалению всех свойств, которые могли быть указаны для всех параметров в команде.  
  
 *rgParamProperties*[in]  
 Массив задаваемых структур SSPARAMPROPS.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 `ISSCommandWithParameters::SetParameterProperties` Метод возвращает те же коды ошибок, что и метод ядра OLE DB **ICommandProperties::SetProperties** метод.  
  
## <a name="remarks"></a>Примечания  
 Настройка свойств параметров с помощью этого метода разрешена для каждого параметра в отдельности по порядковому номеру или с помощью одного `ISSCommandWithParameters::SetParameterProperties` вызвать после структура SSPARAMPROPS строится из массива свойств.  
  
 **SetParameterInfo** метод должен вызываться перед вызовом метода `ISSCommandWithParameters::SetParameterProperties` метод. Вызов метода `SetParameterProperties(0, NULL)` очищает все указанные свойства параметра, тогда как вызов метода `SetParameterInfo(0,NULL,NULL)` очищает все сведения о параметре, в том числе все свойства, которые могут быть связаны с параметром.  
  
 Вызов `ISSCommandWithParameters::SetParameterProperties` для задания свойств для параметра, который не относится к типу DBTYPE_XML и DBTYPE_UDT, возвратит DB_E_ERRORSOCCURRED или DB_S_ERRORSOCCURRED и пометит *dwStatus* поле все DBPROPs, содержащихся в структурах SSPARAMPROPS для этого параметра с DBPROPSTATUS_NOTSET. Чтобы обнаружить, к какому параметру относится DB_E_ERRORSOCCURRED или DB_S_ERRORSOCCURRED, необходимо пройти по массиву DBPROP каждого набора DBPROPSET, содержащегося в структуре SSPARAMPROPS.  
  
 Если `ISSCommandWithParameters::SetParameterProperties` вызывается, чтобы указать свойства параметров, сведения о которых имеют еще не был установлен с **SetParameterInfo**, то поставщик возвратит E_UNEXPECTED со следующим сообщением:  
  
 Невозможно вызвать метод SetParameterProperties для указанных параметров, не вызывая предварительно метод SetParameterInfo. До задания свойств параметров необходимо задать сведения о параметрах.  
  
 Если вызов `ISSCommandWithParameters::SetParameterProperties` содержит некоторые параметры, где было установлено сведения о параметре, а некоторые параметры, в которых сведения о параметре не задано, то свойства dwStatus в структуре DBPROPSET набора свойств SSPARAMPROPS вернутся со значением DBSTATUS_NOTSET.  
  
 Структура SSPARAMPROPS определена следующим образом.  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 Усовершенствования в компоненте database engine, начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] разрешить ISSCommandWithParameters::SetParameterProperties получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значения, возвращаемые методом ISSCommandWithParameters::SetParameterProperties в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [обнаружение метаданных](../native-client/features/metadata-discovery.md).  
  
|Член|Описание|  
|------------|-----------------|  
|*iOrdinal*|Порядковый номер переданного параметра.|  
|*cPropertySets*|Количество структур DBPROPSET в *rgPropertySets*.|  
|*rgPropertySets*|Указатель на буфер, в который будет возвращен массив структур DBPROPSET.|  
  
## <a name="see-also"></a>См. также  
 [ISSCommandWithParameters &#40;OLE DB&#41;](isscommandwithparameters-ole-db.md)  
  
  