---
title: Диалоговое окно «Создание именованного вычисления» (Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsveditor.createnamedcalculation.f1
helpviewer_keywords:
- Named Calculation dialog box
ms.assetid: 66fb30ae-f5c5-4bfc-80ca-8c8a3a9bb30d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a53db9413ce7877182ca5f9c768bb1e1ef71e383
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66086845"
---
# <a name="create-edit-named-calculation-dialog-box-analysis-services"></a>Диалоговое окно «Создание именованного вычисления» (Analysis Services)
  Чтобы определить или изменить именованное вычисление для таблицы [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] в представлении источника данных, используйте диалоговое окно **Создать именованное вычисление/изменение названного вычисления** в. Диалоговое окно **Создание именованного вычисления/Изменение именованного вычисления** можно открыть следующими способами:  
  
-   нажмите кнопку **Создать именованное вычисление** на панели **Панель инструментов****конструктора представлений источников данных**;  
  
-   щелкните правой кнопкой мыши таблицу на панели **Таблицы** или **Диаграмма****конструктора представлений источников данных** и выберите команду **Создать именованное вычисление**;  
  
-   щелкните правой кнопкой мыши именованное вычисление на панели **Диаграмма****конструктора представлений источников данных** и выберите команду **Изменить именованное вычисление**.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Analysis Services конструкторов и диалоговых окон &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Конструктор представлений источников данных &#40;Analysis Services многомерных данных&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
