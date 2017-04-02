---
title: "Редактор задачи &#171;Выполнение инструкции DDL служб Analysis Services&#187; (страница DDL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.asexecuteddltask.ddl.f1"
helpviewer_keywords: 
  - "редактор задачи «Выполнение инструкции DDL служб Analysis Services»"
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# Редактор задачи &#171;Выполнение инструкции DDL служб Analysis Services&#187; (страница DDL)
  Используйте страницу **DDL** диалогового окна **Редактор задачи "Выполнение инструкции DDL служб аналитики"**, чтобы настроить соединение с проектом [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или базой данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], а также предоставить сведения об источнике инструкций языка определения данных (DDL).  
  
 Дополнительные сведения об этой задаче см. в разделе [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md).  
  
## Статические параметры  
 **Соединение**  
 Выберите проект [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или диспетчер соединений [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из списка или нажмите кнопку \<**Новое соединение...**> и создайте новое соединение с помощью диалогового окна **Добавление диспетчера соединений служб Analysis Services**.  
  
 **См. также:** [Добавление диалогового окна "Диспетчер соединений со службами Analysis Services" в справочнике по пользовательскому интерфейсу](../../integration-services/connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md), [Диспетчер соединений служб Analysis Services](../../integration-services/connection-manager/analysis-services-connection-manager.md)  
  
 **Тип источника**  
 Указать тип источника инструкции DDL. Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Прямой ввод**|Установите в качестве источника инструкцию DDL, содержащуюся в текстовом поле **SourceDirect**. При выборе этого значения в следующем подразделе отображаются динамические параметры.|  
|**Соединение с файлом**|В качестве источника указывается файл, содержащий инструкцию DDL. При выборе этого значения в следующем подразделе отображаются динамические параметры.|  
|**Переменная**|Установите в качестве источника переменную. При выборе этого значения в следующем подразделе отображаются динамические параметры.|  
  
## Динамические параметры  
  
### SourceType = Прямой ввод  
 **Source**  
 Введите инструкцию DDL или нажмите кнопку с многоточием **(…)** и после этого введите инструкции в диалоговом окне **Инструкции DDL**.  
  
### SourceType = Подключение файла  
 **Source**  
 Выберите "Соединение с файлом" из списка или нажмите кнопку \<**Новое соединение...**> и создайте новое соединение с помощью диалогового окна **Диспетчер соединения файлов**.  
  
 **См. также:** [Диспетчер соединения файлов](../../integration-services/connection-manager/file-connection-manager.md)  
  
### SourceType = Переменная  
 **Source**  
 Выберите переменную из списка или нажмите \<**Новая переменная...**> и создайте новую переменную с помощью диалогового окна **Добавление переменной**.  
  
 **См. также:** [Переменные в службах Integration Services](../../integration-services/integration-services-ssis-variables.md)  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "Выполнение инструкции DDL служб Analysis Services" (страница "Общие")](../../integration-services/control-flow/analysis-services-execute-ddl-task-editor-general-page.md)   
 [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)   
 [Поток управления](../../integration-services/control-flow/control-flow.md)   
 [Справочник по языку ASSL (ASSL для XMLA)](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [Справочник по XML для аналитики (XMLA)](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  