---
title: "Редактор задачи &#171;Веб-служба&#187; (страница &#171;Вывод&#187;) | Microsoft Docs"
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
  - "sql13.dts.designer.webservicestask.output.f1"
helpviewer_keywords: 
  - "редактор задачи «Веб-служба»"
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# Редактор задачи &#171;Веб-служба&#187; (страница &#171;Вывод&#187;)
  Используйте страницу **Вывод** диалогового окна **Редактор задачи «Веб-служба»** , чтобы указать, где следует хранить результаты, возвращенные веб-методом.  
  
 Дополнительные сведения об этой задаче см. в разделе [Задача "Веб-служба"](../../integration-services/control-flow/web-service-task.md).  
  
## Статические параметры  
 **OutputType**  
 Выберите тип хранения, используемый для хранения результатов. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Соединение с файлом**|Хранить результаты в файле. При выборе этого значения отображается динамический параметр **Файл**.|  
|**Переменная**|Хранить результаты в переменной. При выборе этого значения отображается динамический параметр **Переменная**.|  
  
## Динамические параметры OutputType  
  
### OutputType = Соединение с файлом  
 **Файл**  
 Выберите диспетчер подключений файлов из списка или щелкните \<**Создать соединение...**>, чтобы создать его.  
  
 **См. также:** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### OutputType = Переменная  
 **Переменная**  
 Выберите переменную из списка или нажмите кнопку \<**Создать переменную...**>, чтобы создать переменную.  
  
 **См. также:** [Переменные в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-variables.md), [Добавление переменной](../Topic/Add%20Variable.md)  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "Веб-служба" (страница "Общие")](../../integration-services/control-flow/web-service-task-editor-general-page.md)   
 [Редактор задачи "Веб-служба" (страница "Ввод")](../../integration-services/control-flow/web-service-task-editor-input-page.md)   
 [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)  
  
  