---
title: "Рекомендации по индексам сolumnstore в помощнике по настройке ядра СУБД | Документация Майкрософт"
ms.custom: 
ms.date: 01/09/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Database Engine Tuning Advisor, columnstore index
- Database Engine Tuning Advisor, columnstore and rowstore indexes
ms.assetid: 9fba1139-82cb-4244-a41f-4337a7d0c132
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e465c19541d7577b19eef3b875697ba843cba000
ms.lasthandoff: 04/11/2017

---
# <a name="columnstore-index-recommendations-in-database-engine-tuning-advisor-dta"></a>Рекомендации по индексам сolumnstore в помощнике по настройке ядра СУБД
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

 
  [Индексы columnstore](../../t-sql/statements/create-columnstore-index-transact-sql.md), как и традиционные индексы rowstore, существенно повышают производительность хранения данных и аналитических рабочих нагрузок. Выбор подходящего индекса (rowstore или columnstore) для базы данных зависит от рабочей нагрузки приложения. В SQL Server 2016 [помощник по настройке ядра СУБД](../../relational-databases/performance/database-engine-tuning-advisor.md) может проанализировать рабочую нагрузку и порекомендовать создать индексы rowstore и columnstore в соответствующем сочетании для вашей базы данных. 
  
 Она доступна в среде SQL Server Management Studio версии **16.4** или более поздней. 
  
## <a name="how-to-enable-columnstore-index-recommendations-in-database-engine-tuning-advisor-gui"></a>Как включить рекомендации по индексам сolumnstore в помощнике по настройке ядра СУБД

  
  1. Запустите помощник по настройке ядра СУБД и откройте новый сеанс настройки.
  
  2. На вкладке **Общие** выберите базы данных и рабочую нагрузку для настройки.
  
  3. В области "Параметры настройки" установите флажок **Рекомендовать индексы columnstore** (см. рисунок ниже).
  ![Параметры настройки индексов columnstore помощника по настройке ядра СУБД](../../relational-databases/performance/media/dta-columnstore-indexes-tuning-option.gif)
 
  4. Выберите другие параметры настройки и нажмите кнопку **Начать анализ**.
  
  5. После завершения настройки просмотрите все рекомендации, включая все индексы columnstore, на вкладке **Рекомендации** (см. рисунок ниже).      
  ![Рекомендации индекса columnstore помощника по настройке ядра СУБД](../../relational-databases/performance/media/dta-columnstore-index-recommendation.gif)
  
  6. Щелкните гиперссылку **Определение** для просмотра инструкции языка определения данных DDL SQL, который может создать рекомендованный индекс. По умолчанию помощник по настройке ядра СУБД использует суффикс **col** в имени индекса columnstore, чтобы упростить определение индексов columnstore (см. рисунок ниже).
  ![Определение индекса columnstore в помощнике по настройке ядра СУБД](../../relational-databases/performance/media/dta-columnstore-index-definition.gif) 
  
  
  ## <a name="how-to-enable-columnstore-index-recommendations-in-dtaexe-utility"></a>Как включить рекомендации по индексам columnstore в служебной программе dta.exe

Используйте параметр командной строки **-fc**, чтобы включить рекомендации columnstore при использовании служебной программы командной строки dta.exe.

Сведения о служебной программе командной строки dta.exe см. в [этой статье](../../tools/dta/dta-utility.md).

## <a name="see-also"></a>См. также:
[Руководство по индексам columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md)       
[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md)     (Помощник по настройке ядра СУБД)  
[Руководство по помощнику по настройке ядра СУБД](Tutorial:%20Database%20Engine%20Tuning%20Advisor.md)



  


