---
title: Замена параметров шаблона | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.templates.replaceparameters.f1
helpviewer_keywords:
- template parameters [Template Explorer]
- templates [Transact-SQL], replacing parameters
- Replace (Query) Template Parameters dialog box
- replacing template parameters
ms.assetid: 1234aa14-3464-4a3e-922a-5cfb8fb23627
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 620569275c85bc12f678f64c927956d57452792f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47722504"
---
# <a name="replace-template-parameters"></a>Замена параметров шаблона
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Шаблоны содержат параметры, которым можно присваивать требуемые значения для каждой конкретной реализации при каждом использовании данного шаблона. После открытия шаблона в редакторе кода можно заменить параметры значениями, которые требуются в данной реализации.  
  
## <a name="before-you-begin"></a>Перед началом  
Диалоговое окно **Задание значений для параметров шаблона** представляет собой сетку с тремя столбцами. Столбцы **Параметр** и **Тип** доступны только для чтения и не могут быть изменены. Просмотрите содержимое столбца **Значение** и замените любое из значений по умолчанию значением, требуемым для данной реализации.  
  
Чтобы использовать это диалоговое окно, необходимо заключить параметры в скрипте в угловые скобки (`< >`) в формате `<`*имя_параметра*`,` *тип_данных*`,` *значение_по_умолчанию*`>`.  
  
## <a name="replace-template-parameters"></a>Замена параметров шаблона  
После открытия шаблона в окне редактора кода выполните следующие действия.  
  
1.  В меню **Запрос** выберите пункт **Указать значения для параметров шаблона**.  
  
2.  В диалоговом окне **Задание значений для параметров шаблона** в столбце **Значения** содержится предлагаемое значение параметра. Примите значение или замените его новым значением.  
  
3.  Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **Замена параметров шаблона** , и отредактируйте скрипт в редакторе запросов.  
  
## <a name="see-also"></a>См. также:  
[Template Explorer](../../ssms/template/template-explorer.md)  
[Открытие шаблона](../../ssms/template/open-a-template.md)  
  
