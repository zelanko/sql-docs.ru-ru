---
title: Программирование табличных моделей | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0ceb461e-12c1-44ea-97ac-b99bf308676b
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 785e4818d635d41dc27eea8fc63b62cf63e0ff92
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190530"
---
# <a name="tabular-model-programming"></a>Программирование табличных моделей
  В табличных моделях реляционные конструкции служат для моделирования данных служб Analysis Services, которые используются в аналитических приложениях и отчетах. Эти модели работают в экземпляре служб Analysis Services, настроенном для табличного режима, с использованием модуля аналитики в памяти для хранения и быстрого просмотра таблиц, при применении которого выполняется статистическая обработка и вычисление данных по запросу.  
  
 С программной точки зрения объекты, с которыми пользователь работает в объектах AMO, ADOMD.NET, XMLA и OLE DB, принципиально одинаковы для табличных и многомерных решений. Если требованиям пользовательского решения для бизнес-аналитики лучше всего отвечает табличный шаблон базы данных, то для интеграции приложения с табличными моделями в экземпляре служб Analysis Services можно использовать любые клиентские библиотеки и интерфейсы программирования служб Analysis Services. Для запроса к данным табличной модели и вычисления таких данных можно использовать в коде внедренные многомерные выражения или DAX.  
  
 В этом разделе приведены дополнительные сведения о том, как программным образом работать с сущностями табличной модели и их свойствами.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Заметки языка CSDL для бизнес-аналитики &#40;CSDLBI&#41;](csdl-annotations-for-business-intelligence-csdlbi.md)  
  
 [Основные сведения о табличной объектной модели](representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
 [Технический справочник по аннотациям бизнес-аналитики для языка CSDL](conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
 [Интерфейс IMDEmbedded](imdembeddeddata-interface.md)  
  
## <a name="see-also"></a>См. также  
 [Табличное моделирование &#40;табличные службы SSAS&#41;](../tabular-models/tabular-models-ssas.md)   
 [Конструктор табличных моделей &#40;табличные службы SSAS&#41;](../tabular-model-designer-ssas-tabular.md)  
  
  