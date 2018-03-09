---
title: "Проверка модели в режиме DirectQuery | Документы Microsoft"
ms.custom: 
ms.date: 07/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11260792-ff8b-4d0e-b845-ca210dd3fced
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ad389541ba4bb964df0c3a0ca7cb08277d1bd1d9
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="test-a-model-in-directquery-mode"></a>Тестирование модели в режиме DirectQuery
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Просмотрите параметры тестирования табличной модели в режиме DirectQuery на каждом этапе разработки, начиная с разработки.  
  
## <a name="test-in-excel"></a>Тестирование в Excel 
  
 При разработке модели в службах SSDT можно использовать функцию **Анализ в Excel** , которая позволяет тестировать решения моделирования на основе демонстрационных данных в памяти или реляционной базы данных.  При выборе функции "Анализ в Excel" открывается диалоговое окно, где можно задать параметры.
 
 ![Анализ в Excel: параметры DirectQuery](../../analysis-services/tabular-models/media/analyze-in-excel-directquery-options.png)
 
 Если в модели включен режим DirectQuery, можно задать режим подключения DirectQuery с двумя доступными параметрами:
 - **Представление демонстрационных данных** : при выборе этого параметра все запросы из Excel направляются в примеры секций, содержащие набор демонстрационных данных в памяти. Это параметр полезен, если нужно убедиться в том, что формулы DAX в измерениях, вычисляемые столбцы или защита на уровне строк работают правильно.
 
 - **Полное представление данных** : при выборе этого параметра все запросы из Excel отправляются в службы Analysis Services, а затем в реляционную базу данных. Фактически этот параметр включает полностью функционирующий режим DirecQuery.
 
 ### <a name="other-clients"></a>Другие клиенты
 При использовании функции "Анализ в Excel" создается ODC-файл подключения. Из этого файла можно взять данные строки подключения и использовать их для подключения к модели из других клиентских приложений. Для того чтобы клиент подключался к секциям демонстрационных данных, добавляется еще один параметр — DataView=Sample.  
  
## <a name="monitor-query-execution-on-backend-systems-using-xevents-or-sql-profiler"></a>Мониторинг выполнения запросов в серверных системах с помощью xEvents или SQL Profiler 
 Запустите трассировку сеанса, подключенную к реляционной базе данных SQL Server, для мониторинга подключений, поступающих от табличной модели:  
  
-   [Мониторинг служб Analysis Services с помощью расширенных событий SQL Server](../../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)  
  
-   [Использование приложения SQL Server Profiler для мониторинга служб Analysis Services](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)  
  
 При использовании Oracle или Teradata применяйте для этих систем средства мониторинга трассировки.  
  
  
