---
title: Мониторинг экземпляра служб Analysis Services Обзор | Документация Майкрософт
ms.date: 11/16/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 39cc5a22165d07aafce29e4216548c4e8d226892
ms.sourcegitcommit: b51edbe07a0a2fdb5f74b5874771042400baf919
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087633"
---
# <a name="monitoring-overview"></a>Общие сведения о мониторинге
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

Службы Analysis Services имеет несколько различных средств для отслеживания и настройки производительности ваших серверов. Выбор средств зависит от типа контроля или настройки, а также от конкретных отслеживаемых событий.

Дополнительные сведения о мониторинге SQL Server Analysis Services, см. в разделе [руководстве SQL Server 2008 R2](http://go.microsoft.com/fwlink/?LinkID=225539).  
  
## <a name="monitoring-tools"></a>Средства мониторинга  

|Инструмент  |Описание  |
|---------|---------|
|[Приложение SQL Server Profiler](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)      |   Отслеживает события процесса ядра. Эта команда также запишет данные об этих событиях, позволяя отслеживать работу сервера и базы данных.      |
| [Расширенные события](../../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)     |   Упрощенная трассировки и производительности, мониторинг системы, которая использует очень небольшое количество системных ресурсов, что делает его идеальным средством для диагностики проблем на рабочего и тестового серверов.       |
| [Динамические административные представления &#40;динамических административных представлений&#41;](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)      |   Запросы, которые возвращают сведения о модели объектов, серверных операций и работоспособности сервера. Запрос, на основе SQL, представляет собой интерфейс для наборов строк схемы.      |
| [События трассировки](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)     |  За активностью экземпляра путем отслеживания и анализа событий трассировки, формируемых экземпляром. События трассировки сгруппированы для облегчения поиска связанных событий трассировки.        |
|   [Счетчики производительности](../../analysis-services/instances/performance-counters-ssas.md)\*    |    С помощью системного монитора можно контролировать производительность экземпляра служб Microsoft SQL Server Analysis Services (SSAS) посредством счетчиков производительности.     |
|[Журнал операций](../../analysis-services/instances/performance-counters-ssas.md)\*|Экземпляр SQL Server Analysis Services, регистрируются уведомлений от сервера, ошибки и предупреждения в файл msmdsrv.log — по одному для каждого устанавливаемого экземпляра. |

\* Применяется к SQL Server Analysis Services только.

## <a name="see-also"></a>См. также

[Мониторинг метрик сервера служб Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-monitor)   
[Настройка журнала ведения диагностики для Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-logging)
