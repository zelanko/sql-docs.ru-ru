---
title: Редактор задачи «веб-служба» (страница «Вход») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.input.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 93529c88-f540-47f2-a10a-12c87318ed6f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 63b88aa365139c4d22d7a074f2a30e64947158b7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054514"
---
# <a name="web-service-task-editor-input-page"></a>Редактор задачи «Веб-служба» (страница «Вход»)
  Используйте страницу **Вход** в диалоговом окне **Редактор задачи «Веб-служба»** , чтобы указать веб-службу, веб-метод и значения, предоставляемые в качестве входных данных веб-метода. Значения можно предоставить, либо непосредственно введя строки в столбце «Значение», либо выбрав переменные в столбце «Значение».  
  
 Дополнительные сведения об этой задаче см. в разделе [Задача "Веб-служба"](control-flow/web-service-task.md).  
  
## <a name="options"></a>Параметры  
 **Служба**  
 Чтобы выполнить веб-метод, выберите веб-службу из списка.  
  
 **Method**  
 Чтобы выполнить задачу, выберите веб-метод из списка.  
  
 **WebMethodDocumentation**  
 Введите описание веб-метода или нажмите кнопку обзора **(...)**, а затем введите описание в диалоговом окне **Документация веб-метода**.  
  
 **Имя**  
 Перечисляет имена входных данных веб-метода.  
  
 **Type**  
 Перечисляет тип входных данных.  
  
> [!NOTE]  
>  Задача «Веб-служба» поддерживает только параметры следующих типов данных: типы-примитивы, такие как integer и string, массивы и последовательности типов-примитивов, а также перечисления.  
  
 **Переменная**  
 Установите флажки, чтобы использовать переменные для входных данных.  
  
 **Значение**  
 Если установлены флажки «Переменная», выберите переменные из списка для входных данных; в противном случае введите значения входных данных вручную.  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "веб-служба" &#40;страница "Общие"&#41;](general-page-of-integration-services-designers-options.md)   
 [Редактор задачи "веб-служба" &#40;страница "выходные данные"&#41;](../../2014/integration-services/web-service-task-editor-output-page.md)   
 [Страница «Выражения»](expressions/expressions-page.md)  
  
  
