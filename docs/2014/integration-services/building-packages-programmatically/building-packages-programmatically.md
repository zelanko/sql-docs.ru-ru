---
title: Программное построение пакетов | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 7474b1f4-7607-4f28-a6fd-67f7db1dd3f8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f4227560fbaf3e618a25e3dd214a214ac68a736e
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2020
ms.locfileid: "78176559"
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
 [Создание пакета программным способом](../building-packages-programmatically/creating-a-package-programmatically.md) Описывает, как создать пакет программным способом.

 [Добавление задач программным способом](../building-packages-programmatically/adding-tasks-programmatically.md) Описывает добавление задач в пакет.

 [Программное подключение задач](../building-packages-programmatically/connecting-tasks-programmatically.md) Описывает, как управлять выполнением контейнеров и задач в пакете в зависимости от результата выполнения предыдущей задачи или контейнера.

 [Добавление соединений программным способом](../building-packages-programmatically/adding-connections-programmatically.md) Описывает добавление диспетчеров соединений в пакет.

 [Работа с переменными программным способом](../building-packages-programmatically/working-with-variables-programmatically.md) Описывает, как добавлять и использовать переменные во время выполнения пакета.

 [Программная обработка событий](../building-packages-programmatically/handling-events-programmatically.md) Описывает обработку событий пакета и задачи.

 [Включение ведения журнала программным способом](../building-packages-programmatically/enabling-logging-programmatically.md) Описывает включение ведения журнала для пакета или задачи, а также применение настраиваемых фильтров для записи событий в журнал.

 [Добавление задачи потока данных программным способом](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md) Описывает, как добавить и настроить задачу потока данных и ее компоненты.

 [Программное обнаружение компонентов потока данных](../building-packages-programmatically/discovering-data-flow-components-programmatically.md) Описывает, как определить компоненты, установленные на локальном компьютере.

 [Добавление компонентов потока данных программным способом](../building-packages-programmatically/adding-data-flow-components-programmatically.md) Описывает добавление компонента в задачу потока данных.

 [Программное подключение компонентов потока данных](../building-packages-programmatically/connecting-data-flow-components-programmatically.md) Описывает подключение двух компонентов потока данных.

 [Выбор входных столбцов программным способом](../building-packages-programmatically/selecting-input-columns-programmatically.md) Описывает, как выбрать входные столбцы из тех, которые предоставляются компоненту посредством восходящего компонента в потоке данных.

 [Сохранение пакета программным способом](../building-packages-programmatically/saving-a-package-programmatically.md) Описание способа сохранения пакета программным способом.

## <a name="reference"></a>Справочник
 [Справочник по ошибкам и сообщениям Integration Services](../integration-services-error-and-message-reference.md) Список стандартных [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] кодов ошибок со своими символическими именами и описаниями.

## <a name="related-sections"></a>См. также
 [Расширение пакетов с помощью сценариев](../extending-packages-scripting/extending-packages-with-scripting.md) Описывает, как расширить поток управления с помощью задачи «Скрипт» и как расширить поток данных с помощью компонента скрипта.

 [Расширение пакетов с помощью пользовательских объектов](../extending-packages-custom-objects/extending-packages-with-custom-objects.md) Описывает создание пользовательских задач, компонентов потока данных и других объектов пакета для использования в нескольких пакетах.

 [Программное выполнение пакетов и управление ими](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md) Описывает, как выполнять перечисление, запуск и Управление пакетами и папками, в которых они хранятся.

## <a name="external-resources"></a>Внешние ресурсы

-   Образцы CodePlex, [Образцы продуктов служб Integration Services](https://go.microsoft.com/fwlink/?LinkID=131204)на сайте www.codeplex.com/MSFTISProdSamples

-   Запись в блоге [Профилирование производительности пользовательских расширений](https://go.microsoft.com/fwlink/?LinkId=238831)на сайте blogs.msdn.com.

![Значок Integration Services (маленький)](../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.

## <a name="see-also"></a>См. также:
 [SQL Server Integration Services](../sql-server-integration-services.md)


