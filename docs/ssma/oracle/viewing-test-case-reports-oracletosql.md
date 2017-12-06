---
title: "Просмотр отчетов тестовый случай (OracleToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8da14323-9dd6-4019-bf79-3e8b972a9bc0
caps.latest.revision: "6"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: c03500dde8c71a8cc817c4111eb0e7cc09995aca
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="viewing-test-case-reports-oracletosql"></a>Просмотр отчетов тестовый случай (OracleToSQL)
В отчете тестовый случай отображаются результаты проверки и тестирования Общие сведения. В случае сбоя теста также отображаются сведения об все несоответствующие данные в проверенный объектов.  
  
## <a name="report-structure"></a>Структура отчета  
Верхней части отчета показаны эти статистические данные:  
  
-   Общее число объектов протестированных и количество объектов, для которых проверка выполнена успешно.  
  
-   Общее число проверенных таблиц и внешних ключей и количество таблиц и внешние ключи, которые успешно совпадают.  
  
-   Время начала, время окончания тестового случая и общее время, затраченное на выполнение.  
  
Оставшаяся часть отчета показывает сведения в четырех категорий:  
  
**Необходимые условия ошибок**  
Показывает все ошибки, появившиеся в **шаг предварительные требования.** Как правило он пропускается.  
  
**Инициализация**  
Показывает состояние выполнения как **успех** или **сбоя**.  
  
**Объекты результатов теста**  
Сравнение результатов (успех или сбой) и несоответствий, которые SSMA тестировщик обнаружил в случае сбоя.  
  
**Завершение**  
Показывает состояние выполнения как **успех** или **сбоя**.  
  
## <a name="see-also"></a>См. также:  
[Выполнение тестовых случаев &#40; OracleToSQL &#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Тестирование миграции объектов базы данных &#40; OracleToSQL &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
