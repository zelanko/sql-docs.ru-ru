---
title: Рекомендации по индексам сolumnstore — помощник по настройке ядра СУБД
description: Сведения о том, как помощник по настройке ядра СУБД может проанализировать рабочую нагрузку и порекомендовать создать индексы rowstore и columnstore для базы данных в SQL Server.
ms.custom: seo-dt-2019
ms.date: 01/09/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Database Engine Tuning Advisor, columnstore index
- Database Engine Tuning Advisor, columnstore and rowstore indexes
ms.assetid: 9fba1139-82cb-4244-a41f-4337a7d0c132
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 441b0c37a39efaf02ff00d64b893896cd3fe8f6f
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505378"
---
# <a name="columnstore-index-recommendations-in-database-engine-tuning-advisor-dta"></a>Рекомендации по индексам сolumnstore в помощнике по настройке ядра СУБД
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

 
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
[Руководство. Помощник по настройке ядра СУБД](../../tools/dta/tutorial-database-engine-tuning-advisor.md)



  

