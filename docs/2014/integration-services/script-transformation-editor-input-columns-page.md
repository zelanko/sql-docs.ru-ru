---
title: Редактор преобразования скриптов (страница "входные столбцы") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.inputcolumn.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: d6e4ce84-3335-48e6-82d3-1c359ed87f63
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b71f12c9f36f74799c47538b30a058b529fdfa6d
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58391712"
---
# <a name="script-transformation-editor-input-columns-page"></a>Редактор преобразования «Скрипт» (страница «Входные столбцы»)
  Страница **Входные столбцы** диалогового окна **Редактор преобразования «Скрипт»** используется для установки свойств входных столбцов.  
  
> [!NOTE]  
>  Страница **Входные столбцы** не отображается для компонентов источника, которые имеют выводы, но не имеют входов.  
  
 Дополнительные сведения о компоненте скрипта см. в разделе [компонента скрипта](data-flow/transformations/script-component.md) и [Настройка компонента скрипта в редакторе компонента скрипта](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md). Дополнительные сведения о программировании компонента скрипта, см. в разделе [расширение потока данных в компоненте скрипта](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
## <a name="options"></a>Параметры  
 **Имя входа**  
 Выберите из списка доступных входов.  
  
 **Доступные входные столбцы**  
 С помощью флажков укажите столбцы, которые будут использоваться в преобразовании «Скрипт».  
  
 **Входной столбец**  
 Выберите для каждой строки столбец из списка доступных входных столбцов. Выбранные столбцы обозначаются флажками в таблице **Доступные входные столбцы**.  
  
 **Псевдоним вывода**  
 Введите псевдоним для каждого выходного столбца. По умолчанию, используется имя входного столбца, однако можно выбрать любое уникальное описательное имя.  
  
 **Тип применения**  
 Указывает, будет ли преобразование «Скрипт» рассматривать каждый столбец как `ReadOnly` или `ReadWrite`.  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Выбор типа компонента скрипта](../../2014/integration-services/select-script-component-type.md)   
 [Редактор преобразования "Скрипт" (страница "Входы и выходы")](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md)   
 [Редактор преобразования "Скрипт" (страница "Скрипт")](../../2014/integration-services/script-transformation-editor-script-page.md)   
 [Редактор преобразования "Скрипт" (страница "Диспетчеры соединений")](../../2014/integration-services/script-transformation-editor-connection-managers-page.md)   
 [Дополнительные примеры компонента скрипта](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
