---
title: "Развертывание решения интеллектуального анализа данных в предыдущих версиях SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backward compatibility [Analysis Services]
- holdout [data mining]
- deploy [Analysis Services]
- time series [Analysis Services]
- deploying [Analysis Services - data mining]
- synchronization [Analysis Services]
- deployment [Analysis Services]
ms.assetid: 2715c245-f206-43af-8bf5-e6bd2585477a
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 834b8ceae72e00eea7bf989ea9583068551bfc92
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="deploy-a-data-mining-solution-to-previous-versions-of-sql-server"></a>Развертывание решения интеллектуального анализа данных в предыдущих версиях SQL Server
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]В этом разделе описаны известные проблемы совместимости, возникающих при попытке развернуть модель интеллектуального анализа данных или структуры интеллектуального анализа данных, созданной в экземпляре [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] в базе данных, который использует SQL Server 2005 Analysis Services, или при развертывании модели, созданные в SQL Server 2005 к экземпляру компонента [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Развертывание на экземпляре служб SQL Server 2000 Analysis Services не поддерживается.  
  
 [Развертывание моделей временных рядов](#bkmk_TimeSeries)  
  
 [Развертывание моделей с контрольными данными](#bkmk_Holdout)  
  
 [Развертывание моделей с фильтрами](#bkmk_Filter)  
  
 [Восстановление из резервных копий базы данных](#bkmk_Backup)  
  
 [Использование синхронизации базы данных](#bkmk_Synch)  
  
##  <a name="bkmk_TimeSeries"></a> Развертывание моделей временных рядов  
 Алгоритм временных рядов (Майкрософт) в SQL Server 2008 был расширен. В него был добавлен второй, дополнительный алгоритм ARIMA. Дополнительные сведения об изменениях в алгоритме временных рядов см. в разделе [Алгоритм временных рядов (Майкрософт)](../../analysis-services/data-mining/microsoft-time-series-algorithm.md).  
  
 Поэтому модели временных рядов, в которых используется алгоритм ARIMA, при развертывании на экземпляре служб SQL Server 2005 Analysis Services могут работать иначе.  
  
 Если явно задан параметр PREDICTION_SMOOTHING, управляющий смешиванием моделей ARTXP и ARIMA в процессе прогнозирования, то при развертывании такой модели на экземпляре SQL Server 2005 службы Analysis Services выдадут сообщение об ошибке, указывающее на недопустимый параметр. Чтобы избежать этой ошибки, удалите параметр PREDICTION_SMOOTHING и преобразуйте модель таким образом, чтобы в ней использовался только алгоритм ARTXP.  
  
 И наоборот, если при развертывании модели временных рядов, созданной в службах SQL Server 2005 Analysis Services, в экземпляре [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]открыть модель интеллектуального анализа данных в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], то файлы определений сначала преобразуются в новый формат, а во все модели временных рядов по умолчанию будут добавлены два новых параметра. Параметр FORECAST_METHOD добавляется со значением по умолчанию MIXED, а параметр PREDICTION_SMOOTHING — со значением 0,5. Однако до повторной обработки при прогнозировании модель будет по-прежнему использовать только алгоритм ARTXP. После повторной обработки модели при прогнозировании будет использоваться как алгоритм ARIMA, так и алгоритм ARTXP.  
  
 Поэтому, если желательно избежать изменения модели, ее следует только просматривать, но не обрабатывать. Кроме того, параметры FORECAST_METHOD и PREDICTION_SMOOTHING можно задать явным образом.  
  
 Дополнительные сведения о настройке смешанных моделей см. в разделе [Технический справочник по алгоритму временных рядов (Майкрософт)](../../analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md).  
  
 Если источник данных обслуживается поставщиком данных клиента SQL 10, то необходимо также изменить определение источника данных, указав предыдущую версию собственного клиента SQL Server. В противном случае среда [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] создает сообщение об ошибке, извещающее о том, что поставщик не зарегистрирован.  
  
##  <a name="bkmk_Holdout"></a> Развертывание моделей с контрольными данными  
 При создании структуры интеллектуального анализа данных, который содержит контрольную секцию для тестирования моделей интеллектуального анализа данных, структуры интеллектуального анализа данных могут развертываться на экземпляре SQL Server 2005, но сведения о секции будут потеряны.  
  
 При открытии структуры интеллектуального анализа данных в службах SQL Server 2005 Analysis Services среда [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] выдает ошибку и производит повторное формирование структуры, удаляя контрольную секцию.  
  
 После перестроения структуры размер контрольной секции, больше не доступны в окне «Свойства»; Тем не менее, значение \<ddl100_100: holdoutmaxpercent > 30\</ddl100_100:HoldoutMaxPercent >) по-прежнему присутствовать в файле скрипта ASSL.  
  
##  <a name="bkmk_Filter"></a> Развертывание моделей с фильтрами  
 Если применить фильтр к модели интеллектуального анализа данных, модели можно развернуть на экземпляре SQL Server 2005, но не будет применяться фильтр.  
  
 При открытии модели интеллектуального анализа данных среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] выдает ошибку и производит повторное формирование модели, чтобы удалить фильтр.  
  
##  <a name="bkmk_Backup"></a> Восстановление из резервных копий базы данных  
 Резервную копию базы данных, созданную в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , нельзя восстановить на экземпляре SQL Server 2005. При попытке сделать это среда SQL Server Management Studio сообщает об ошибке.  
  
 Если создать резервную копию базы данных служб SQL Server 2005 Analysis Services и восстановить ее на экземпляре [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], все модели временных рядов будут изменены, как описано в предыдущем разделе.  
  
##  <a name="bkmk_Synch"></a> Использование синхронизации базы данных  
 Синхронизация базы данных с [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] на SQL Server 2005 не поддерживается.  
  
 При попытке синхронизации базы данных [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] сервер вернет ошибку, а синхронизация будет отменена.  
  
## <a name="see-also"></a>См. также  
 [Analysis Services Backward Compatibility](../../analysis-services/analysis-services-backward-compatibility.md)  
  
  
