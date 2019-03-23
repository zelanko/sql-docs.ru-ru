---
title: Редактор задач веб-служба (страница "Вывод") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.output.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4cfeac28676dc8134c7eedf1e4b27901e0f053dc
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58377932"
---
# <a name="web-service-task-editor-output-page"></a>Редактор задачи «Веб-служба» (страница «Вывод»)
  Используйте страницу **Вывод** диалогового окна **Редактор задачи «Веб-служба»** , чтобы указать, где следует хранить результаты, возвращенные веб-методом.  
  
 Дополнительные сведения об этой задаче см. в разделе [Задача "Веб-служба"](control-flow/web-service-task.md).  
  
## <a name="static-options"></a>Статические параметры  
 **OutputType**  
 Выберите тип хранения, используемый для хранения результатов. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Соединение с файлом**|Хранить результаты в файле. При выборе этого значения отображается динамический параметр **Файл**.|  
|**Переменная**|Хранить результаты в переменной. При выборе этого значения отображается динамический параметр **Переменная**.|  
  
## <a name="outputtype-dynamic-options"></a>Динамические параметры OutputType  
  
### <a name="outputtype--file-connection"></a>OutputType = Соединение с файлом  
 **Файл**  
 Выберите диспетчер подключений файлов в списке или щелкните \<**Создать соединение...**>, чтобы создать его.  
  
 **См. также:** [Диспетчер подключения файлов](connection-manager/file-connection-manager.md), [редактор диспетчера подключения файлов](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="outputtype--variable"></a>OutputType = Переменная  
 **Переменная**  
 Выберите переменную в списке или щелкните \<**Создать переменную...**>, чтобы создать ее.  
  
 **См. также:**  [Службы Integration Services &#40;SSIS&#41; переменных](integration-services-ssis-variables.md), [добавить переменную](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "Веб-служба" (страница "Общие")](general-page-of-integration-services-designers-options.md)   
 [Редактор задачи "Веб-служба" (страница "Ввод")](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [Страница «Выражения»](expressions/expressions-page.md)  
  
  
