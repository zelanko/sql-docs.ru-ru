---
title: Табличной модели, справочник по Скриптовому языку (TMSL) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c353266a96799672772a3c037ef14be45e2b6144
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="tabular-model-scripting-language-tmsl-reference"></a>Справочник по Скриптовому языку (TMSL) табличной модели
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

  Табличные языка скриптов модели (TMSL) приведен синтаксис определение команды и объект модели для баз данных табличной модели служб Analysis Services на уровне совместимости 1200 или выше. TMSL взаимодействует со службами Analysis Services через протокол XML для Аналитики, где [XML для Аналитики. Выполнение](../analysis-services/xmla/xml-elements-methods-execute.md) метод ресурс принимает как на основе JSON- **инструкции** скрипты TMSL, а также в традиционные сценарии XML в [язык сценариев служб Analysis Services &#40;языка ASSL для XMLA&#41; ](../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md).  
  
 Ниже приведены ключевые элементы TMSL:  
  
-   Табличных метаданных, в соответствии с семантикой табличной модели. Табличной модели состоит из таблицы, столбцы и связи. Эквивалентный объект определения в TMSL: теперь, не удивительно, что таблицы, столбцы, связи и т. д.  
  
     Новый механизм метаданных поддерживает следующие определения.  
  
-   Определения объектов структурированы в форме JSON вместо XML.  
  
 За исключением форматирование полезных данных (в JSON или XML) ASSL и TMSL, функционально эквивалентны, в том, как они предоставляют команды и метаданных XML для Аналитики методы, используемые для сервера связи и передачу данных.  
  
## <a name="how-to-use-tmsl"></a>Как использовать TMSL  
 Самый простой способ просмотра сценариев TMSL использует команд CREATE, ALTER, DELETE или процесс в SQL Server Management Studio (SSMS) для модели, вы уже знаете. Предположим, что вы используете существующую модель, не забудьте обновить ее до уровня совместимости 1200 или выше.  
  
1.  Найти команду, вы хотите использовать: [команд в языке скриптов табличных моделей &#40;TMSL&#41;](../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md)  
  
2.  Проверьте определение ссылку объекта для объектов, используемых в команде: [определений объектов в языке скриптов табличных моделей &#40;TMSL&#41;](../analysis-services/tabular-models-scripting-language-objects/tmsl-reference-tabular-objects.md)  
  
3.  Выберите метод для отправки TMSL сценарий:  
  
    -   Окно XMLA в среде Management Studio  
  
    -   **Invoke-ascmd** через объекты AMO PowerShell ([командлета Invoke-ASCmd](../analysis-services/powershell/invoke-ascmd-cmdlet.md))  
  
    -   [Analysis Services задача выполнения DDL](../integration-services/control-flow/analysis-services-execute-ddl-task.md) служб SSIS.  
  
## <a name="model-definition-schema"></a>Схема определения модели  
 На следующем снимке экрана показано сокращенную версию схемы, сворачивать, чтобы показать основные объекты.  
  
 ![SSAS_TabularMetadata](../analysis-services/media/ssas-tabularmetadata.JPG "SSAS_TabularMetadata")  
  
## <a name="scripting-languages-in-analysis-services"></a>Языки сценариев служб Analysis Services  
 Службы Analysis Services поддерживают языки сценариев ASSL и TMSL. В TMS описаны только табличных моделей, созданных на уровне совместимости 1200 или более поздней версии в формате JSON.  
  
 [Язык сценариев служб Analysis Services &#40;языка ASSL для XMLA&#41; ](../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md) был первый язык сценариев и остается только язык сценариев для многомерных и табличных моделей на более низких уровнях совместимости (1100 или 1103). В языке ASSL, табличных моделей на 110 x описаны в многомерные условия, такие как **куба** (для модели) и **measuregroup** (для таблицы).  
  
> [!NOTE]  
>  В [SQL Server Data Tools (SSDT), можно выполнить обновление более ранней версии табличную модель с помощью переключения вверх TMSL его **CompatibilityLevel** 1200 или выше. Помните, что обновление является необратимой операцией. Перед обновлением, резервное копирование модели при необходимости исходной версии более поздней версии.  
  
 В следующей таблице приведен матрице язык сценариев для моделей данных служб Analysis Services в разных версиях на уровнях совместимости.  

||||||  
|-|-|-|-|-|  
|**Версия**|**Многомерные**|**Табличные 110 x**|**Tabular 1200**| **Табличные 1400** |
|Службы Analysis Services|Н/Д|Н/Д|TMSL|TMSL| 
|SQL Server 2017|ASSL|ASSL|TMSL|TMSL| 
|SQL Server 2016|ASSL|ASSL|TMSL|TMSL| 
|SQL Server 2014|ASSL|ASSL|Н/Д|Н/Д|   
|SQL Server 2012|ASSL|ASSL|Н/Д|Н/Д|  

  
## <a name="see-also"></a>См. также  
 [Уровень совместимости для табличных моделей в службах Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Язык ASSL &#40;ASSL XML для Аналитики.&#41;](../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [Определение режима работы сервера экземпляра служб Analysis Services](../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
