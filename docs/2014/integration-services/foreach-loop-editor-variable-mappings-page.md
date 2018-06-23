---
title: Редактор циклов по каждому элементу (страница «сопоставления переменных») | Документы Microsoft
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.mapping.f1
ms.assetid: aa847b87-f391-48a5-9849-eeda2d6b00b9
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b38583d5fe07315f6f80a54a188312f3becb3e28
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188027"
---
# <a name="foreach-loop-editor-variable-mappings-page"></a>Редактор циклов по каждому элементу (страница «Сопоставления переменных»)
  Страница **Сопоставления переменных** диалогового окна **Редактор циклов по каждому элементу** используется для сопоставления переменных со значениями коллекции. Значение переменной обновляется значениями из коллекции при каждом повторе цикла.  
  
 Сведения об использовании контейнера «цикл по каждому элементу» в пакете служб Integration Services см. в разделе [Foreach Loop Container](control-flow/foreach-loop-container.md) . Сведения о его настройке см. в разделе [Настройка контейнера "цикл по каждому элементу"](../../2014/integration-services/configure-a-foreach-loop-container.md).  
  
 Учебник по службам [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] «Создание простого учебного пакета ETL» содержит занятие, посвященное добавлению и настройке «цикла по каждому элементу».  
  
## <a name="options"></a>Параметры  
 **Переменная**  
 Выберите существующую переменную или щелкните \<**Создать переменную...**>, чтобы создать ее.  
  
> [!NOTE]  
>  После установки сопоставления переменной новая строка автоматически добавится к списку **Переменная**.  
  
 **См. также:** [Переменные в службах Integration Services (SSIS)](integration-services-ssis-variables.md), [Добавление переменной](../../2014/integration-services/add-variable.md)  
  
 **Index**  
 При использовании перечислителя по каждому элементу задайте индекс столбца в значении коллекции, чтобы установить сопоставление переменных. Для других типов перечислителей индекс доступен только для чтения.  
  
> [!NOTE]  
>  Индекс отсчитывается от 0.  
  
 **См. также:** [Просмотр файлов и таблиц Excel с помощью контейнера "цикл по каждому элементу"](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
 **Удаление**  
 Выберите переменную и нажмите кнопку **Удалить**.  
  
## <a name="see-also"></a>См. также  
 [Об ошибках служб Integration Services и справочник по сообщениям](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор циклов по каждому элементу &#40;страница «Общие»&#41;](general-page-of-integration-services-designers-options.md)   
 [Редактор циклов по каждому элементу &#40;страница «Коллекция»&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md)   
 [Страница «выражения»](expressions/expressions-page.md)   
 [Контейнер «цикл по элементам»](control-flow/for-loop-container.md)  
  
  