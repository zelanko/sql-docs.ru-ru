---
title: Редактор задач веб-служб (страница «Вывод») | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.webservicestask.output.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: bcf7bd1ce50b19f62de5f249a1f89a4fdda0f5b0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095952"
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
 [Об ошибках служб Integration Services и справочник по сообщениям](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задач веб-служба &#40;страница «Общие»&#41;](general-page-of-integration-services-designers-options.md)   
 [Редактор задач веб-служба &#40;страница «Вход»&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [Страница "Выражения"](expressions/expressions-page.md)  
  
  