---
title: Функциональные возможности сервера ADOMD.NET | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4a8500c06aeb1f8a9aedf6635016b0124d866a3d
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="adomdnet-server-functionality"></a>Функциональные возможности сервера ADOMD.NET
  Все серверные объекты ADOMD.NET предоставляют доступ только для чтения к данным и метаданным на сервере. Чтобы извлечь данные и метаданные, необходимо использовать модель серверных объектов ADOMD.NET, поскольку модель серверных объектов не поддерживает наборы строк схемы.  
  
 Серверные объекты ADOMD.NET можно создавать определяемые пользователем функции (UDF) или хранимую процедуру для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Эти внутрипроцессные методы вызываются при помощи инструкций запроса, создаваемых на таких языках, как MDX, DMX или SQL. Кроме того, эти внутрипроцессные методы обеспечивают дополнительные возможности без задержек, связанных с обменом данными по сети.  
  
> [!NOTE]  
>  Объект <xref:Microsoft.AnalysisServices.AdomdServer.AdomdCommand> поддерживает только расширения интеллектуального анализа данных.  
  
## <a name="what-is-a-udf"></a>Что такое определяемая пользователем функция?  
 Объект *определяемой пользователем функции* — метод, который имеет следующие характеристики:  
  
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
 Объект *хранимой процедуры* — метод, который имеет следующие характеристики:  
  
-   Можно вызвать хранимую процедуру на свои собственные с помощью многомерных Выражений [ВЫЗОВИТЕ](../../mdx/mdx-data-manipulation-call.md) инструкции.  
  
-   Хранимая процедура может принимать любое количество параметров.  
  
-   Хранимая процедура может возвращать dataset, **IDataReader**, или пустой результат.  
  
 В следующем примере используется вымышленная хранимая процедура, `FinalSalesNumbers`:  
  
```  
CALL FinalSalesNumbers()  
```  
  
## <a name="see-also"></a>См. также  
 [Программирование сервера ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  
