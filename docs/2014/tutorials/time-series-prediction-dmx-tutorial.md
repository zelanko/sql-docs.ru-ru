---
title: Время учебника расширений интеллектуального анализа данных прогнозирования ряда | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38ea7c03-4754-4e71-896a-f68cc2c98ce2
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2a9e3e5db1e0f21bfe3822d73fd0e3c0b456e250
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312202"
---
# <a name="time-series-prediction-dmx-tutorial"></a>Учебник по расширениям интеллектуального анализа данных для прогнозирования временных рядов
  В этом учебнике объясняется, как создавать структуры интеллектуального анализа временных рядов, создать дерево моделей интеллектуального анализа временных рядов, а затем делать прогнозы с помощью этих моделей.  
  
 Модели интеллектуального анализа данных основаны на данных из образца базы данных [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)], где хранятся данные вымышленной компании [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]. [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] является крупной транснациональной производственной организацией.  
  
## <a name="tutorial-scenario"></a>Сценарий учебника  
 Компания [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] решила использовать интеллектуальный анализ данных для прогнозирования продаж. Они уже созданы некоторые модели регионального прогнозирования; Дополнительные сведения см. в разделе [Lesson 2: построение сценария прогнозирования &#40;промежуточного Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md). Однако отделу продаж требуется периодически обновлять модель интеллектуального анализа данных новыми данными о сбыте. Кроме того, необходимо настраивать модели для предоставления различных проекций.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] предоставляет несколько средств, которые можно использовать для выполнения этой задачи:  
  
-   Язык запросов расширений интеллектуального анализа данных (DMX)  
  
-   Алгоритм временных рядов (Майкрософт)  
  
-   Редактор запросов в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Алгоритма временных рядов создает модели, которые могут использоваться для прогнозирования временных данных. Расширения интеллектуального анализа данных представляют собой язык запросов, поставляемый в составе служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] и применяемый для создания моделей интеллектуального анализа данных и прогнозирующих запросов.  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
 При изучении материала этого учебника предполагается, что читатель уже знаком с объектами, с помощью которых службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] создают модели интеллектуального анализа данных. Если вы раньше не приходилось создавать структуру интеллектуального анализа данных или модели интеллектуального анализа данных с помощью расширений интеллектуального анализа данных, см. раздел [Bike Buyer расширений интеллектуального анализа данных учебника](../../2014/tutorials/bike-buyer-dmx-tutorial.md).  
  
 Учебник содержит следующие занятия:  
  
 [Урок 1. Создание модели интеллектуального анализа данных временных рядов и структуры интеллектуального анализа данных](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)  
 На этом занятии рассматривается добавление новой модели прогнозирования и связанной с ней модели интеллектуального анализа с помощью инструкции `CREATE MINING MODEL`.  
  
 [Урок 2. Добавление моделей интеллектуального анализа данных в структуру интеллектуального анализа временных рядов](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)  
 На этом занятии будет показано добавление новых моделей интеллектуального анализа данных в структуру временных рядов с помощью инструкции ALTER MINING STRUCTURE. Также будет описана настройка алгоритма, применяемого для анализа временных рядов.  
  
 [Урок 3. Обработка структуры и моделей временных рядов](../../2014/tutorials/lesson-3-processing-the-time-series-structure-and-models.md)  
 На этом занятии будет показан процесс обучения моделей с помощью инструкции `INSERT INTO`, а также заполнение структуры данными из базы данных [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].  
  
 [Урок 4. Создание прогнозов временных рядов с использованием расширений интеллектуального анализа данных](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
 На этом занятии будет показано, как создать прогнозы временных рядов.  
  
 [Урок 5. Расширение модели временных рядов](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
 На этом занятии рассматривается обновление новой модели новыми данными с помощью параметра `EXTEND_MODEL_CASES` при выполнении прогнозов.  
  
## <a name="requirements"></a>Требования  
 Прежде чем выполнять задания этого учебника, убедитесь, что установлены следующие компоненты:  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   База данных [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]  
  
 В целях повышения безопасности образцы баз данных по умолчанию не установлены. Чтобы установить официальные образцы баз данных для [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], перейдите в меню [ http://www.CodePlex.com/MSFTDBProdSamples ](http://go.microsoft.com/fwlink/?LinkId=88417) или на домашней странице Microsoft SQL Server Samples and Community Projects в разделе Microsoft SQL Server Product Samples. Нажмите кнопку **баз данных**, нажмите кнопку **выпуски** вкладки и выберите нужные базы данных.  
  
> [!NOTE]  
>  При просмотре учебников рекомендуется добавить **следующий раздел** и **предыдущий раздел** кнопок панели инструментов средства просмотра документов.  
  
## <a name="see-also"></a>См. также  
 [Учебник по интеллектуальному анализу данных](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Учебник по интеллектуальному анализу данных промежуточного &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  