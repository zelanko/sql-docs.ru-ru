---
title: "Проверка модели в режиме DirectQuery | Документы Microsoft"
ms.custom: 
ms.date: 07/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11260792-ff8b-4d0e-b845-ca210dd3fced
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d6f55de10089d304fe5dc5d00c388d007a2241a6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="test-a-model-in-directquery-mode"></a>Тестирование модели в режиме DirectQuery

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Просмотрите параметры тестирования табличной модели в режиме DirectQuery на каждом этапе разработки, начиная с проектирования.  
  
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
  
  
