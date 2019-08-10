---
title: OPENQUERY (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: caac43eb176e17a6e92e487f3dedae71a252f5af
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68887729"
---
# <a name="ltsource-data-querygt---openquery"></a>&lt;запрос&gt; источника данных — OPENQUERY
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Заменяет запрос источника данных запросом существующего источника данных. Инструкция INSERT, выбор из ПРОГНОЗИРУЕМого объединения и выбор из выражений ЕСТЕСТВЕННОго ПРОГНОЗИРУЮЩЕГО подключения поддерживают **OPENQUERY**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
OPENQUERY(<named datasource>, <query syntax>)  
```  
  
## <a name="arguments"></a>Аргументы  
 *именованный источник данных*  
 Источник данных, существующий в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] базе данных.  
  
 *синтаксис запроса*  
 Синтаксис запроса, возвращающего набор строк.  
  
## <a name="remarks"></a>Примечания  
 **OPENQUERY** обеспечивает более безопасный способ доступа к внешним данным путем поддержки разрешений источника данных. Так как строка соединения хранится в источнике данных, администраторы могут использовать свойства источника данных для управления доступом к данным. Дополнительные сведения об источниках данных см. в разделе [поддерживаемые &#40;источники данных SSAS — многомерные&#41;данные](https://docs.microsoft.com/analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional).  
  
 Список источников данных, доступных на сервере, можно получить, выполнив запрос к набору строк схемы **MDSCHEMA_INPUT_DATASOURCES** . Дополнительные сведения об использовании **MDSCHEMA_INPUT_DATASOURCES**см. в разделе [набор строк MDSCHEMA_INPUT_DATASOURCES](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset).  
  
 Кроме того, список источников данных в текущей базе данных служб Analysis Services можно получить с помощью следующего DMX-запроса:  
  
 `SELECT * FROM $system.MDSCHEMA_INPUT_DATASOURCES`  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется источник данных MyDS, уже определенный в [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] базе данных, чтобы создать соединение [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] с базой данных и выполнить запрос к представлению **vTargetMail** .  
  
```  
OPENQUERY (MyDS,'SELECT TOP 1000 * FROM vTargetMail')  
```  
  
## <a name="see-also"></a>См. также  
 [&#60;запрос источника данных&#62;](../dmx/source-data-query.md)   
 [Расширения &#40;интеллектуального анализа&#41; данных инструкции DMX-операций с данными](../dmx/dmx-statements-data-manipulation.md)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
