---
title: Выполнение задач редактор SQL («результирующий набор») | Документы Microsoft
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
- sql12.dts.designer.executesqltask.resultset.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: d27000c8-8d91-4e1c-b45e-bca9a3c12f6d
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b80d8052fd4492e0da04a65aa17e55f3e960d238
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191253"
---
# <a name="execute-sql-task-editor-result-set-page"></a>Редактор задачи «Выполнение SQL» (страница «Результирующий набор»)
  Страница **Результирующий набор** диалогового окна **Редактор задачи «Выполнение SQL»** применяется для сопоставления результатов инструкции SQL с новыми или существующими переменными. Эти параметры в диалоговом окне отключены, если параметр **Результирующий набор** на странице «Общие» установлен в **Нет**.  
  
 Дополнительные сведения об этой задаче см. в разделах [Задача "Выполнение SQL"](control-flow/execute-sql-task.md) и [Результирующие наборы в задаче "Выполнение SQL"](../../2014/integration-services/result-sets-in-the-execute-sql-task.md).  
  
## <a name="options"></a>Параметры  
 **Имя результата**  
 После того как с помощью кнопки **Добавить**было добавлено сопоставление результирующего набора, укажите имя результата. В зависимости от типа результирующего набора необходимо использовать определенные имена результирующих наборов.  
  
 Если тип результирующего набора **Одна строка**, то можно использовать имя столбца, возвращаемого запросом, или число, указывающее положение столбца в списке столбцов, возвращаемых запросом.  
  
 Если результирующий набор имеет тип **Полный результирующий набор** или **XML**, то в качестве имени результирующего набора необходимо использовать 0.  
  
 **См. также:** [Настройка результирующих наборов в задаче "Выполнение SQL"](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)  
  
 **Имя переменной**  
 Для сопоставления результирующего набора с переменной выберите ее или щелкните \<**Создать переменную...**>, чтобы добавить новую переменную с помощью диалогового окна **Добавление переменной**.  
  
 **Добавить**  
 Нажмите кнопку, чтобы добавить сопоставление результирующего набора.  
  
 **Удалить**  
 Выберите в списке сопоставление результирующего набора и нажмите кнопку **Удалить**.  
  
## <a name="see-also"></a>См. также  
 [Об ошибках служб Integration Services и справочник по сообщениям](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Выполнение задач редактор SQL &#40;страница «Общие»&#41;](general-page-of-integration-services-designers-options.md)   
 [Выполнение задач редактор SQL &#40;страница «сопоставление параметров»&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md)   
 [Справочник по Transact-SQL (компонент Database Engine)](/sql/t-sql/language-reference)  
  
  
