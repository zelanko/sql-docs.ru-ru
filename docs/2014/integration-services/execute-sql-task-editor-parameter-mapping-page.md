---
title: Выполнение задач редактор SQL (страница «сопоставление параметров») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.parametermapping.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: 8ebe020a-7921-46b2-8823-398748f379b2
caps.latest.revision: 42
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9c35360c4cddebecf7f6237071bc430b74f726cb
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39082956"
---
# <a name="execute-sql-task-editor-parameter-mapping-page"></a>Редактор задачи «Выполнение SQL» (страница «Сопоставление параметров»)
  Используйте страницу **Сопоставление параметров** диалогового окна **Редактор задачи «Выполнение SQL»** для сопоставления переменных с параметрами в инструкции SQL.  
  
 Сведения об этой задаче см. в разделах [Задача "Выполнение SQL"](control-flow/execute-sql-task.md) и [Параметры и коды возврата в задаче "Выполнение SQL"](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).  
  
## <a name="options"></a>Параметры  
 **Имя переменной**  
 После добавления сопоставления параметров нажатием кнопки **Добавить** выберите системную или пользовательскую переменную в списке или щелкните \<**Создать переменную...**> для добавления новой переменной с помощью диалогового окна **Добавление переменной**.  
  
 **См. также:** [Переменные в службах Integration Services](integration-services-ssis-variables.md)  
  
 **Направление**  
 Выбор направления для параметра. Сопоставьте каждую переменную с входным параметром, выходным параметром или кодом возврата.  
  
 **Тип данных**  
 Выберите тип данных для параметра. Список доступных типов данных зависит от поставщика, который был выбран в диспетчере соединений, используемом задачей.  
  
 **Имя параметра**  
 Введите имя параметра.  
  
 В зависимости от типа диспетчера соединений, используемого задачей, необходимо использовать числа или имена параметра. Некоторые типы диспетчеров соединений требуют, что первый символ имени параметра — \@ подписать, как и с определенными именами \@Param1 или столбец имена в качестве имен параметров.  
  
 **См. также:** [Параметры и коды возврата в задаче "Выполнение SQL"](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)  
  
 **Размер параметра**  
 Укажите размер для параметров, имеющих переменную длину, например, строк и двоичных полей.  
  
 Эта настройка гарантирует, что поставщик выделит достаточное пространство для значений параметров изменяемой длины.  
  
 **Добавить**  
 Нажмите для добавления сопоставления параметра.  
  
 **Удалить**  
 Выберите сопоставление параметра из списка, затем нажмите **Удалить**.  
  
## <a name="see-also"></a>См. также  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задач SQL Выполнение &#40;страница "Общие"&#41;](general-page-of-integration-services-designers-options.md)   
 [Редактор задач SQL Выполнение &#40;результирующий набор страниц&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md)   
 [Справочник по Transact-SQL (компонент Database Engine)](/sql/t-sql/language-reference)  
  
  
