---
title: Редактор задач веб-служба (страница «Вход») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.input.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 93529c88-f540-47f2-a10a-12c87318ed6f
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7eec6368855b52088d5ed5ff253ec6020286aadf
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52515149"
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
 Введите описание веб-метода или нажмите кнопку обзора **(...)**, а затем введите описание в диалоговом окне **Документация веб-метода**.  
  
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
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "Веб-служба" (страница "Общие")](general-page-of-integration-services-designers-options.md)   
 [Редактор задачи "Веб-служба" (страница "Вывод")](../../2014/integration-services/web-service-task-editor-output-page.md)   
 [Страница «Выражения»](expressions/expressions-page.md)  
  
  
