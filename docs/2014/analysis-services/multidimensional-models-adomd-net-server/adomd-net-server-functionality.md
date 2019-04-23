---
title: Функциональные возможности сервера ADOMD.NET | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- functionality [ADOMD.NET]
- ADOMD.NET, functionality
ms.assetid: b74c6957-3f64-4e09-aa09-d06ee93f82fa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cc127a8bafc9ad2f53465caeca013d5033e5c396
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60154380"
---
# <a name="adomdnet-server-functionality"></a>Функциональные возможности сервера ADOMD.NET
  Все серверные объекты ADOMD.NET предоставляют доступ только для чтения к данным и метаданным на сервере. Чтобы извлечь данные и метаданные, необходимо использовать модель серверных объектов ADOMD.NET, поскольку модель серверных объектов не поддерживает наборы строк схемы.  
  
 Серверные объекты ADOMD.NET, можно создать определяемую пользователем функцию (UDF) или хранимую процедуру для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Эти внутрипроцессные методы вызываются при помощи инструкций запроса, создаваемых на таких языках, как MDX, DMX или SQL. Кроме того, эти внутрипроцессные методы обеспечивают дополнительные возможности без задержек, связанных с обменом данными по сети.  
  
> [!NOTE]  
>  Объект <xref:Microsoft.AnalysisServices.AdomdServer.AdomdCommand> поддерживает только расширения интеллектуального анализа данных.  
  
## <a name="what-is-a-udf"></a>Что такое определяемая пользователем функция?  
 Объект *определяемой пользователем функции* — это метод, который имеет следующие характеристики:  
  
-   Определяемую пользователем функцию можно вызывать в контексте запроса.  
  
-   Определяемая пользователем функция может принимать любое количество параметров.  
  
-   Определяемая пользователем функция может возвращать различные типы данных.  
  
 Следующий пример иллюстрирует применение вымышленной определяемой пользователем функции, `FinalSalesNumber`.  
  
```  
SELECT SalesPerson.Name ON ROWS,  
       FinalSalesNumber() ON COLUMNS  
FROM SalesModel  
```  
  
## <a name="what-is-a-stored-procedure"></a>Что такое хранимая процедура?  
 Объект *хранимой процедуры* — это метод, который имеет следующие характеристики:  
  
-   Можно вызвать хранимую процедуру на свой собственный с помощью многомерных Выражений [ВЫЗОВИТЕ](/sql/mdx/mdx-data-manipulation-call) инструкции.  
  
-   Хранимая процедура может принимать любое количество параметров.  
  
-   Хранимая процедура может возвращать набор данных, модуль `IDataReader` или пустой результат.  
  
 В следующем примере используется вымышленная хранимая процедура, `FinalSalesNumbers`:  
  
```  
CALL FinalSalesNumbers()  
```  
  
## <a name="see-also"></a>См. также  
 [Программирование сервера ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
  
