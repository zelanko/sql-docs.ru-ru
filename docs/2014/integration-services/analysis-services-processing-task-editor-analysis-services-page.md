---
title: Службы Analysis Services редактор задач обработки (страница Analysis Services) | Документация Майкрософт
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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a6a114cba7caa1fa223f21de2aa8cc4a85979fe1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66061470"
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
 **диспетчер соединений служб Analysis Services**  
 Выберите из списка существующий диспетчер подключений служб Analysis Services или нажмите кнопку **Создать** для его создания.  
  
 **Создать**  
 Создайте новый диспетчер соединений служб Analysis Services.  
  
 **См. также:** подробные сведения о [диспетчере подключений Analysis Services](connection-manager/analysis-services-connection-manager.md) и о [добавлении диалогового окна диспетчера подключений Analysis Services](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md).  
  
 **Список объектов**  
 |Свойство|Описание|  
|--------------|-----------------|  
|**Имя объекта**|Позволяет отобразить список имен заданных объектов.|  
|**Тип**|Позволяет отобразить список типов заданных объектов.|  
|**Параметры обработки**|Выберите из списка параметр обработки.<br /><br /> **См. также**: [Обработка объектов многомерной модели](../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)|  
|**Настройки**|Позволяет отобразить список настроек обработки для заданных объектов.|  
  
 **Добавить**  
 Добавьте объект служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в список.  
  
 **Удалить**  
 Выделите объект, а затем нажмите кнопку **Удалить**.  
  
 **Анализ влияния**  
 Выполните анализ влияния на выбранный объект.  
  
 **См. также:** подробные сведения о [диалоговом окне "Анализ влияния" &#40;Analysis Services — многомерные данные&#41;](../../2014/analysis-services/impact-analysis-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Сводка о настройках пакета**  
 |Свойство|Описание|  
|--------------|-----------------|  
|**Порядок обработки**|Позволяет задать, будут ли объекты обрабатываться последовательно или в составе пакета. При использовании параллельной обработки задает количество объектов для одновременной обработки.|  
|**Режим транзакции**|Позволяет задать режим транзакции для последовательной обработки.|  
|**Ошибки измерения**|Позволяет задать реакцию задачи на возникновение ошибок.|  
|**Путь к журналу ошибок ключа измерения**|Позволяет задать путь к файлу журнала, в который записываются ошибки.|  
|**Обработать затронутые объекты**|Позволяет указать, необходимо ли обрабатывать зависимые или затрагиваемые объекты.|  
  
 **Изменить настройки**  
 Измените параметры обработки и действия при ошибках в ключах измерения.  
  
 **См. также:** подробные сведения о [диалоговом окне "Изменение параметров" &#40;Analysis Services — многомерные данные&#41;](../../2014/analysis-services/change-settings-dialog-box-analysis-services-multidimensional-data.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "Обработка средствами Analysis Services" (страница "Общие")](general-page-of-integration-services-designers-options.md)   
 [Задача «Выполнение инструкции DDL служб Analysis Services»](control-flow/analysis-services-execute-ddl-task.md)  
  
  
