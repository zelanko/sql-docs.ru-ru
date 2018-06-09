---
title: ЭКСПОРТ (ДАННЫХ DMX) | Документы Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bb777a0de00596c99e22e514986cf3ec930ba0fd
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841967"
---
# <a name="export-dmx"></a>EXPORT (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Извлекает модель или объект структуры интеллектуального анализа данных из сервера в файл резервной копии служб Analysis Services (ABF).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
EXPORT <object type> <object name>[, <object name>] [<object type> <object name>[, <object name] ] TO <filename> [WITH DEPENDENCIES]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Тип объекта*  
 Тип объекта для экспорта (модели интеллектуального анализа данных или структуры интеллектуального анализа данных) (необязательно).  
  
 *Имя объекта*  
 Необязательный параметр. Имя экспортируемого объекта.  
  
 *Имя файла*  
 Имя и расположение файла для экспорта (аргумент типа string).  
  
## <a name="remarks"></a>Примечания  
 Если инструкция указывает модель интеллектуального анализа данных, итоговый файл также содержит связанную структуру интеллектуального анализа данных. Если инструкция указывает **WITH DEPENDENCIES**, все объекты, необходимые для обработки объекта (например, источник данных и представление источника данных), включаются в ABF-файл.  
  
 Должна быть базой данных или администратора сервера для экспорта или импорта объектов из [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] базы данных.  
  
## <a name="export-mining-structure-example"></a>Пример экспорта структуры интеллектуального анализа данных  
 В следующем примере структуры интеллектуального анализа данных Targeted Mailing и Forecasting, а также модель интеллектуального анализа данных Association экспортируются в определенный файл. Вследствие того, что модель Association является частью структуры интеллектуального анализа Market Basket, в примере также экспортируется структура Market Basket. Других моделей интеллектуального анализа данных, которые могут существовать как частью структуры интеллектуального анализа данных «Потребительская корзина» не будут экспортироваться, потому что модель Association была экспортирована с помощью **МОДЕЛИ интеллектуального анализа данных**, а не **СТРУКТУРЫ интеллектуального анализа данных**.  
  
```  
EXPORT MINING STRUCTURE [Targeted Mailing], [Forecasting] MINING MODEL Association TO 'C:\TM_NEW.abf'  
```  
  
## <a name="export-mining-model-example"></a>Пример экспорта модели интеллектуального анализа данных  
 В следующем примере модель интеллектуального анализа данных Association экспортируется в определенный файл. Так как инструкция указывает **WITH DEPENDENCIES**, источник данных и объекты представления источника данных также включаются в ABF-файл.  
  
```  
EXPORT MINING MODEL [Association] TO 'C:\Association_NEW.abf' WITH DEPENDENCIES  
```  
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; инструкции определения данных](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; инструкции обработки данных](../dmx/dmx-statements-data-manipulation.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; Справка по инструкции](../dmx/data-mining-extensions-dmx-statements.md)   
 [ИМПОРТ &AMP;#40;РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ&AMP;#41;](../dmx/import-dmx.md)   
 [Экспорт и импорт объектов интеллектуального анализа данных](../analysis-services/data-mining/export-and-import-data-mining-objects.md)  
  
  
