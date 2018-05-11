---
title: Объект модели (TMSL) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ec39669a28480a1b255c7f596395392a650fe859
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="model-object-tmsl"></a>Объект модели (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет табличной модели. Имеется одна модель на базу данных и только одну базу данных, которые могут быть указаны в командам. Объект базы данных является родительским объектом.  
  
 Определения модели слишком велики для воспроизведения полный синтаксис в один раздел. По этой причине частичного выделения основных частей синтаксиса находятся ниже со ссылками на дочерние объекты.  
  
 Возможно, лучшим способом узнать определения модели — начать с табличной модели, хорошо известны. Используйте **Просмотр кода** параметр в SQL Server Data Tools, чтобы просмотреть его определение. Не забудьте установить редактор JSON, чтобы можно было просмотреть код. В Visual Studio, можно получить редактор JSON [загрузка Community edition](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) или другой выпуск Visual Studio.  
  
> [!NOTE]  
>  В любом сценарии можно ссылаться только одна база данных во время. Для любого объекта, отличные от самой базы данных свойства базы данных необязателен, если указать модель. Имеется взаимно-однозначное сопоставление между моделью и базы данных, которая может использоваться для определения имени базы данных, если явно не указано.   
> Аналогичным образом вы можете оставить модель, задавая ее свойства в базе данных.  
  
## <a name="object-definition"></a>Определение объекта  
 Все объекты имеют общий набор свойств, включая имя, тип, описание, коллекцию свойств и заметки. **Модель** объекты также имеют следующие свойства.  
  
 storageLocation  
 Место на диске, где размещается модель.  
  
 defaultMode  
 Метод по умолчанию для предоставления доступа к данным в секции.  
  
 defaultDataView  
 Для моделей в режиме DirectQuery это свойство определяет, какие разделы используются для выполнения запросов к модели.  Допустимые значения: Full и образец.  
  
 культура  
 Язык и региональные параметры для форматирования.  
  
 collation  
 Последовательность параметров сортировки. В разделе [сценарии глобализации для служб Analysis Services](../../analysis-services/globalization-scenarios-for-analysis-services.md) для получения дополнительной информации.  
  
 таблицы  
 Полная коллекция таблиц в модели, включая секции, столбцы, меры, ключевые показатели эффективности и заметки. В разделе [объект Tables &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md) подробные сведения.  
  
 связи  
 Определяет связь между каждой парой таблиц, включая свойства, настройки безопасности и направление фильтрации. В разделе [связи объекта &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md) подробные сведения.  
  
 Источники данных  
 Одно или несколько подключений к внешним базам данных, предоставляющего данные для модели или для передачи с помощью запросов. В разделе [объектов источников данных &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md) подробные сведения.  
  
 роли  
 Объекты, которые связать разрешений на базу данных, учетные записи и при необходимости фильтры безопасности в DAX для пользовательское управление доступом.  
  
## <a name="usage"></a>Использование  
 **Модель** объекты содержат всю модель. Необходимо указать большинство команд в одной модели или его родительский объект базы данных.  
  
 При создании, замена или изменение объекта модели укажите все свойства чтения и записи определения объекта. Пропуск свойства чтения и записи, считается удаления.  
  
## <a name="partial-syntax"></a>Частичное синтаксис  
 Так как это определение объектов велико, перечислены только первого уровня свойства. В разделе [определений объектов в языке скриптов табличных моделей &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/tmsl-reference-tabular-objects.md) список дочерних объектов.  
  
```  
    "model": {  
      "description": "Model object of a Tabular database",  
      "type": "object",  
      "properties": {  
          "name": {  },  
          "description": {  },  
         "storageLocation": {  },  
         "defaultMode":  {  },  
         "defaultDataView": {  },  
         "culture": {  },  
         "collation": {  },  
         "annotations": {  },  
         "tables": {  },  
         "relationships": {  },  
         "dataSources": {  },  
         "perspectives": {  },  
            "cultures": {  },  
         "roles": {  }  
    }  
  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Уровень совместимости табличных моделей в службах Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
