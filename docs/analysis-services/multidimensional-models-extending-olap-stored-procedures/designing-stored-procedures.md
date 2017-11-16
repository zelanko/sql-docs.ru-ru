---
title: "Проектирование хранимых процедур | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- stored procedures [Analysis Services], designing
- dependent assemblies [Analysis Services]
- assemblies [Analysis Services]
ms.assetid: af4e7bd5-041b-4a40-9942-0ef6a3af46c6
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7ce4810cec6ebfe861150aa24fea322682dc0e8c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="designing-stored-procedures"></a>Конструирование хранимых процедур
  В хранимых процедурах доступны как административная объектная модель объектов AMO, так и ориентированная на клиентов объектная модель объектов [!INCLUDE[msCoName](../../includes/msconame-md.md)] ADO Multidimensional.  
  
 Для возможности вызова хранимые процедуры должны быть в области (сервер или база данных), видимой на уровне многомерных выражений. Однако после вызова хранимой процедуры ее область не ограничивается действиями под своим родителем. Хранимая процедура может вносить изменения или правки в любом месте сервера при условии соблюдения ограничений безопасности, налагаемых вызывающим пользовательским процессом, или ограничений транзакции, в составе которой такая процедура функционирует.  
  
 Процедуры серверной области доступны во всех контекстах на сервере. Хранимые процедуры области базы данных видимы только в контексте базы данных, в которой они определены.  
  
 Как и любая другая функция многомерных выражений, хранимая процедура должна быть разрешена до продолжения сеанса многомерных выражений. Во время выполнения хранимые процедуры блокируют сеансы многомерных выражений. Если не существует конкретной причины для остановки сеанса многомерных выражений в ожидании пользовательского взаимодействия, то пользовательские взаимодействия (например, диалоговые окна) не рекомендуются.   
  
## <a name="dependent-assemblies"></a>Зависимые сборки  
 Все зависимые сборки должны быть загружены в экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], чтобы их обнаружила среда CLR. Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] хранят зависимые сборки в папке главной сборки, так что среда CLR автоматически разрешает все ссылки на функции в этих сборках.  
  
## <a name="see-also"></a>См. также:  
 [Управление сборками многомерной модели](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Определение хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  

