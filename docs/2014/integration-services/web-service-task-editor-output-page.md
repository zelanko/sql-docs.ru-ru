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
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2e2a0c1639352b8c5aaad9be4bd6740eceacb6cf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48132014"
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
 Выберите диспетчер подключений файлов из списка или щелкните \<**Создать соединение…**>, чтобы создать его.  
  
 **См. также:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="outputtype--variable"></a>OutputType = Переменная  
 **Переменная**  
 Выберите переменную из списка или нажмите кнопку \<**Создать переменную…**>, чтобы создать переменную.  
  
 **См. также**: [Переменные в службах Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Добавление переменной](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>См. также  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задач веб-служба &#40;страница "Общие"&#41;](general-page-of-integration-services-designers-options.md)   
 [Редактор задач веб-служба &#40;страница «Вход»&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [Страница "Выражения"](expressions/expressions-page.md)  
  
  
