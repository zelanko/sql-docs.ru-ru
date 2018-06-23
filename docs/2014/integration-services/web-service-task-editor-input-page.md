---
title: Редактор задач веб-служб (страница «Вход») | Документы Microsoft
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
- sql12.dts.designer.webservicestask.input.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 93529c88-f540-47f2-a10a-12c87318ed6f
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 8f458f4a2898915102ab2a05b04fb7ba223c5e30
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191235"
---
# <a name="web-service-task-editor-input-page"></a>Редактор задачи «Веб-служба» (страница «Вход»)
  Используйте страницу **Вход** в диалоговом окне **Редактор задачи «Веб-служба»** , чтобы указать веб-службу, веб-метод и значения, предоставляемые в качестве входных данных веб-метода. Значения можно предоставить, либо непосредственно введя строки в столбце «Значение», либо выбрав переменные в столбце «Значение».  
  
 Дополнительные сведения об этой задаче см. в разделе [Задача "Веб-служба"](control-flow/web-service-task.md).  
  
## <a name="options"></a>Параметры  
 **Служба**  
 Чтобы выполнить веб-метод, выберите веб-службу из списка.  
  
 **Метод**  
 Чтобы выполнить задачу, выберите веб-метод из списка.  
  
 **WebMethodDocumentation**  
 Введите описание веб-метода или нажмите кнопку обзора **(…)** , а затем введите описание в диалоговом окне **Документация веб-метода** .  
  
 **Название**  
 Перечисляет имена входных данных веб-метода.  
  
 **Тип**  
 Перечисляет тип входных данных.  
  
> [!NOTE]  
>  Задача «Веб-служба» поддерживает только параметры следующих типов данных: типы-примитивы, такие как integer и string, массивы и последовательности типов-примитивов, а также перечисления.  
  
 **Переменная**  
 Установите флажки, чтобы использовать переменные для входных данных.  
  
 **Value**  
 Если установлены флажки «Переменная», выберите переменные из списка для входных данных; в противном случае введите значения входных данных вручную.  
  
## <a name="see-also"></a>См. также  
 [Об ошибках служб Integration Services и справочник по сообщениям](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задач веб-служба &#40;страница «Общие»&#41;](general-page-of-integration-services-designers-options.md)   
 [Редактор задач веб-служба &#40;вывода страниц&#41;](../../2014/integration-services/web-service-task-editor-output-page.md)   
 [Страница "Выражения"](expressions/expressions-page.md)  
  
  