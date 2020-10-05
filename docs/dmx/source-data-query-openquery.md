---
description: '&lt;запрос источника данных &gt; — OPENQUERY'
title: OPENQUERY (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 62d638b6b6028ffa861460e07f2283cb7380e129
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726114"
---
# <a name="ltsource-data-querygt---openquery"></a>&lt;запрос источника данных &gt; — OPENQUERY
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

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
  
## <a name="remarks"></a>Комментарии  
 **OPENQUERY** обеспечивает более безопасный способ доступа к внешним данным путем поддержки разрешений источника данных. Так как строка соединения хранится в источнике данных, администраторы могут использовать свойства источника данных для управления доступом к данным. Дополнительные сведения об источниках данных см. в разделе [Поддерживаемые источники данных &#40;SSAS — многомерные&#41;](/analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional).  
  
 Список источников данных, доступных на сервере, можно получить, выполнив запрос к набору строк схемы **MDSCHEMA_INPUT_DATASOURCES** . Дополнительные сведения об использовании **MDSCHEMA_INPUT_DATASOURCES**см. в разделе [набор строк MDSCHEMA_INPUT_DATASOURCES](/previous-versions/sql/sql-server-2012/ms126243(v=sql.110)).  
  
 Кроме того, список источников данных в текущей базе данных служб Analysis Services можно получить с помощью следующего DMX-запроса:  
  
 `SELECT * FROM $system.MDSCHEMA_INPUT_DATASOURCES`  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется источник данных MyDS, уже определенный в [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] базе данных, чтобы создать соединение с [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] базой данных и выполнить запрос к представлению **vTargetMail** .  
  
```  
OPENQUERY (MyDS,'SELECT TOP 1000 * FROM vTargetMail')  
```  
  
## <a name="see-also"></a>См. также  
 [&#62;запроса источника данных&#60;](../dmx/source-data-query.md)   
 [Расширения интеллектуального анализа данных &#40;инструкции расширений интеллектуального анализа данных&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-statements.md)  
  
