---
title: Редактор циклов по каждому элементу (страница «сопоставления переменных») | Документация Майкрософт
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.mapping.f1
ms.assetid: aa847b87-f391-48a5-9849-eeda2d6b00b9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 03488e4cfd3a0cc905a58166f381f68eb3292c49
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66058525"
---
# <a name="foreach-loop-editor-variable-mappings-page"></a>Редактор циклов по каждому элементу (страница «Сопоставления переменных»)
  Страница **Сопоставления переменных** диалогового окна **Редактор циклов по каждому элементу** используется для сопоставления переменных со значениями коллекции. Значение переменной обновляется значениями из коллекции при каждом повторе цикла.  
  
 Сведения об использовании контейнера «цикл по каждому элементу» в пакете служб Integration Services см. в разделе [Foreach Loop Container](control-flow/foreach-loop-container.md) . Сведения о его настройке см. в разделе [Настройка контейнера "цикл по каждому элементу"](../../2014/integration-services/configure-a-foreach-loop-container.md).  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] созданию простого пакета ETL содержит урок, позволяющий добавить и настроить цикл [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] foreach.  
  
## <a name="options"></a>Параметры  
 **Переменная**  
 Выберите существующую переменную или нажмите кнопку \< **создать переменную...**>, чтобы создать новую переменную.  
  
> [!NOTE]  
>   После установки сопоставления переменной новая строка автоматически добавится к списку **Переменная** .  
  
 **См. также**: [Integration Services &#40;переменные&#41; SSIS](integration-services-ssis-variables.md), [Добавить переменную](../../2014/integration-services/add-variable.md)  
  
 **Индекс**  
 При использовании перечислителя по каждому элементу задайте индекс столбца в значении коллекции, чтобы установить сопоставление переменных. Для других типов перечислителей индекс доступен только для чтения.  
  
> [!NOTE]  
>  Индекс отсчитывается от 0.  
  
 **См. также:**[Просмотр файлов и таблиц Excel с помощью контейнера "цикл по каждому элементу"](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
 **Удаление**  
 Выберите переменную и нажмите кнопку **Удалить**.  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор циклов по каждому элементу &#40;страница "Общие"&#41;](general-page-of-integration-services-designers-options.md)   
 [Редактор циклов по каждому элементу &#40;страница коллекции&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md)   
 [Страница "выражения"](expressions/expressions-page.md)   
 [Контейнер «цикл по элементам»](control-flow/for-loop-container.md)  
  
  
