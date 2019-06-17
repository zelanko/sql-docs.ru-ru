---
title: Образец входного XML-файла с пользовательской конфигурацией (DTA) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- sample applications [DTA]
ms.assetid: b29c9716-e5c3-4003-9efb-3ade2197b630
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4fefcec96100a9848810bc37a7b02760a3005cc3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188095"
---
# <a name="xml-input-file-sample-with-user-specified-configuration-dta"></a>Образец входного XML-файла с пользовательской конфигурацией (DTA)
  Скопируйте и вставьте этот образец входного XML-файла, определяющего пользовательскую конфигурацию с помощью элемента **Конфигурация**, в свой привычный XML-редактор или редактор текста. Это позволит выполнить анализ гипотетических вариантов. Анализ гипотетических вариантов предполагает использование элемента **Конфигурация** , чтобы определить набор гипотетических структур физического проектирования для настраиваемой базы данных. Затем можно применить помощник по настройке ядра СУБД для анализа эффекта от запуска рабочей нагрузки с учетом этой гипотетической конфигурации с целью выяснить, насколько повышается производительность выполнения запросов. Этот тип анализа позволяет проводить оценку новой конфигурации без затрат, связанных с ее фактическим внедрением. Если гипотетическая конфигурация не дает желаемого увеличения производительности, ее можно легко изменить и снова проанализировать до получения конфигурации, позволяющей достигнуть желаемых результатов.  
  
 После копирования образца в редактор замените значения элементов **Server**, **Database**, **Schema**, **Table**, **Workload**, **TuningOptions**и **Configuration** значениями, соответствующими конкретным особенностям данного сеанса настройки. Дополнительные сведения обо всех атрибутах и дочерних элементов, которые можно использовать с этими элементами, см. в разделе [Справочник по входным файлам XML &#40;помощник по настройке ядра СУБД&#41;](xml-input-file-reference-database-engine-tuning-advisor.md). В следующем образце используется только подмножество доступных атрибутов и параметров дочерних элементов.  
  
## <a name="code"></a>Код  
 [!code-xml[InputFileSamples#UserSpecifiedConfigInputFile](../../snippets/xml/SQL14/dta_xml/inputfilesamples/xml/dta_xml_input_file_samples.xml#userspecifiedconfiginputfile)]  
  
## <a name="comments"></a>Комментарии  
  
-   Удаление структур физического проектирования при указании режима **Absolute** элемента **Configuration** (`Configuration SpecificationMode="Absolute"`) не поддерживается.  
  
-   Нельзя создавать и удалять одинаковые структуры физического проектирования в режимах**Relative** и **Absolute**элемента **Configuration** .  
  
## <a name="see-also"></a>См. также  
 [Запуск и использование помощника по настройке ядра СУБД](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)   
 [Просмотр и работа с выходными данными помощника по настройке ядра СУБД](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md)   
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
