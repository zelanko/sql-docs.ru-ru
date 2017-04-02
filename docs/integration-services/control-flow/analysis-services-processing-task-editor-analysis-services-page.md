---
title: "Редактор задачи &#171;Обработка средствами Analysis Services&#187; (страница &#171;Средства Analysis Services&#187;) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.asprocessingtask.as.f1"
helpviewer_keywords: 
  - "редактор задачи «Обработка средствами Analysis Services»"
ms.assetid: 5612be78-57cf-4e4e-92cf-6bfa9f971040
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 29
---
# Редактор задачи &#171;Обработка средствами Analysis Services&#187; (страница &#171;Средства Analysis Services&#187;)
  Используйте страницу **Службы Analysis Services** диалогового окна **Редактор задачи «Обработка средствами Analysis Services»** для задания диспетчера соединений служб Analysis Services, выбора аналитических объектов для обработки, установки параметров обработки и действий при ошибках.  
  
 При обработке табличных моделей имейте в виду следующее.  
  
1.  Невозможно выполнить анализ влияния на табличных моделях.  
  
2.  Не отображаются некоторые параметры обработки для табличного режима, такие как процесс дефрагментации и процесс повторного вычисления. Эти функции вы можете выполнить с помощью задачи «Выполнение инструкции DDL».  
  
3.  Некоторые предоставляемые параметры обработки, например индексы обработки, не подходят для табличных моделей, поэтому они не должны использоваться.  
  
4.  Параметры пакетов не учитываются в табличных моделях.  
  
 Дополнительные сведения об этой задаче см. в разделе [Analysis Services Processing Task](../../integration-services/control-flow/analysis-services-processing-task.md).  
  
## Параметры  
 **диспетчер соединений служб Analysis Services**  
 Выберите из списка существующий диспетчер подключений служб Analysis Services или нажмите кнопку **Создать** для его создания.  
  
 **Создать**  
 Создайте новый диспетчер соединений служб Analysis Services.  
  
 **См. также:** [Диспетчер соединений служб Analysis Services](../../integration-services/connection-manager/analysis-services-connection-manager.md), [Добавление диалогового окна "Диспетчер соединений со службами Analysis Services" в справочник по пользовательскому интерфейсу](../../integration-services/connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 **Список объектов**  
 |Свойство|Description|  
|--------------|-----------------|  
|**Имя объекта**|Позволяет отобразить список имен заданных объектов.|  
|**Тип**|Позволяет отобразить список типов заданных объектов.|  
|**Параметры обработки**|Выберите из списка параметр обработки.<br /><br /> **См. также**: [Обработка многомерной модели (службы Analysis Services)](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)|  
|**Настройки**|Позволяет отобразить список настроек обработки для заданных объектов.|  
  
 **Добавить**  
 Добавьте объект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в список.  
  
 **Удалить**  
 Выделите объект, а затем нажмите кнопку **Удалить**.  
  
 **Анализ влияния**  
 Выполните анализ влияния на выбранный объект.  
  
 **См. также:** [Диалоговое окно "Анализ влияния" (службы Analysis Services — многомерные данные)](../Topic/Impact%20Analysis%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
 **Сводка о настройках пакета**  
 |Свойство|Description|  
|--------------|-----------------|  
|**Порядок обработки**|Позволяет задать, будут ли объекты обрабатываться последовательно или в составе пакета. При использовании параллельной обработки задает количество объектов для одновременной обработки.|  
|**Режим транзакции**|Позволяет задать режим транзакции для последовательной обработки.|  
|**Ошибки измерения**|Позволяет задать реакцию задачи на возникновение ошибок.|  
|**Путь к журналу ошибок ключа измерения**|Позволяет задать путь к файлу журнала, в который записываются ошибки.|  
|**Обработать затронутые объекты**|Позволяет указать, необходимо ли обрабатывать зависимые или затрагиваемые объекты.|  
  
 **Изменить настройки**  
 Измените параметры обработки и действия при ошибках в ключах измерения.  
  
 **См. также:** [Диалоговое окно "Изменение настроек" (службы Analysis Services — многомерные данные)](../Topic/Change%20Settings%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "Обработка средствами Analysis Services" (страница "Общие")](../../integration-services/control-flow/analysis-services-processing-task-editor-general-page.md)   
 [Задача «Выполнение инструкции DDL служб Analysis Services»](../../integration-services/control-flow/analysis-services-execute-ddl-task.md)  
  
  