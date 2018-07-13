---
title: Замена параметров шаблона | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.templates.replaceparameters.f1
helpviewer_keywords:
- template parameters [Template Explorer]
- templates [Transact-SQL], replacing parameters
- Replace (Query) Template Parameters dialog box
- replacing template parameters
ms.assetid: 1234aa14-3464-4a3e-922a-5cfb8fb23627
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2adca9bc75cbe15055cc7500569e72b0344cb6be
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37204614"
---
# <a name="replace-template-parameters"></a>Замена параметров шаблона
  Шаблоны содержат параметры, которым можно присваивать требуемые значения для каждой конкретной реализации при каждом использовании данного шаблона. После открытия шаблона в редакторе кода можно заменить параметры значениями, которые требуются в данной реализации.  
  
## <a name="before-you-begin"></a>Перед началом  
 Диалоговое окно **Задание значений для параметров шаблона** представляет собой сетку с тремя столбцами. Столбцы **Параметр** и **Тип** доступны только для чтения и не могут быть изменены. Просмотрите содержимое столбца **Значение** и замените любое из значений по умолчанию значением, требуемым для данной реализации.  
  
 Чтобы использовать это диалоговое окно, необходимо заключить параметры в скрипте в угловые скобки (`< >`) в формате `<`*имя_параметра*`,` *тип_данных*`,` *значение_по_умолчанию*`>`.  
  
## <a name="replace-template-parameters"></a>Замена параметров шаблона  
 После открытия шаблона в окне редактора кода выполните следующие действия.  
  
1.  В меню **Запрос** выберите пункт **Указать значения для параметров шаблона**.  
  
2.  В диалоговом окне **Задание значений для параметров шаблона** в столбце **Значения** содержится предлагаемое значение параметра. Примите значение или замените его новым значением.  
  
3.  Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **Замена параметров шаблона** , и отредактируйте скрипт в редакторе запросов.  
  
## <a name="see-also"></a>См. также  
 [Обозреватель шаблонов](template-explorer.md)   
 [Открытие шаблона](open-a-template.md)  
  
  
