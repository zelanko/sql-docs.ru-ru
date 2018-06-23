---
title: Выполнение задач редактор SQL (страница «сопоставление параметров») | Документы Microsoft
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
- sql12.dts.designer.executesqltask.parametermapping.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: 8ebe020a-7921-46b2-8823-398748f379b2
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 863ae3b186cc60c4d2d2e04308dd81023f653f12
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102242"
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
  
 В зависимости от типа диспетчера соединений, используемого задачей, необходимо использовать числа или имена параметра. Некоторые типы диспетчеров подключений требуют, чтобы первым символом имени параметра был знак @ либо определенные имена, как @Param1, или имена столбцов в качестве имен параметров.  
  
 **См. также:** [Параметры и коды возврата в задаче "Выполнение SQL"](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)  
  
 **Размер параметра**  
 Укажите размер для параметров, имеющих переменную длину, например, строк и двоичных полей.  
  
 Эта настройка гарантирует, что поставщик выделит достаточное пространство для значений параметров изменяемой длины.  
  
 **Добавить**  
 Нажмите для добавления сопоставления параметра.  
  
 **Удалить**  
 Выберите сопоставление параметра из списка, затем нажмите **Удалить**.  
  
## <a name="see-also"></a>См. также  
 [Об ошибках служб Integration Services и справочник по сообщениям](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Выполнение задач редактор SQL &#40;страница «Общие»&#41;](general-page-of-integration-services-designers-options.md)   
 [Выполнение задач редактор SQL &#40;«результирующий набор»&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md)   
 [Справочник по Transact-SQL (компонент Database Engine)](/sql/t-sql/language-reference)  
  
  
