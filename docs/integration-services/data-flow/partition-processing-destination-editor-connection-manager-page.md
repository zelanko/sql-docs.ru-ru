---
title: "Редактор назначения обработки секций (страница &#171;Диспетчер соединений&#187;) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.partprocessingtransformation.connection.f1"
helpviewer_keywords: 
  - "редактор назначения «Обработка секций»"
ms.assetid: 7add6f82-eed1-47fc-a5d7-7b91f3f24d34
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# Редактор назначения обработки секций (страница &#171;Диспетчер соединений&#187;)
  Используйте страницу **Диспетчер соединений** диалогового окна **Редактор назначения обработки секций** , чтобы определить соединение с проектом служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Дополнительные сведения о назначении «Обработка секций» см. в разделе [Partition Processing Destination](../../integration-services/data-flow/partition-processing-destination.md).  
  
> [!NOTE]  
>  Описанные здесь задачи не применимы к табличным моделям служб Analysis Services.  Нельзя связать входные столбцы со столбцами секционирования для табличных моделей. Вместо этого для обработки секции следует использовать задачу выполнения DDL [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) служб Analysis Services.  
  
## Параметры  
 **Диспетчер соединений**  
 Выберите из списка существующий диспетчер соединений или создайте новое соединение, нажав кнопку **Создать**.  
  
 **Создать**  
 Создайте новое соединение, воспользовавшись диалоговым окном **Добавление диспетчера соединений со службами Analysis Services**.  
  
 **Список доступных секций**  
 Выберите секцию для обработки.  
  
 **Метод обработки**  
 Выберите метод обработки. Значение этого параметра по умолчанию — **Полная**.  
  
|Значение|Description|  
|-----------|-----------------|  
|Добавление (дополнительное)|Выполнить дополнительную обработку секции.|  
|Полный|Выполнить полную обработку секции.|  
|Только данные|Выполнить обработку обновления секции.|  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор назначения "Обработка секций" (страница "Сопоставления")](../../integration-services/data-flow/partition-processing-destination-editor-mappings-page.md)   
 [Редактор назначения "Обработка секций" (страница "Дополнительно")](../../integration-services/data-flow/partition-processing-destination-editor-advanced-page.md)  
  
  