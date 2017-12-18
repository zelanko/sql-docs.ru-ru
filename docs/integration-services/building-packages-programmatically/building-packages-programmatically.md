---
title: "Программное построение пакетов | Документы Майкрософт"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: building-packages-programmatically
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 7474b1f4-7607-4f28-a6fd-67f7db1dd3f8
caps.latest.revision: "26"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 88e58bc5a10c7b42f33fe1dae255114a919af556
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="building-packages-programmatically"></a>Программное построение пакетов
  Если необходимо динамическое создание пакетов или управление и выполнение пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] вне среды разработки, то можно управлять пакетами программно. Этот подход предлагает следующий набор вариантов.  
  
-   Загрузка и выполнение существующего пакета без изменения.  
  
-   Загрузка существующего пакета, изменение его конфигурации (например, для другого источника данных) и выполнение пакета.  
  
-   Создание нового пакета, добавление и настройка компонентов поочередно для каждого объекта и для каждого свойства, сохранение пакета и выполнение пакета.  
  
 Можно использовать модель объектов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], чтобы написать код, который создает, настраивает и выполняет пакеты на любом языке программирования управляемого кода. Например, может потребоваться создать управляемые метаданными пакеты, которые настраивают свои соединения или свои источники данных, преобразования и назначения на основании выбранного источника данных и его таблиц и столбцов.  
  
 В этом разделе описывается и демонстрируется пошаговое создание и настройка пакета программным способом. Используя наименее сложный вариант из набора вариантов программирования пакетов, можно просто загрузить и выполнить существующий пакет, не внося в него изменения, как описано в разделе [Выполнение пакетов и управление пакетами программным образом](../../integration-services/run-manage-packages-programmatically/running-and-managing-packages-programmatically.md).  
  
 В качестве промежуточного, не описываемого здесь варианта, может быть предложен вариант загрузки существующего пакета в виде шаблона, его перенастройки (например, для другого источника данных) и выполнения. Сведения данного раздела можно использовать для изменения существующих объектов в пакете.  
  
> [!NOTE]  
>  При использовании существующего пакета в качестве шаблона и при изменении существующих столбцов в потоке данных, может понадобиться удалить существующие столбцы и вызывать метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> затронутых компонентов.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Создание пакета программным способом](../../integration-services/building-packages-programmatically/creating-a-package-programmatically.md)  
 Описывает создание пакета программным образом.  
  
 [Программное добавление задач](../../integration-services/building-packages-programmatically/adding-tasks-programmatically.md)  
 Описывает добавление задач в пакет.  
  
 [Соединение задач программным образом](../../integration-services/building-packages-programmatically/connecting-tasks-programmatically.md)  
 Описывает управление выполнением контейнеров и задач в пакете на основе результатов выполнения предыдущей задачи или предыдущего контейнера.  
  
 [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)  
 Описывает добавление в пакет диспетчеров соединений.  
  
 [Программная работа с переменными](../../integration-services/building-packages-programmatically/working-with-variables-programmatically.md)  
 Описывает добавление и использование переменных во время выполнения пакета.  
  
 [Программная обработка событий](../../integration-services/building-packages-programmatically/handling-events-programmatically.md)  
 Описывает обработку событий пакета и задачи.  
  
 [Программное включение ведения журнала](../../integration-services/building-packages-programmatically/enabling-logging-programmatically.md)  
 Описывает включение ведения журнала для пакета или задачи и применение пользовательских фильтров для записи в журнал событий.  
  
 [Добавление задачи потока данных программным образом](../../integration-services/building-packages-programmatically/adding-the-data-flow-task-programmatically.md)  
 Описывает добавление и настройку задачи потока данных и ее компонентов.  
  
 [Программный поиск компонентов потока данных](../../integration-services/building-packages-programmatically/discovering-data-flow-components-programmatically.md)  
 Описывает обнаружение компонентов, установленных на локальном компьютере.  
  
 [Добавление компонентов потока данных программным образом](../../integration-services/building-packages-programmatically/adding-data-flow-components-programmatically.md)  
 Описывает добавление компонента в задачу потока данных.  
  
 [Программное соединение компонентов потока данных](../../integration-services/building-packages-programmatically/connecting-data-flow-components-programmatically.md)  
 Описывает соединение двух компонентов потока данных.  
  
 [Выбор входных столбцов программным образом](../../integration-services/building-packages-programmatically/selecting-input-columns-programmatically.md)  
 Описывает выбор входных столбцов из столбцов, предоставленных компоненту вышестоящими компонентами потока данных.  
  
 [Сохранение пакета программным образом](../../integration-services/building-packages-programmatically/saving-a-package-programmatically.md)  
 Описывает сохранение пакета программным образом.  
  
## <a name="reference"></a>Справочник  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)  
 Содержится список стандартных кодов ошибок служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с символическими именами и описаниями.  
  
## <a name="related-sections"></a>См. также  
 [Расширение пакетов с помощью сценариев](../../integration-services/extending-packages-scripting/extending-packages-with-scripting.md)  
 Описываются вопросы расширения потока управления с помощью задачи «Скрипт» и расширения потока данных с помощью компонента скрипта.  
  
 [Расширение пакетов с помощью пользовательских объектов](../../integration-services/extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 Описываются вопросы программирования пользовательских задач, компонентов потока данных и других объектов пакета, используемых в нескольких пакетах.  
  
 [Выполнение пакетов и управление пакетами программным образом](../../integration-services/run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)  
 Рассматривается перечисление, выполнение и управление пакетами и папками, в которых они хранятся.  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
-   Образцы CodePlex, [Образцы продуктов служб Integration Services](http://go.microsoft.com/fwlink/?LinkID=131204)на сайте www.codeplex.com/MSFTISProdSamples  
  
-   Запись в блоге [Профилирование производительности пользовательских расширений](http://go.microsoft.com/fwlink/?LinkId=238831)на сайте blogs.msdn.com.  

## <a name="see-also"></a>См. также:  
 [службы SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)  
  
  
