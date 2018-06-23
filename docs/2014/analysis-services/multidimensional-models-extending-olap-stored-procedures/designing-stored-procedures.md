---
title: Проектирование хранимых процедур | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services], designing
- dependent assemblies [Analysis Services]
- assemblies [Analysis Services]
ms.assetid: af4e7bd5-041b-4a40-9942-0ef6a3af46c6
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 245d02d18fdaf9fdce5d1b63b965525642bebcc4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096950"
---
# <a name="designing-stored-procedures"></a>Конструирование хранимых процедур
  В хранимых процедурах доступны как административная объектная модель объектов AMO, так и ориентированная на клиентов объектная модель объектов [!INCLUDE[msCoName](../../includes/msconame-md.md)] ADO Multidimensional.  
  
 Для возможности вызова хранимые процедуры должны быть в области (сервер или база данных), видимой на уровне многомерных выражений. Однако после вызова хранимой процедуры ее область не ограничивается действиями под своим родителем. Хранимая процедура может вносить изменения или правки в любом месте сервера при условии соблюдения ограничений безопасности, налагаемых вызывающим пользовательским процессом, или ограничений транзакции, в составе которой такая процедура функционирует.  
  
 Процедуры серверной области доступны во всех контекстах на сервере. Хранимые процедуры области базы данных видимы только в контексте базы данных, в которой они определены.  
  
 Как и любая другая функция многомерных выражений, хранимая процедура должна быть разрешена до продолжения сеанса многомерных выражений. Во время выполнения хранимые процедуры блокируют сеансы многомерных выражений. Если не существует конкретной причины для остановки сеанса многомерных выражений в ожидании пользовательского взаимодействия, то пользовательские взаимодействия (например, диалоговые окна) не рекомендуются.   
  
## <a name="dependent-assemblies"></a>Зависимые сборки  
 Все зависимые сборки должны быть загружены в экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], чтобы их обнаружила среда CLR. Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] хранят зависимые сборки в папке главной сборки, так что среда CLR автоматически разрешает все ссылки на функции в этих сборках.  
  
## <a name="see-also"></a>См. также  
 [Управление сборками многомерной модели](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Определение хранимых процедур](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  