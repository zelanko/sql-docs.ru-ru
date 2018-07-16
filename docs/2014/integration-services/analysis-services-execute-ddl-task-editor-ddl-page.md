---
title: Analysis Services редактор выполнение инструкции DDL задачи (страница DDL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asexecuteddltask.ddl.f1
helpviewer_keywords:
- Analysis Services Execute DDL Task Editor
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
caps.latest.revision: 29
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8693bb66bb848301a739a16f6989537d203eca25
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37269436"
---
# <a name="analysis-services-execute-ddl-task-editor-ddl-page"></a>Редактор задачи «Выполнение инструкции DDL служб Analysis Services» (страница DDL)
  Используйте страницу **DDL** диалогового окна **Редактор задачи "Выполнение инструкции DDL служб аналитики"**, чтобы настроить соединение с проектом [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] или базой данных [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], а также предоставить сведения об источнике инструкций языка определения данных (DDL).  
  
 Дополнительные сведения об этой задаче см. в разделе [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md).  
  
## <a name="static-options"></a>Статические параметры  
 **Соединение**  
 Выберите проект [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] или диспетчер соединений [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] из списка или нажмите кнопку \<**Новое соединение...**> и создайте новое соединение с помощью диалогового окна **Добавление диспетчера соединений со службами Analysis Services**.  
  
 **См. также:** [Добавление диалогового окна "Диспетчер соединений со службами Analysis Services" в справочнике по пользовательскому интерфейсу](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md), [Диспетчер соединений служб Analysis Services](connection-manager/analysis-services-connection-manager.md)  
  
 **Тип источника**  
 Указать тип источника инструкции DDL. Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Прямой ввод**|Установите в качестве источника инструкцию DDL, содержащуюся в текстовом поле **SourceDirect** . При выборе этого значения в следующем подразделе отображаются динамические параметры.|  
|**Соединение с файлом**|В качестве источника указывается файл, содержащий инструкцию DDL. При выборе этого значения в следующем подразделе отображаются динамические параметры.|  
|**Переменная**|Установите в качестве источника переменную. При выборе этого значения в следующем подразделе отображаются динамические параметры.|  
  
## <a name="dynamic-options"></a>Динамические параметры  
  
### <a name="sourcetype--direct-input"></a>SourceType = Прямой ввод  
 **Source**  
 Введите инструкцию DDL или нажмите кнопку с многоточием **(…)** и после этого введите инструкции в диалоговом окне **Инструкции DDL** .  
  
### <a name="sourcetype--file-connection"></a>SourceType = Подключение файла  
 **Source**  
 Выберите "Соединение с файлом" из списка или нажмите кнопку \<**Новое соединение...**> и создайте новое соединение с помощью диалогового окна **Диспетчер соединения файлов**.  
  
 **См. также:** [Диспетчер соединения файлов](connection-manager/file-connection-manager.md)  
  
### <a name="sourcetype--variable"></a>SourceType = Переменная  
 **Source**  
 Выберите переменную из списка или нажмите \<**Новая переменная...**> и создайте новую переменную с помощью диалогового окна **Добавление переменной**.  
  
 **См. также:** [Переменные в службах Integration Services](integration-services-ssis-variables.md)  
  
## <a name="see-also"></a>См. также  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Analysis Services редактор выполнение инструкции DDL задач &#40;страница "Общие"&#41;](general-page-of-integration-services-designers-options.md)   
 [Страница «выражения»](expressions/expressions-page.md)   
 [Поток управления](control-flow/control-flow.md)   
 [Язык сценариев Analysis Services &#40;ASSL&#41; ссылки](../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [XML для аналитики &#40;XMLA&#41; ссылки](../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
