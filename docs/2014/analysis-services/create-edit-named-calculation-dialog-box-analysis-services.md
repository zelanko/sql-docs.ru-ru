---
title: Создание Изменение с именем диалоговое окно «вычисления» (службы Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsveditor.createnamedcalculation.f1
helpviewer_keywords:
- Named Calculation dialog box
ms.assetid: 66fb30ae-f5c5-4bfc-80ca-8c8a3a9bb30d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 31c0444930e15d933d75dd72554c3232871cd59e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62679941"
---
# <a name="create-edit-named-calculation-dialog-box-analysis-services"></a>Создание Изменение диалоговое окно «именованное вычисление» (службы Analysis Services)
  Используйте диалоговое окно **Создание именованного вычисления/Изменение именованного вычисления** в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] для определения или редактирования именованного вычисления для таблицы в представлении источника данных. You can display the **Create/Edit Named Calculation** dialog box by:  
  
-   нажмите кнопку **Создать именованное вычисление** на панели **Панель инструментов** **конструктора представлений источников данных**;  
  
-   щелкните правой кнопкой мыши таблицу на панели **Таблицы** или **Диаграмма** **конструктора представлений источников данных** и выберите команду **Создать именованное вычисление**;  
  
-   щелкните правой кнопкой мыши именованное вычисление на панели **Диаграмма** **конструктора представлений источников данных** и выберите команду **Изменить именованное вычисление**.  
  
## <a name="options"></a>Параметры  
 **Имя столбца**  
 Введите имя именованного вычисления.  
  
 **Описание**  
 Введите необязательное описание именованного вычисления.  
  
 **Выражение**  
 Введите допустимое выражение SQL, возвращающее скалярное значение. The expression is sent to the provider, and validated in the following expression:  
  
```  
SELECT <Table Name in Data Source>.* , <Expression> AS <Column Name> FROM <Table Name in Data Source>AS <Table Name in Data Source View>  
```  
  
 The expression can contain references to other tables, by means of a sub-select statement. If the expression would require parentheses in a SELECT statement, the expression entered must be enclosed between parentheses.  
  
## <a name="see-also"></a>См. также  
 [Конструкторы и диалоговые окна служб Analysis Services &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Конструктор представлений источников данных (службы Analysis Services — многомерные данные)](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
