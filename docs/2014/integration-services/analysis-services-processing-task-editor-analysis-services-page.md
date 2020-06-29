---
title: Редактор задачи "обработка Analysis Services" (страница "Analysis Services") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asprocessingtask.as.f1
helpviewer_keywords:
- Analysis Services Processing Task Editor
ms.assetid: 5612be78-57cf-4e4e-92cf-6bfa9f971040
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ab462b751215ed6573de20764f3dee0715e5f33
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439471"
---
# <a name="analysis-services-processing-task-editor-analysis-services-page"></a>Редактор задачи «Обработка средствами Analysis Services» (страница «Средства Analysis Services»)
  Используйте страницу **Службы Analysis Services** диалогового окна **Редактор задачи «Обработка средствами Analysis Services»** для задания диспетчера соединений служб Analysis Services, выбора аналитических объектов для обработки, установки параметров обработки и действий при ошибках.  
  
 При обработке табличных моделей имейте в виду следующее.  
  
1.  Невозможно выполнить анализ влияния на табличных моделях.  
  
2.  Не отображаются некоторые параметры обработки для табличного режима, такие как процесс дефрагментации и процесс повторного вычисления. Эти функции вы можете выполнить с помощью задачи «Выполнение инструкции DDL».  
  
3.  Некоторые предоставляемые параметры обработки, например индексы обработки, не подходят для табличных моделей, поэтому они не должны использоваться.  
  
4.  Параметры пакетов не учитываются в табличных моделях.  
  
 Дополнительные сведения об этой задаче см. в разделе [Analysis Services Processing Task](control-flow/analysis-services-processing-task.md).  
  
## <a name="options"></a>Параметры  
 **Диспетчер подключений Analysis Services**  
 Выберите из списка существующий диспетчер подключений служб Analysis Services или нажмите кнопку **Создать** для его создания.  
  
 **Новые**  
 Создайте новый диспетчер соединений служб Analysis Services.  
  
 **См. также:** [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md), [Добавление диалогового окна "Диспетчер соединений со службами Analysis Services" в справочник по пользовательскому интерфейсу](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 **Список объектов**  
 |Свойство|Описание:|  
|--------------|-----------------|  
|**Имени объекта**|Позволяет отобразить список имен заданных объектов.|  
|**Type**|Позволяет отобразить список типов заданных объектов.|  
|**Параметры обработки**|Выберите из списка параметр обработки.<br /><br /> **См. также**: [Обработка объектов многомерной модели](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services)|  
|**Параметры**|Позволяет отобразить список настроек обработки для заданных объектов.|  
  
 **Добавление**  
 Добавьте объект служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в список.  
  
 **Remove**  
 Выделите объект, а затем нажмите кнопку **Удалить**.  
  
 **Анализ влияния**  
 Выполните анализ влияния на выбранный объект.  
  
 **См. также:** [Диалоговое окно "Анализ влияния" (службы Analysis Services — многомерные данные)](../../2014/analysis-services/impact-analysis-dialog-box-analysis-services-multidimensional-data.md)  
  
 **Сводка о настройках пакета**  
 |Свойство|Описание:|  
|--------------|-----------------|  
|**Порядок обработки**|Позволяет задать, будут ли объекты обрабатываться последовательно или в составе пакета. При использовании параллельной обработки задает количество объектов для одновременной обработки.|  
|**Режим транзакции**|Позволяет задать режим транзакции для последовательной обработки.|  
|**Ошибки измерения**|Позволяет задать реакцию задачи на возникновение ошибок.|  
|**Путь к журналу ошибок ключа измерения**|Позволяет задать путь к файлу журнала, в который записываются ошибки.|  
|**Обработать затронутые объекты**|Позволяет указать, необходимо ли обрабатывать зависимые или затрагиваемые объекты.|  
  
 **Изменить параметры**  
 Измените параметры обработки и действия при ошибках в ключах измерения.  
  
 **См. также:** [Диалоговое окно "Изменение настроек" (службы Analysis Services — многомерные данные)](../../2014/analysis-services/change-settings-dialog-box-analysis-services-multidimensional-data.md)  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "обработка Analysis Services" &#40;страница "Общие"&#41;](general-page-of-integration-services-designers-options.md)   
 [Задача «Выполнение инструкции DDL служб Analysis Services»](control-flow/analysis-services-execute-ddl-task.md)  
  
  
