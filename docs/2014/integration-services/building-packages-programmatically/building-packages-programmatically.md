---
title: Программное построение пакетов | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 7474b1f4-7607-4f28-a6fd-67f7db1dd3f8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b49f6b4ae3ec88339927f083b58e016dbc38639b
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53370426"
---
# <a name="building-packages-programmatically"></a>Программное построение пакетов
  Если необходимо динамическое создание пакетов или управление и выполнение пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] вне среды разработки, то можно управлять пакетами программно. Этот подход предлагает следующий набор вариантов.  
  
-   Загрузка и выполнение существующего пакета без изменения.  
  
-   Загрузка существующего пакета, изменение его конфигурации (например, для другого источника данных) и выполнение пакета.  
  
-   Создание нового пакета, добавление и настройка компонентов поочередно для каждого объекта и для каждого свойства, сохранение пакета и выполнение пакета.  
  
 Можно использовать модель объектов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , чтобы написать код, который создает, настраивает и выполняет пакеты на любом языке программирования управляемого кода. Например, может потребоваться создать управляемые метаданными пакеты, которые настраивают свои соединения или свои источники данных, преобразования и назначения на основании выбранного источника данных и его таблиц и столбцов.  
  
 В этом разделе описывается и демонстрируется пошаговое создание и настройка пакета программным способом. Используя наименее сложный вариант из набора вариантов программирования пакетов, можно просто загрузить и выполнить существующий пакет, не внося в него изменения, как описано в разделе [Выполнение пакетов и управление пакетами программным образом](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md).  
  
 В качестве промежуточного, не описываемого здесь варианта, может быть предложен вариант загрузки существующего пакета в виде шаблона, его перенастройки (например, для другого источника данных) и выполнения. Сведения данного раздела можно использовать для изменения существующих объектов в пакете.  
  
> [!NOTE]  
>  При использовании существующего пакета в качестве шаблона и при изменении существующих столбцов в потоке данных, может понадобиться удалить существующие столбцы и вызывать метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> затронутых компонентов.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Создание пакета программным способом](../building-packages-programmatically/creating-a-package-programmatically.md)  
 Описывает создание пакета программным образом.  
  
 [Программное добавление задач](../building-packages-programmatically/adding-tasks-programmatically.md)  
 Описывает добавление задач в пакет.  
  
 [Соединение задач программным образом](../building-packages-programmatically/connecting-tasks-programmatically.md)  
 Описывает управление выполнением контейнеров и задач в пакете на основе результатов выполнения предыдущей задачи или предыдущего контейнера.  
  
 [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md)  
 Описывает добавление в пакет диспетчеров соединений.  
  
 [Программная работа с переменными](../building-packages-programmatically/working-with-variables-programmatically.md)  
 Описывает добавление и использование переменных во время выполнения пакета.  
  
 [Программная обработка событий](../building-packages-programmatically/handling-events-programmatically.md)  
 Описывает обработку событий пакета и задачи.  
  
 [Программное включение ведения журнала](../building-packages-programmatically/enabling-logging-programmatically.md)  
 Описывает включение ведения журнала для пакета или задачи и применение пользовательских фильтров для записи в журнал событий.  
  
 [Добавление задачи потока данных программным образом](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md)  
 Описывает добавление и настройку задачи потока данных и ее компонентов.  
  
 [Программный поиск компонентов потока данных](../building-packages-programmatically/discovering-data-flow-components-programmatically.md)  
 Описывает обнаружение компонентов, установленных на локальном компьютере.  
  
 [Добавление компонентов потока данных программным образом](../building-packages-programmatically/adding-data-flow-components-programmatically.md)  
 Описывает добавление компонента в задачу потока данных.  
  
 [Программное соединение компонентов потока данных](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)  
 Описывает соединение двух компонентов потока данных.  
  
 [Выбор входных столбцов программным образом](../building-packages-programmatically/selecting-input-columns-programmatically.md)  
 Описывает выбор входных столбцов из столбцов, предоставленных компоненту вышестоящими компонентами потока данных.  
  
 [Сохранение пакета программным образом](../building-packages-programmatically/saving-a-package-programmatically.md)  
 Описывает сохранение пакета программным образом.  
  
## <a name="reference"></a>Ссылка  
 [Справочник по сообщениям об ошибках служб Integration Services](../integration-services-error-and-message-reference.md)  
 Содержится список стандартных кодов ошибок служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с символическими именами и описаниями.  
  
## <a name="related-sections"></a>См. также  
 [Расширение пакетов с помощью сценариев](../extending-packages-scripting/extending-packages-with-scripting.md)  
 Описываются вопросы расширения потока управления с помощью задачи «Скрипт» и расширения потока данных с помощью компонента скрипта.  
  
 [Расширение пакетов с помощью пользовательских объектов](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 Описываются вопросы программирования пользовательских задач, компонентов потока данных и других объектов пакета, используемых в нескольких пакетах.  
  
 [Выполнение пакетов и управление пакетами программным образом](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)  
 Рассматривается перечисление, выполнение и управление пакетами и папками, в которых они хранятся.  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
-   Образцы CodePlex, [Образцы продуктов служб Integration Services](https://go.microsoft.com/fwlink/?LinkID=131204)на сайте www.codeplex.com/MSFTISProdSamples  
  
-   Запись в блоге [Профилирование производительности пользовательских расширений](https://go.microsoft.com/fwlink/?LinkId=238831)на сайте blogs.msdn.com.  
  
![Значок служб Integration Services (маленький)](../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [службы SQL Server Integration Services](../sql-server-integration-services.md)  
  
  
