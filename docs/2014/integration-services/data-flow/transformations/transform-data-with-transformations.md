---
title: Преобразование данных с помощью преобразований | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data flow [Integration Services], transformations
- transformations [Integration Services], about transformations
- transforming data [Integration Services]
ms.assetid: e1340b6f-ef75-4b14-af6f-823586eff0ed
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fa5d7788650cd1a36dfcf3f59531ff4b09182b61
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437541"
---
# <a name="transform-data-with-transformations"></a>Преобразование данных с помощью преобразований
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] включают три различных типа компонентов потока данных: источники, преобразования и назначения.  
  
 На следующей диаграмме показан простой поток данных, который имеет источник, два преобразования и назначение.  
  
 ![Data flow](../../media/mw-dts-08.gif "Поток данных") (Поток данных)  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] обеспечивают следующие функциональные возможности:  
  
-   разделение, копирование и объединение наборов строк и выполнение операций уточняющего запроса;  
  
-   обновление значений столбца и создание новых столбцов путем применения преобразований, таких как изменение нижнего регистра в верхний регистр;  
  
-   выполнение операций бизнес-аналитики, таких как очистка данных, интеллектуальный анализ текста или выполнение запросов прогноза интеллектуального анализа данных;  
  
-   создание новых наборов строк, содержащих статистические или упорядоченные значения, образцы данных, сведенные данные или данные, сведение которых отменено;  
  
-   выполнение задач, таких как экспорт и импорт данных, предоставление данных аудита, работа с медленно изменяющимися измерениями.  
  
 Дополнительные сведения см. в статье [Integration Services Transformations](integration-services-transformations.md).  
  
 Также можно создавать пользовательские преобразования. Дополнительные сведения см. в разделах [Разработка пользовательского компонента потока данных](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) и [Разработка компонентов потока данных определенных типов](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md).  
  
 После добавления преобразования к конструктору потока данных, но до настройки преобразования нужно подключить преобразование к потоку данных путем подключения к входу данного преобразования выхода другого преобразования или источника в потоке данных. Соединитель компонентов потока данных называется путем. Дополнительные сведения о соединении компонентов и работе с путями см. в разделе [Соединение компонентов с путями](../../connect-components-with-paths.md).  
  
### <a name="to-add-a-transformation-to-a-data-flow"></a>Добавление преобразования к потоку данных  
  
-   [Добавление или удаление компонента в потоке данных](../add-or-delete-a-component-in-a-data-flow.md)  
  
### <a name="to-connect-a-transformation-to-a-data-flow"></a>Подключение преобразования к потоку данных  
  
-   [Соединение компонентов в потоке данных](../connect-components-in-a-data-flow.md)  
  
### <a name="to-set-the-properties-of-a-transformation"></a>Установка свойства преобразования  
  
-   [Установление свойств компонента потока данных](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="see-also"></a>См. также:  
 [Задача потока данных](../../control-flow/data-flow-task.md)   
 [Поток данных](../data-flow.md)   
 [Соединение компонентов с путями](../../connect-components-with-paths.md)   
 [Обработка ошибок в данных](../error-handling-in-data.md)   
 [Поток данных](../data-flow.md)  
  
  
