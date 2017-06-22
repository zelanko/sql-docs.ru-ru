---
title: "Настройка базы данных с помощью рабочей нагрузки из хранилища запросов | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Database Engine Tuning Advisor, Query Store
ms.assetid: 17107549-5073-4fa2-8ee7-5ed33b38821e
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7f89ed5e87b8fd51e8618a8559679225d91b32de
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="tuning-database-using-workload-from-query-store"></a>Настройка базы данных с помощью рабочей нагрузки из хранилища запросов
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]


Компонент [Хранилище запросов](../../relational-databases/performance/how-query-store-collects-data.md) в SQL Server автоматически записывает журнал запросов, планы и статистику выполнения и сохраняет их в базе данных. [Помощник по настройке ядра СУБД (DTA)](../../relational-databases/performance/database-engine-tuning-advisor.md) теперь позволяет использовать хранилище запросов, чтобы автоматически выбирать соответствующую рабочую нагрузку для настройки. Для многих пользователей это может устранить необходимость явно собирать рабочую нагрузку для настройки. Эта функция доступна только в том случае, если в базе данных включен компонент хранилища запросов. 
  
  Она доступна в среде SQL Server Management Studio версии **16.4** или более поздней. 
  
<a name="how-to-tune-a-workload-from-query-store-in-database-engine-tuning-advisor-gui"></a>Как настроить рабочую нагрузку из хранилища запросов в графическом пользовательском интерфейсе помощника по настройке ядра СУБД
---
Чтобы включить эту функцию, в графическом интерфейсе помощника по настройке ядра СУБД установите переключатель **Хранилище запросов** на панели **Общие** (см. ниже).
![Рабочая нагрузка помощника по настройке ядра СУБД из хранилища запросов](../../relational-databases/performance/media/dta-workload-from-query-store.gif)
 
<a name="how-to-tune-a-workload-from-query-store-in-dtaexe-command-line-utility"></a>Как настроить рабочую нагрузку из хранилища запросов в программе командной строки dta.exe
---
В командной строке (dta.exe) выберите параметр **-iq**, чтобы использовать рабочую нагрузку из хранилища запросов. 

В командной строке, позволяющей настраивать поведение DTA при выборе рабочей нагрузки из хранилища запросов, можно использовать два дополнительных параметра. Эти параметры недоступны в графическом пользовательском интерфейсе.
  1. Number of workload events to tune (Число настраиваемых событий рабочей нагрузки). Этот параметр задается с помощью аргумента командной строки **-n**. Он позволяет управлять количеством настраиваемых событий из хранилища запросов. По умолчанию для этого параметра DTA использует значение 1000. Обратите внимание, что DTA всегда выбирает самые ресурсоемкие события по общей продолжительности. 
  
  2. Time windows of events to tune (Временные окна настраиваемых событий). Так как хранилище запросов может содержать запросы, выполненные очень давно, этот параметр позволяет пользователю указать прошедшее временное окно (в часах) для запросов, которые будет настраивать DTA. Этот параметр задается с помощью аргумента командной строки **-I**. 

Дополнительные сведения см. в статье о [служебной программе dta](../../tools/dta/dta-utility.md).

<a name="difference-between-using-workload-from-query-store-and-plan-cache"></a>Различия в использовании рабочей нагрузки из хранилища запросов и кэша планов 
--- 
Разница между параметрами хранилища запросов и кэша планов состоит в том, что первый содержит более длинный журнал запросов, выполненных в базе данных, которые сохранялись при перезапуске сервера. Кэш планов, в свою очередь, содержит только подмножество недавно выполненных запросов, планы которых кэшируются в памяти. При перезапуске сервера записи в кэше планов удаляются.

<a name="see-also"></a>См. также: 
--- 
[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md)    (Помощник по настройке ядра СУБД)  
[Руководство по помощнику по настройке ядра СУБД](Tutorial:%20Database%20Engine%20Tuning%20Advisor.md)     
[Сбор данных в хранилище запросов](../../relational-databases/performance/how-query-store-collects-data.md)     
[Query Store Best Practices](../../relational-databases/performance/best-practice-with-the-query-store.md) (Рекомендации по использованию хранилища запросов)
