---
title: Редактор задачи «Выполнение инструкции DDL Analysis Services» (страница «DDL») | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asexecuteddltask.ddl.f1
helpviewer_keywords:
- Analysis Services Execute DDL Task Editor
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2b57ad76be3811352bbfb8774fb56c748efa1ac8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66061608"
---
# <a name="analysis-services-execute-ddl-task-editor-ddl-page"></a>Редактор задачи «Выполнение инструкции DDL служб Analysis Services» (страница DDL)
  Используйте страницу **DDL** диалогового окна **Редактор задачи "Выполнение инструкции DDL служб аналитики"** , чтобы настроить соединение с проектом [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] или базой данных [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , а также предоставить сведения об источнике инструкций языка определения данных (DDL).  
  
 Дополнительные сведения об этой задаче см. в разделе [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md).  
  
## <a name="static-options"></a>Статические параметры  
 **Соединен**  
 Выберите проект [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] или диспетчер соединений [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] из списка или нажмите кнопку \<**Новое соединение...**> и создайте новое соединение с помощью диалогового окна **Добавление диспетчера соединений со службами Analysis Services**.  
  
 **См. также:** [диалоговое окно "Добавление Analysis Services диспетчера соединений" Справочник по интерфейсу пользователя](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md) [Analysis Services диспетчер соединений](connection-manager/analysis-services-connection-manager.md)  
  
 **SourceType**  
 Указать тип источника инструкции DDL. Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Прямой ввод**|Установите в качестве источника инструкцию DDL, содержащуюся в текстовом поле **SourceDirect** . При выборе этого значения в следующем подразделе отображаются динамические параметры.|  
|**Соединение с файлом**|В качестве источника указывается файл, содержащий инструкцию DDL. При выборе этого значения в следующем подразделе отображаются динамические параметры.|  
|**Перемен**|Установите в качестве источника переменную. При выборе этого значения в следующем подразделе отображаются динамические параметры.|  
  
## <a name="dynamic-options"></a>Динамические параметры  
  
### <a name="sourcetype--direct-input"></a>SourceType = Прямой ввод  
 **Source**  
 Введите инструкции DDL или нажмите кнопку с многоточием **(…)** и после этого введите инструкции в диалоговом окне **Инструкции DDL**.  
  
### <a name="sourcetype--file-connection"></a>SourceType = Подключение файла  
 **Source**  
 Выберите "Соединение с файлом" из списка или нажмите кнопку \<**Новое соединение...**> и создайте новое соединение с помощью диалогового окна **Диспетчер соединения файлов**.  
  
 **См. также:** [Диспетчер подключения файлов](connection-manager/file-connection-manager.md)  
  
### <a name="sourcetype--variable"></a>SourceType = Переменная  
 **Source**  
 Выберите переменную из списка или нажмите \<**Новая переменная...**> и создайте новую переменную с помощью диалогового окна **Добавление переменной**.  
  
 **См. также:** [Integration Services &#40;переменные&#41; SSIS](integration-services-ssis-variables.md)  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "Analysis Services выполнение инструкции DDL" &#40;страница "Общие"&#41;](general-page-of-integration-services-designers-options.md)   
 [Страница "выражения"](expressions/expressions-page.md)   
 [Поток управления](control-flow/control-flow.md)   
 [Справочник по языку сценариев Analysis Services &#40;языка ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)   
 [Справочник по XML для аналитики &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)  
  
  
